# Chapter 7b: Enterprise Collaboration — GitLab CI Companion

> **What this file is.** A direct GitLab-CI counterpart to **Chapter 7 §3 (CI/CD Integration)**. Everything in Chapter 7 about team standards (§2), security/permissions (§4), performance and cost (§5), and troubleshooting (§6) applies unchanged — only the pipeline tooling differs. Read Chapter 7 first; come here when you need the GitLab YAML.

The community's typical pattern on GitLab is to invoke Claude through the Claude Code CLI (or the Anthropic API directly) inside a `claude` Docker image, instead of using a vendor-published GitHub Action. The recipes below take that approach.

---

## 1. Prep: GitLab Variables

Add the secret in your project:

1. **Settings → CI/CD → Variables → Add variable**
2. Key: `ANTHROPIC_API_KEY`, Value: your API key
3. Check **Masked** and **Protected** (so it only injects into protected branches/tags)

If self-hosted/Anthropic-on-Bedrock/Vertex: also set `ANTHROPIC_BASE_URL`, `AWS_*`, or `GOOGLE_*` variables as appropriate.

---

## 2. Minimal `.gitlab-ci.yml` — Claude Reviews Every MR

This is the GitLab equivalent of Chapter 7 §3.1's minimal config — every Merge Request gets an automatic Claude review posted as an MR note.

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
    GIT_DEPTH: 0   # Full history so we can diff against the target branch
  before_script:
    - apk add --no-cache git curl jq
    - npm install -g @anthropic-ai/claude-code
  script:
    # 1. Compute the diff between source and target branches
    - git fetch origin "$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"
    - DIFF=$(git diff "origin/$CI_MERGE_REQUEST_TARGET_BRANCH_NAME"...HEAD)
    # 2. Ask Claude to review
    - |
      REVIEW=$(echo "$DIFF" | claude --print \
        --model "$CLAUDE_MODEL" \
        --max-tokens 4096 \
        "Review the following diff. Output three sections: \
         'Must fix (blocking)', 'Suggested', 'Strengths'. \
         Each finding: brief description + file path + line range + suggested fix.")
    # 3. Post the review back as an MR note
    - |
      curl --silent --show-error --fail \
        --request POST \
        --header "PRIVATE-TOKEN: $CLAUDE_BOT_TOKEN" \
        --data-urlencode "body=## 🤖 Claude Review\n\n${REVIEW}" \
        "$CI_API_V4_URL/projects/$CI_PROJECT_ID/merge_requests/$CI_MERGE_REQUEST_IID/notes"
```

**Two project access tokens are required:**

| Token                | Purpose                                | Scope                       |
| -------------------- | -------------------------------------- | --------------------------- |
| `ANTHROPIC_API_KEY`  | Call Claude                            | (no GitLab scope needed)    |
| `CLAUDE_BOT_TOKEN`   | Post the review note back to the MR    | `api` (Project Access Token) |

Create `CLAUDE_BOT_TOKEN` under **Settings → Access Tokens → Add new token** with role *Developer* (or *Reporter*+Note permissions) and scope `api`.

---

## 3. Multi-job Workflow

Three parallel jobs — code review, security scan, and an interactive `@claude` handler — mirroring Chapter 7 §3.2. GitLab equivalents of GitHub event triggers:

| GitHub trigger                             | GitLab trigger                                       |
| ------------------------------------------ | ---------------------------------------------------- |
| `pull_request: opened/synchronize/reopened` | `$CI_PIPELINE_SOURCE == "merge_request_event"`       |
| `issue_comment` with `@claude`             | MR/Issue note webhook → pipeline trigger (see §3.3)  |

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

# ===== Code Review =====
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

# ===== Security Scan =====
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

# ===== Interactive Commands (triggered by webhook, see §3.3) =====
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

### 3.3 Wiring up `@claude` comments

GitHub fires a workflow on every comment; GitLab does not. Two common patterns:

**Option A — Pipeline trigger token + tiny webhook receiver** (most flexible)

1. **Settings → CI/CD → Pipeline triggers → Add trigger** → save the token as `CLAUDE_TRIGGER_TOKEN`.
2. Stand up a small webhook receiver (Cloud Function / Lambda / a tiny Node service) that listens for GitLab's *Note Hook* events and, when the body contains `@claude`, calls:

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

3. **Settings → Webhooks → Add webhook** → trigger `Comments`, URL pointing at your receiver.

**Option B — Scheduled poller** (no extra service)

A daily/hourly pipeline polls the GitLab API for new MR/Issue notes mentioning `@claude` and processes them in batch. Simpler to host, higher latency.

---

## 4. Full Pipeline Example (lint → test → review → build → deploy)

The GitLab equivalent of Chapter 7 §3.3's six-stage pipeline:

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

> **Note:** `claude-review` only runs on MR events (mirroring the Chapter 7 advice not to spend tokens on every push to main/develop).

---

## 5. GitHub → GitLab Quick Reference

When porting other Claude-in-CI patterns, this table covers the usual gotchas:

| Concept                       | GitHub Actions                              | GitLab CI                                                       |
| ----------------------------- | ------------------------------------------- | --------------------------------------------------------------- |
| Secret storage                | Repo *Settings → Secrets and variables*     | Project *Settings → CI/CD → Variables* (Masked + Protected)     |
| Trigger: PR/MR opened/updated | `on: pull_request` types                    | `rules: - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'`   |
| Trigger: comment              | `on: issue_comment` (native)                | Webhook → pipeline trigger token (§3.3)                          |
| Checkout full history         | `actions/checkout@v4` with `fetch-depth: 0` | `variables: GIT_DEPTH: 0`                                       |
| Reusable workflow             | `uses: anthropics/claude-code-action@v1`    | `extends: .claude-base` + `npm install -g @anthropic-ai/claude-code` |
| Post comment back             | Action does it implicitly                   | `curl` to `/projects/:id/merge_requests/:iid/notes`             |
| Per-environment guard         | `environment: production`                   | `environment: { name: production }`                             |
| Artifact passing              | `actions/upload-artifact` / `download-artifact` | `artifacts: paths: [...]` (auto-passed to dependent jobs)  |
| Conditional on branch         | `if: github.ref == 'refs/heads/main'`       | `rules: - if: '$CI_COMMIT_BRANCH == "main"'`                    |

---

## 6. Troubleshooting (GitLab-specific)

| Symptom                                       | Likely cause                                          | Fix                                                                       |
| --------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------- |
| `claude` command not found in job             | npm install missed in `before_script`                 | Confirm `npm install -g @anthropic-ai/claude-code` ran                    |
| Git diff is empty                             | Shallow clone (default GIT_DEPTH=20)                  | Set `variables: GIT_DEPTH: 0`                                             |
| `403 Forbidden` posting note back to MR       | `CLAUDE_BOT_TOKEN` lacks `api` scope or expired       | Recreate token with `api` scope; bot needs at least *Reporter* role       |
| Pipeline doesn't trigger on `@claude` comment | Webhook missing or trigger token wrong                | Check Note hook setup and pipeline trigger token                          |
| `ANTHROPIC_API_KEY` not visible to job        | Variable marked **Protected** but branch isn't        | Either unprotect the variable, or mark the branch as protected            |
| Masked variable shows in logs                 | Value contains characters GitLab can't mask           | Regenerate API key, ensure it's only `[a-zA-Z0-9_+/=@:.-]`                |

---

## 7. What stays the same as Chapter 7

These sections in Chapter 7 do **not** change when you move to GitLab — they're about Claude Code itself, not the CI platform:

- §2 Team Collaboration Standards (directory layout, three-tier CLAUDE.md, onboarding)
- §4 Security and Compliance (allow/deny, allowedTools, audit logs)
- §5 Performance and Cost Optimization
- §6 Troubleshooting (team / security / cost)

Apply those exactly as Chapter 7 describes; replace only the GitHub Actions YAML with the GitLab YAML in this file.
