# 第三章：告別重複提示詞，自定義Commands讓AI秒懂你

## 1. 前言

學完前兩章，你已經能熟練啟動 Claude Code、使用各種 Slash 命令和快捷鍵。

但你可能發現一個痛點：**每次讓 Claude 做同型別的事，都要重複一大段要求**。

Commands（自定義命令）就是解決這個問題的——**把重複的提示詞壓縮成一個詞，一次配置，永久生效。**

------

## 2. Commands 是什麼

### 2.1 什麼是 Slash 命令

Slash 命令是 Claude Code 的"快捷方式"：輸入 `/命令名` 觸發預設操作。

**工作原理**：輸入 `/write AI教程` → 找到 `.claude/commands/write.md` → 讀取內容作為提示詞 → 把 `AI教程` 賦值給 `$ARGUMENTS` → 執行。

核心等式：**命令名 = 檔名（不含 `.md`）**，**引數 = `$ARGUMENTS`**。

### 2.2 命令的三大型別

| 型別         | 存放位置              | 生效範圍                        |
| ------------ | --------------------- | ------------------------------- |
| 內建命令     | 程式內部（不可改）    | 所有專案                        |
| 專案級自定義 | `.claude/commands/`   | 僅當前專案，可提交 Git 團隊共享 |
| 使用者級自定義 | `~/.claude/commands/` | 所有專案，個人通用工具          |

選擇原則：會話管理/診斷用內建；專案專屬工作流用專案級；跨專案通用工具用使用者級。

### 2.3 為什麼要學 Commands

| 對比維度 | 手動輸入     | 使用 Commands      |
| -------- | ------------ | ------------------ |
| 效率     | 每次重複輸入 | 一次配置，永久使用 |
| 一致性   | 容易遺漏要求 | 標準化執行         |
| 可複用   | 困在聊天記錄 | 團隊共享、版本控制 |

------

## 3. 建立第一個自定義命令

**Step 1：建目錄**

```Bash
# macOS / Linux
mkdir -p .claude/commands

# Windows PowerShell
New-Item -ItemType Directory -Path ".claude\commands" -Force
```

**Step 2：建立命令檔案** `.claude/commands/hello.md`

```markdown
# 問候命令

使用者想要問候的物件是：$ARGUMENTS

如果沒有提供名字，請使用"朋友"作為預設稱呼。
請用熱情友好的方式問候，並詢問今天可以幫助什麼。
```

> 推薦新手直接在 Claude Code 對話方塊說："幫我建立檔案 `.claude/commands/hello.md`，內容是……"，讓 AI 幫你寫檔案。

**Step 3：測試**

```nix
claude
You: /hello 張三   → 你好，張三！……
You: /hello        → 你好，朋友！……
```

> **小技巧**：輸入 `/` 後按 `Tab` 鍵可檢視所有可用命令。

------

## 4. 自定義命令開發進階

### 4.1 命令檔案結構

命令檔案由兩部分組成：**YAML frontmatter 配置區**（機器讀）+ **Markdown 正文**（AI 讀）。

```markdown
---
description: 電子報文章創作命令
argument-hint: <主題關鍵詞>
allowed-tools:
  - Read
  - Write
  - WebSearch
model: claude-sonnet-4-5-20250929
---

# 電子報文章創作

你是一位資深的電子報寫作專家。
主題：$ARGUMENTS

寫作要求：接地氣 · 1500-2000字 · 金句開頭 → 核心內容 → 行動號召
```

### 4.2 作用域與優先順序

**優先順序**：專案級 > 使用者級 > 內建命令（非核心）

> `/clear`、`/help`、`/compact` 等核心內建命令受保護，自定義命令無法覆蓋。

支援子目錄，用 `:` 作名稱空間：

```verilog
.claude/commands/
├── write.md              # /write
├── dev/
│   └── code-review.md    # /dev:code-review
└── test/
    └── generate.md       # /test:generate
```

### 4.3 frontmatter 配置詳解

| 配置項                     | 作用                                   |
| -------------------------- | -------------------------------------- |
| `description`              | 命令描述，顯示在 `/help` 和 Tab 補全中 |
| `argument-hint`            | 輸入命令後顯示的引數佔位符提示         |
| `allowed-tools`            | 限制可呼叫的工具（安全邊界）           |
| `model`                    | 強制指定模型，覆蓋當前會話模型         |
| `disable-model-invocation` | 設為 `true` 時只做文字替換，不呼叫 AI  |

**`disable-model-invocation` 示例**（節省 Token 的純模板命令）：

```markdown
---
description: 快速插入版權宣告
disable-model-invocation: true
---

© 2025 $ARGUMENTS. All rights reserved.
```

執行 `/copyright 你的名字` → 直接輸出 `© 2025 . All rights reserved.`，不經過 AI 處理。

### 4.4 $ARGUMENTS 引數處理

`$ARGUMENTS` 接收命令後的全部輸入（整段字串）：

```bash
/write AI工具            → $ARGUMENTS = "AI工具"
/write AI工具 技術 3000  → $ARGUMENTS = "AI工具 技術 3000"
/write                   → $ARGUMENTS = ""（空）
```

多引數解析和空值校驗直接用自然語言在提示詞中描述即可：

```markdown
$ARGUMENTS 格式：<主題> [風格] [字數]
- 第一個詞：主題（必需，若為空請提示使用者補充）
- 第二個詞：風格（可選，預設"接地氣"）
- 第三個詞：字數（可選，預設 1500）
```

### 4.5 可呼叫的工具

| 工具名      | 功能             | 常用場景              |
| ----------- | ---------------- | --------------------- |
| `Read`      | 讀取檔案         | 分析程式碼、讀取配置    |
| `Write`     | 寫入新檔案       | 建立檔案、儲存結果    |
| `Edit`      | 編輯已有檔案     | 修改程式碼              |
| `Bash`      | 執行命令         | 執行測試、Git 操作    |
| `WebSearch` | 網路搜尋         | 獲取最新資訊          |
| `WebFetch`  | 抓取網頁內容     | 下載指定頁面分析      |
| `Glob`      | 按檔名匹配查詢 | 批次找 `*.md`、`*.ts` |
| `Grep`      | 按內容搜尋檔案   | 找含 TODO 的程式碼      |
| `Task`      | 啟動子代理       | 並行執行復雜任務      |
| `TodoWrite` | 任務管理         | 建立和更新待辦清單    |

> **最小許可權原則**：審查類只需 `Read, Grep`；寫程式碼加 `Write, Edit`；跑命令才開 `Bash`。
>
> MCP 工具命名格式：`mcp__伺服器名__工具名`（如 `mcp__github__create_issue`），詳見第04章。

### 4.6 條件邏輯設計

Markdown 不支援程式碼邏輯，但 Claude 能理解自然語言描述的條件分支：

```markdown
根據 $ARGUMENTS 判斷：
- 包含"深度"或"詳細" → 深度分析，輸出 3000 字以上完整報告
- 包含"快速"或"簡要" → 快速分析，輸出 500 字以內摘要
- 其他情況（預設）    → 標準分析，輸出 1500 字標準報告
檢查 $ARGUMENTS 的第一個關鍵詞：
- "測評" → 測評模板，重點寫優缺點對比
- "教程" → 教程模板，重點寫步驟和程式碼
- "對比" → 對比模板，重點寫表格和結論
- 其他   → 通用模板
```

### 4.7 實戰：完整寫作命令

檔案：`.claude/commands/write.md`

```markdown
---
description: 電子報文章全自動創作，從資訊收集到成稿儲存
argument-hint: <主題關鍵詞>
allowed-tools:
  - Read
  - Write
  - WebSearch
  - Grep
---

# 電子報文章創作系統

你是資深電子報寫作專家，擅長創作接地氣、有深度的技術科普文章。

**主題**：$ARGUMENTS

## 執行步驟

1. **資訊收集**：WebSearch 搜尋"$ARGUMENTS 最新資訊 2025"，收集核心概念、最新動態、使用者痛點
2. **構思大綱**：金句開頭 → 問題引入(2-3段) → 核心內容(5-8段) → 總結號召
3. **撰寫文章**：說人話、用類比、多短句，字數 1500-2000，每段≤150字
4. **儲存文章**：Write 儲存到 `articles/drafts/[日期]_[主題].md`
5. **生成標題**：5個備選標題（含數字、引發好奇、≤30字）

## 輸出格式

# [選定標題]

[文章正文]

---
## 備選標題
1. [標題1] ... 5. [標題5]
```

使用：`/write Claude Code入門` → 自動完成搜尋、構思、撰寫、儲存全流程。

------

## 5. 命令高階用法

> 名稱空間（子目錄組織）見 4.2 作用域與優先順序。

### 5.1 命令組合與鏈式呼叫

單個命令可以描述多步驟工作流，Claude 會按順序執行：

```markdown
# 完整發布流程

1. WebSearch 搜尋 "$ARGUMENTS 最新動態"
2. 根據搜尋結果撰寫文章並 Write 儲存
3. Read 讀取文章，進行自我審查並輸出修改意見
4. 輸出最終版本與 5 個備選標題
```

多命令串聯：先 `/research 主題` 生成素材檔案，再 `/write 主題` 讀取該檔案寫作，每個命令職責單一、可單獨複用。

### 5.2 模組化設計

把多個命令共用的角色設定、寫作風格提取為**共享片段**，存入 `.claude/modules/`：

```nix
.claude/
├── commands/
│   ├── write.md        # 引用 modules/writer-role.md
│   └── review.md       # 引用 modules/writer-role.md
└── modules/
    └── writer-role.md  # 共享角色設定，修改一次全部生效
```

在命令檔案中載入模組（需在 `allowed-tools` 開啟 `Read`）：

```markdown
請先讀取 `.claude/modules/writer-role.md` 作為角色設定，再執行以下任務……
```

### 5.3 社群命令資源

| 資源                 | 搜尋關鍵詞         | 內容                       |
| -------------------- | ------------------ | -------------------------- |
| Claude Command Suite | GitHub 搜尋        | 審查、測試、文件類命令集合 |
| Awesome Claude Code  | GitHub 搜尋        | 社群精選命令、模板、工作流 |
| 官方文件示例         | docs.anthropic.com | 官方推薦命令寫法           |

> 使用社群命令前，先審查 `allowed-tools` 列表，避免許可權過寬。

### 5.4 故障排查

| 現象                   | 原因          | 解決方法                                    |
| ---------------------- | ------------- | ------------------------------------------- |
| 輸入命令無響應         | 檔案路徑錯誤  | 確認路徑：`.claude/commands/命令名.md`      |
| 名稱空間命令找不到     | 目錄層級錯誤  | `/dev:review` 對應 `commands/dev/review.md` |
| frontmatter 配置未生效 | YAML 格式有誤 | 檢查縮排用空格、冒號後有空格                |
| 工具呼叫被拒絕         | 工具未宣告    | 將所需工具加入 `allowed-tools` 列表         |
| 引數被截斷             | 特殊字元問題  | 用引號包裹：`/write "AI 教程 2025"`         |

------

## 6. 內建命令速查

> 詳細用法見[第二章 6. Slash 命令大全](https://xn--02:30+,-ix3k85d6ye67rjn7ajwjpsam0rhr0e8fmzqnlzdmvbu38bdqedy8m.md/#6-slash-命令大全)，這裡提供速查表。

| 分類       | 命令                            | 功能                       | 重要度 |
| ---------- | ------------------------------- | -------------------------- | ------ |
| 會話管理   | `/clear` `/compact` `/resume`   | 清空/壓縮/恢復會話         | ⭐⭐⭐    |
|            | `/export` `/rename`             | 匯出/重新命名會話            | ⭐⭐     |
| 上下文控制 | `/context` `/model`             | 檢視Token / 切換模型       | ⭐⭐⭐    |
|            | `/cost` `/usage`                | 檢視費用/用量              | ⭐⭐     |
| 專案配置   | `/init` `/add-dir`              | 初始化CLAUDE.md / 新增目錄 | ⭐⭐⭐    |
|            | `/memory` `/permissions`        | 編輯記憶 / 管理許可權        | ⭐⭐     |
| 開發輔助   | `/rewind` `/review` `/todos`    | 回退/審查/待辦             | ⭐⭐⭐    |
|            | `/agents`                       | 管理子代理                 | ⭐⭐     |
| 診斷工具   | `/doctor` `/status`             | 健康檢查/完整狀態          | ⭐⭐     |
| MCP 相關   | `/mcp` `/hooks`                 | 管理MCP/Hooks              | ⭐⭐⭐    |
| 其他       | `/help` `/bug` `/release-notes` | 幫助/報告Bug/更新日誌      | ⭐⭐     |

------

## 7. 總結

本章你已掌握：

1. **Commands 本質**：`.claude/commands/` 下的 Markdown 檔案，檔名即命令名，`$ARGUMENTS` 接收引數
2. **三種型別**：內建 / 專案級 / 使用者級，按需選擇
3. **frontmatter**：5 個配置項控制描述、引數提示、工具許可權、模型、是否呼叫 AI
4. **最小許可權原則**：按角色只開放必要工具
5. **條件邏輯**：自然語言描述分支，Claude 正確執行
6. **高階用法**：鏈式呼叫多步驟工作流、模組化共享片段、社群命令資源借力
