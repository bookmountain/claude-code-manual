# 第 7b 章：企業協作 — GitLab CI 配套篇

> **本檔案定位。** 對應 **第 7 章 §3（CI/CD 整合）** 的 GitLab-CI 版本。第 7 章中的團隊規範（§2）、安全與權限（§4）、效能與成本（§5）、故障排查（§6）內容均不變，僅 CI 工具鏈不同。請先讀第 7 章，需要 GitLab YAML 時再回來看本檔案。

GitLab 上常見的做法是用 `claude` Docker image 內呼叫 Claude Code CLI（或直接呼叫 Anthropic API），而不是用廠商發佈的 GitHub Action。下面的範例採用這個模式。

---

## 1. 前置作業：GitLab 變數

在你的專案中加入金鑰：

1. **Settings → CI/CD → Variables → Add variable**
2. Key：`ANTHROPIC_API_KEY`，Value：你的 API Key
3. 勾選 **Masked** 和 **Protected**（只在受保護的分支/標籤注入）

如果是自架 / Bedrock / Vertex：依需求另外設定 `ANTHROPIC_BASE_URL`、`AWS_*`、`GOOGLE_*` 變數。

---

## 2. 最簡 `.gitlab-ci.yml` — 每個 MR 自動 Claude 審查

這是第 7 章 §3.1 最簡配置的 GitLab 對應版本 — 每個 Merge Request 都會自動觸發 Claude 審查，結果以 MR note 形式回貼。

```yaml
# .gitlab-ci.yml

stages:
  - review

variables:
  CLAUDE_MODEL: "claude-sonnet-4-6-20250929"

claude-review:
  stage: review
  image: node:20-alpine
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
  variables:
    GIT_DEPTH: 0   # 完整歷史，才能 diff 目標分支
  before_script:
    - apk add --no-cache git curl jq
    - npm install -g @anthropic-ai/claude-code
  script:
    # 1. 計算 source 分支與 target 分支之間的 diff
    - git fetch origin "$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"
    - DIFF=$(git diff "origin/$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"...HEAD)
    # 2. 請 Claude 進行審查
    - |
      REVIEW=$(echo "$DIFF" | claude --print \
        --model "$CLAUDE_MODEL" \
        --max-tokens 4096 \
        "Review the following diff. Output three sections: \
         'Must fix (blocking)', 'Suggested', 'Strengths'. \
         Each finding: brief description + file path + line range + suggested fix.")
    # 3. 將審查結果回貼為 MR note
    - |
      curl --silent --show-error --fail \
        --request POST \
        --header "PRIVATE-TOKEN: $CLAUDE_BOT_TOKEN" \
        --data-urlencode "body=## 🤖 Claude Review\n\n${REVIEW}" \
        "$CI_API_V4_URL/projects/$CI_PROJECT_ID/merge_requests/$CI_MERGE_REQUEST_IID/notes"
```

**需要兩個專案存取權杖：**

| 權杖                 | 用途                                | 範圍                          |
| -------------------- | ----------------------------------- | ----------------------------- |
| `ANTHROPIC_API_KEY`  | 呼叫 Claude                         | （不需要 GitLab 範圍）        |
| `CLAUDE_BOT_TOKEN`   | 將審查結果回貼到 MR                 | `api`（Project Access Token） |

在 **Settings → Access Tokens → Add new token** 建立 `CLAUDE_BOT_TOKEN`，角色 *Developer*（或 *Reporter* + Note 權限），範圍 `api`。

---

## 3. 多任務工作流

三個並行任務 — 程式碼審查、安全掃描、互動式 `@claude` 處理 — 對應第 7 章 §3.2。GitHub 與 GitLab 的事件觸發對照：

| GitHub 觸發器                              | GitLab 觸發器                                        |
| ------------------------------------------ | ---------------------------------------------------- |
| `pull_request: opened/synchronize/reopened` | `$CI_PIPELINE_SOURCE == "merge_request_event"`       |
| `issue_comment` 含 `@claude`               | MR/Issue note webhook → pipeline trigger（見 §3.3） |

```yaml
# .gitlab-ci.yml

stages:
  - review
  - security
  - interactive

variables:
  CLAUDE_MODEL: "claude-sonnet-4-6-20250929"

.claude-base:
  image: node:20-alpine
  before_script:
    - apk add --no-cache git curl jq
    - npm install -g @anthropic-ai/claude-code

# ===== 程式碼審查 =====
review:
  extends: .claude-base
  stage: review
  variables:
    GIT_DEPTH: 0
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
  script:
    - git fetch origin "$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"
    - DIFF=$(git diff "origin/$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"...HEAD)
    - |
      REVIEW=$(echo "$DIFF" | claude --print \
        --model "$CLAUDE_MODEL" \
        --max-tokens 4096 \
        "Please review the code changes in this MR with a focus on: \
         1. Code quality and maintainability \
         2. Potential bugs and security issues \
         3. Performance considerations \
         4. Test coverage suggestions \
         Output three sections: 'Must fix', 'Suggested', 'Strengths'.")
    - |
      curl --silent --fail --request POST \
        --header "PRIVATE-TOKEN: $CLAUDE_BOT_TOKEN" \
        --data-urlencode "body=## 🤖 Claude Code Review\n\n${REVIEW}" \
        "$CI_API_V4_URL/projects/$CI_PROJECT_ID/merge_requests/$CI_MERGE_REQUEST_IID/notes"

# ===== 安全掃描 =====
security-scan:
  extends: .claude-base
  stage: security
  variables:
    GIT_DEPTH: 0
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
  script:
    - git fetch origin "$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"
    - DIFF=$(git diff "origin/$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"...HEAD)
    - |
      SCAN=$(echo "$DIFF" | claude --print \
        --model "$CLAUDE_MODEL" \
        --max-tokens 2048 \
        "Run a security scan on this diff. Check for: \
         1. Hard-coded sensitive data (API keys, passwords, tokens...) \
         2. SQL injection / XSS / command injection risks \
         3. Insecure dependency versions \
         4. Permission misconfiguration \
         Tag high-severity findings with [SECURITY-CRITICAL] at the start.")
    - |
      curl --silent --fail --request POST \
        --header "PRIVATE-TOKEN: $CLAUDE_BOT_TOKEN" \
        --data-urlencode "body=## 🔐 Claude Security Scan\n\n${SCAN}" \
        "$CI_API_V4_URL/projects/$CI_PROJECT_ID/merge_requests/$CI_MERGE_REQUEST_IID/notes"

# ===== 互動式指令（由 webhook 觸發，見 §3.3）=====
interactive:
  extends: .claude-base
  stage: interactive
  rules:
    - if: '$CI_PIPELINE_SOURCE == "trigger" && $CLAUDE_TRIGGER == "comment"'
  script:
    - |
      REPLY=$(claude --print \
        --model "$CLAUDE_MODEL" \
        --max-tokens 4096 \
        "$COMMENT_BODY")
    - |
      curl --silent --fail --request POST \
        --header "PRIVATE-TOKEN: $CLAUDE_BOT_TOKEN" \
        --data-urlencode "body=## 🤖 Claude Reply\n\n${REPLY}" \
        "$CI_API_V4_URL/projects/$CI_PROJECT_ID/${RESOURCE_KIND}/${RESOURCE_IID}/notes"
```

### 3.3 串接 `@claude` 留言

GitHub 每個留言都會觸發 workflow；GitLab 不會。兩種常見作法：

**作法 A — Pipeline trigger token + 小型 webhook 接收器**（最有彈性）

1. **Settings → CI/CD → Pipeline triggers → Add trigger** → 把 token 存成 `CLAUDE_TRIGGER_TOKEN`。
2. 架一個小型 webhook 接收器（Cloud Function / Lambda / 一個小型 Node 服務）監聽 GitLab 的 *Note Hook* 事件，當 body 含 `@claude` 時呼叫：

   ```bash
   curl --request POST \
     --form "token=$CLAUDE_TRIGGER_TOKEN" \
     --form "ref=main" \
     --form "variables[CLAUDE_TRIGGER]=comment" \
     --form "variables[COMMENT_BODY]=$NOTE_BODY" \
     --form "variables[RESOURCE_KIND]=merge_requests" \
     --form "variables[RESOURCE_IID]=$MR_IID" \
     "$GITLAB_HOST/api/v4/projects/$PROJECT_ID/trigger/pipeline"
   ```

3. **Settings → Webhooks → Add webhook** → 觸發類型 `Comments`，URL 指向你的接收器。

**作法 B — 排程輪詢**（不需額外服務）

每日／每小時的 pipeline 輪詢 GitLab API，找出新的 `@claude` MR/Issue 留言並批次處理。架設更簡單，但延遲較高。

---

## 4. 完整流水線範例（lint → test → review → build → deploy）

第 7 章 §3.3 六階段流水線的 GitLab 對應版本：

```yaml
# .gitlab-ci.yml

stages:
  - lint
  - test
  - review
  - build
  - deploy

variables:
  NODE_VERSION: "20"
  CLAUDE_MODEL: "claude-sonnet-4-6-20250929"

default:
  image: node:20-alpine

lint:
  stage: lint
  script:
    - npm ci
    - npm run lint
    - npm run format:check

test:
  stage: test
  needs: [lint]
  script:
    - npm ci
    - npm test -- --coverage
  artifacts:
    when: always
    reports:
      coverage_report:
        coverage_format: cobertura
        path: coverage/cobertura-coverage.xml

claude-review:
  stage: review
  needs: [test]
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
  variables:
    GIT_DEPTH: 0
  before_script:
    - apk add --no-cache git curl jq
    - npm install -g @anthropic-ai/claude-code
  script:
    - git fetch origin "$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"
    - DIFF=$(git diff "origin/$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"...HEAD)
    - |
      REVIEW=$(echo "$DIFF" | claude --print \
        --model "$CLAUDE_MODEL" --max-tokens 4096 \
        "Review the MR. Output quality assessment, security check, and improvement suggestions.")
    - |
      curl --silent --fail --request POST \
        --header "PRIVATE-TOKEN: $CLAUDE_BOT_TOKEN" \
        --data-urlencode "body=## 🤖 Claude Review\n\n${REVIEW}" \
        "$CI_API_V4_URL/projects/$CI_PROJECT_ID/merge_requests/$CI_MERGE_REQUEST_IID/notes"

build:
  stage: build
  needs: [test]
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 week

deploy-staging:
  stage: deploy
  needs: [build]
  rules:
    - if: '$CI_COMMIT_BRANCH == "develop"'
  environment:
    name: staging
    url: https://staging.example.com
  script:
    - echo "Deploying to Staging..."

deploy-production:
  stage: deploy
  needs: [build]
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
  environment:
    name: production
    url: https://app.example.com
  script:
    - echo "Deploying to Production..."
```

> **注意：** `claude-review` 只在 MR 事件觸發（呼應第 7 章「不要為了 push 到 main/develop 浪費 token」的建議）。

---

## 5. GitHub → GitLab 速查對照

移植其他 Claude-in-CI 模式時，這張表能掃掉大多數常見坑：

| 概念                  | GitHub Actions                              | GitLab CI                                                       |
| --------------------- | ------------------------------------------- | --------------------------------------------------------------- |
| 金鑰存放              | Repo *Settings → Secrets and variables*     | Project *Settings → CI/CD → Variables*（Masked + Protected）    |
| 觸發：PR/MR 建立/更新 | `on: pull_request` types                    | `rules: - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'`   |
| 觸發：留言            | `on: issue_comment`（原生支援）             | Webhook → pipeline trigger token（§3.3）                        |
| 完整歷史 checkout     | `actions/checkout@v4` 配 `fetch-depth: 0`   | `variables: GIT_DEPTH: 0`                                       |
| 可重用 workflow       | `uses: anthropics/claude-code-action@v1`    | `extends: .claude-base` + `npm install -g @anthropic-ai/claude-code` |
| 回貼留言              | Action 自動完成                             | `curl` 打 `/projects/:id/merge_requests/:iid/notes`             |
| 環境守門              | `environment: production`                   | `environment: { name: production }`                             |
| Artifact 傳遞         | `actions/upload-artifact` / `download-artifact` | `artifacts: paths: [...]`（自動傳給依賴任務）                |
| 分支條件              | `if: github.ref == 'refs/heads/main'`       | `rules: - if: '$CI_COMMIT_BRANCH == "main"'`                    |

---

## 6. 故障排查（GitLab 特有）

| 症狀                                      | 可能原因                                            | 解決方法                                                                  |
| ----------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------- |
| Job 找不到 `claude` 指令                  | `before_script` 漏掉 npm install                   | 確認 `npm install -g @anthropic-ai/claude-code` 有執行                    |
| Git diff 是空的                           | Shallow clone（預設 GIT_DEPTH=20）                  | 設定 `variables: GIT_DEPTH: 0`                                            |
| `403 Forbidden` 回貼 MR note 失敗         | `CLAUDE_BOT_TOKEN` 缺 `api` 範圍或已過期            | 重新建立 token，加 `api` 範圍；bot 至少需 *Reporter* 角色                 |
| `@claude` 留言沒觸發 pipeline             | Webhook 未設或 trigger token 錯誤                   | 檢查 Note hook 設定與 pipeline trigger token                              |
| Job 看不到 `ANTHROPIC_API_KEY`            | 變數標為 **Protected** 但分支不是                   | 取消變數的 Protected，或把分支設為 protected                              |
| Masked 變數仍出現在 log 中                | 變數值含 GitLab 無法 mask 的字元                    | 重產 API key，確保只含 `[a-zA-Z0-9_+/=@:.-]`                              |

---

## 7. 與第 7 章相同的部分

第 7 章中以下章節在轉用 GitLab 時 **不變** — 它們屬於 Claude Code 本身，與 CI 平台無關：

- §2 團隊協作規範（目錄結構、三層 CLAUDE.md、新人入職）
- §4 安全與合規（allow/deny、allowedTools、稽核日誌）
- §5 效能與成本最佳化
- §6 故障排查（團隊／安全／成本）

完全照第 7 章執行，只把 GitHub Actions YAML 換成本檔案中的 GitLab YAML 即可。
