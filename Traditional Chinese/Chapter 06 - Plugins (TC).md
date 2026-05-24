# 第六章：Plugins全攻略——一鍵安裝海量擴充套件，還能自己造輪子

## 1. 前言

學完 Skills，你已經能給 Claude 裝上各種專屬能力包了。

但你有沒有想過一個問題——**辛辛苦苦寫好的 Commands + Skills + Hooks 配置，換個專案又得重來一遍？想分享給團隊成員？手動複製貼上？**

**Plugin 就是解決這個問題的終極方案：**

| 痛點               | Plugin 怎麼解決                    | 類比         |
| ------------------ | ---------------------------------- | ------------ |
| 配置不可移植       | 一個 Plugin 打包所有配置，一鍵安裝 | 手機備份恢復 |
| 分享靠手動複製     | Marketplace 搜一下裝一下           | App Store    |
| 更新全靠自己盯     | 自動更新，作者推了新版你自動獲得   | APP 自動更新 |
| 找好用的工具費時間 | 社群 200+ Plugin 直接選            | 排行榜推薦   |

說白了：**Plugin = 可分享、可安裝、可自動更新的 Commands + Skills + Hooks + MCP 打包體。**

------

## 2. Plugin 核心概念

### 2.1 Plugin 是什麼

Plugin 是 Claude Code 的**擴充套件包**——把 Commands、Skills、Hooks、MCP 配置打包成一個可安裝、可分享、可自動更新的整體。

**類比理解：**

| 手機                    | Claude Code        |
| ----------------------- | ------------------ |
| 作業系統（iOS/Android） | Claude Code 核心   |
| App Store               | Plugin Marketplace |
| 安裝的 APP              | 已安裝的 Plugins   |
| APP 自動更新            | Plugin 自動更新    |

**核心價值：**

| 價值     | 說明                                    |
| -------- | --------------------------------------- |
| 可複用   | 一次開發，多個專案使用                  |
| 可分享   | 透過 Marketplace 一鍵安裝，不用手動複製 |
| 模組化   | 每個 Plugin 專注一個領域，互不干擾      |
| 社群驅動 | 200+ 社群 Plugin 開箱即用               |

### 2.2 Plugin vs Commands / Skills / MCP

很多人問："我已經有 Commands 和 Skills 了，為什麼還要 Plugin？"

一張表說清楚：

| 維度     | Commands            | Skills            | MCP           | **Plugins**        |
| -------- | ------------------- | ----------------- | ------------- | ------------------ |
| 定義     | Markdown 提示詞     | 專業 Agent 能力   | 外部服務整合  | **打包的擴充套件**     |
| 存放位置 | `.claude/commands/` | `.claude/skills/` | `.mcp.json`   | `.claude/plugins/` |
| 可分享性 | ❌ 手動複製          | ❌ 手動複製        | ⚠️ 需配置      | ✅ 一鍵安裝         |
| 自動更新 | ❌ 手動更新          | ❌ 手動更新        | ⚠️ 部分支援    | ✅ 自動更新         |
| 包含內容 | 單個提示詞          | 多個檔案+配置     | 伺服器配置    | **全部都能包含**   |
| 適用場景 | 簡單重複任務        | 複雜專業任務      | 外部 API 呼叫 | **所有場景**       |

> **關鍵區別**：Plugin 是一個**"超集"**概念——`Plugin = Commands + Skills + Hooks + MCP 配置 + 文件`，打包成一個可以一鍵安裝和分享的整體。

**何時用什麼？決策指南：**

- **Commands**：專案內簡單重複任務（如 `/format-code`）——夠用就行，別上 Plugin
- **Skills**：專案內複雜專業任務（如程式碼註釋生成）——能力需要積累和複用
- **MCP**：需要呼叫外部服務（如 GitHub API、資料庫）——解決連線問題
- **Plugins**：✅ **想分享給團隊或社群的任何功能**——打包分發的最佳選擇

### 2.3 生態現狀

**三大 Marketplace：**

| 平臺                       | 地址                                                | 特點                  |
| -------------------------- | --------------------------------------------------- | --------------------- |
| Anthropic 官方 Marketplace | code.claude.com/plugins                             | 稽核嚴格，質量保證    |
| Jeremy Longshore 社群合集  | github.com/jeremylongshore/claude-code-plugins-plus | 200+ Plugin，持續更新 |
| Composio Integration       | composio.dev                                        | 整合 2000+ 外部工具   |

**熱門 Plugin 分類速查：**

| 分類     | 典型 Plugin        | 用途                       | 來源           | 熱度  |
| -------- | ------------------ | -------------------------- | -------------- | ----- |
| 文件處理 | document-skills    | PDF/PPTX/XLSX 全套文件處理 | Anthropic 官方 | ⭐⭐⭐⭐⭐ |
| 示例學習 | example-skills     | 官方 Skill 開發示例        | Anthropic 官方 | ⭐⭐⭐   |
| 程式碼質量 | code-review-expert | 自動程式碼審查               | 社群           | ⭐⭐⭐⭐  |
| 專案管理 | task-master-ai     | 任務拆解和跟蹤             | 社群           | ⭐⭐⭐⭐  |
| API 整合 | connect-apps       | Gmail/Slack/GitHub 聯動    | 社群           | ⭐⭐⭐⭐⭐ |
| 資料分析 | data-viz-pro       | 資料視覺化                 | 社群           | ⭐⭐⭐   |

> **說明**：`document-skills` 是 Anthropic 官方出品的文件處理套件（來自 `anthropics/skills` 源），安裝後包含 `document-skills:pdf`、`document-skills:pptx`、`document-skills:xlsx` 等多個 Skill，一次安裝全部可用。

------

## 3. 5 分鐘安裝第一個 Plugin

### 3.1 前置檢查

```bash
# 1. 確認 Claude Code 版本（需 v2.1+）
claude --version

# 2. 確認在專案目錄中
cd /path/to/your/project
```

> Plugin 功能於 2025 年 10 月 9 日隨 Claude Code v2.1 釋出。如果版本過低，先升級。

### 3.2 瀏覽 Marketplace

**方式一：對話內 `/plugin` 命令（最方便）**

在 Claude Code 對話中直接輸入：

```bash
/plugin
```

會進入 Plugin 管理介面，切換到 `Marketplace` 標籤頁即可瀏覽所有可用 Plugin。

**方式二：CLI 命令**

```bash
# 新增社群 Marketplace 源（第一次用需要先新增）
claude plugin marketplace add anthropics/skills

# 檢視已新增的 Marketplace 源
claude plugin marketplace list
```

新增成功後，就能從該源瀏覽和安裝 Plugin 了。

![image.png](../images/TCRVPlKTNAHEa3JN.webp)

![img](../images/ca0fDOBjTMEUt7pO.webp)

**實戰：新增 Marketplace 源並安裝 Plugin**

以新增 VoltAgent Subagent 代理庫為例，完整流程：

```bash
# 1. 新增 Marketplace 源
claude plugin marketplace add VoltAgent/awesome-claude-code-subagents
# 2. 從該源安裝你需要的 Plugin
claude plugin install <plugin-name>
```

或者在對話中輸入 `/plugin`，切換到 `Installed` 介面自行瀏覽安裝。

![img](../images/Mf04IaM5EfoHxHI0.webp)

![img](../images/uOS6EACM700JHJMs.webp)

![img](../images/NEGrXQ1K0EE2KE1a.webp)

> **網路問題？** 如果安裝過程中遇到超時或下載失敗，需要檢查代理軟體配置：
>
> ```powershell
> # Windows PowerShell（根據自己的代理埠修改）
> $env:HTTP_PROXY = "http://127.0.0.1:7897"
> $env:HTTPS_PROXY = "http://127.0.0.1:7897"
> # macOS / Linux
> export HTTP_PROXY="http://127.0.0.1:7897"
> export HTTPS_PROXY="http://127.0.0.1:7897"
> ```

**方式三：Web 瀏覽器**

直接訪問官方 Marketplace 網頁：`https://code.claude.com/plugins`

------

## 4. Plugin 管理全流程

在 Claude Code 對話中輸入 `/plugin`，進入圖形化管理介面。介面頂部有四個標籤頁，覆蓋所有管理場景：

| 標籤頁           | 功能                          |
| ---------------- | ----------------------------- |
| **Discover**     | 瀏覽並安裝 Plugin（預設開啟） |
| **Installed**    | 檢視和管理已安裝的 Plugin     |
| **Marketplaces** | 管理 Plugin 源                |
| **Errors**       | 排查載入錯誤                  |

> **介面導航**：`↑↓` 上下移動，`空格` 快速安裝/切換，`回車` 進入詳情，`ESC` 返回上級

### 4.1 安裝 Plugin（Discover 標籤頁）

開啟 `/plugin`，預設進入 **Discover** 標籤頁，列出所有已新增 Marketplace 源中的可用 Plugin：

![img](../images/galctWb54V7eOUuH.webp)

**安裝步驟：**

1. 用 `↑↓` 移動游標，選中想安裝的 Plugin
2. 按**回車**檢視詳情（或直接按**空格**快速安裝）
3. 在詳情頁選擇**安裝範圍**，確認安裝

![img](../images/UfAf3bnnI5SPnKHe.webp)

**安裝範圍說明：**

| 範圍                                                         | 說明                           | 適用場景               |
| ------------------------------------------------------------ | ------------------------------ | ---------------------- |
| Install for you (user scope)                                 | 個人級：你的所有專案都可用     | 日常通用工具（推薦）   |
| Install for all collaborators on this repository (project scope) | 專案級：整個倉庫的協作者共享   | 團隊協作專案           |
| Install for you, in this repo only (local scope)             | 本地倉庫級：僅自己在此專案可用 | 本地測試、不想影響他人 |

**三種安裝來源：**

| 來源                       | 操作方式                                     |
| -------------------------- | -------------------------------------------- |
| Marketplace Plugin（推薦） | 在 Discover 標籤頁直接選中安裝               |
| GitHub URL                 | 在 Discover 頁頂部輸入 GitHub 倉庫地址       |
| 本地目錄                   | 在 Discover 頁頂部輸入本地路徑（開發測試用） |

> **找不到想裝的 Plugin？** 先去 **Marketplaces** 標籤頁新增對應的源，再回 Discover 重新整理列表。

### 4.2 管理已安裝的 Plugin（Installed 標籤頁）

切換到 **Installed** 標籤頁，檢視所有已啟用的 Plugin：

![img](../images/jtEek0SPMBIfWbD4.webp)

列表中同時顯示 Plugin 系統安裝的擴充套件和 MCP 連線，每條顯示名稱、版本和狀態。

**更新 / 禁用 / 解除安裝操作：**

選中某個 Plugin，按**回車**進入詳情，可執行以下操作：

| 操作 | 效果                               |
| ---- | ---------------------------------- |
| 更新 | 升級到最新版本（有新版本時顯示）   |
| 禁用 | 臨時停用，保留檔案，下次可重新啟用 |
| 解除安裝 | 徹底刪除 Plugin 及其所有檔案       |

> **自動更新**：Claude Code 啟動時會自動檢查所有 Plugin 更新，無需手動觸發。

![img](../images/Bs1Hpui9ZB1ukGdd.webp)

### 4.3 管理 Marketplace 源（Marketplaces 標籤頁）

切換到 **Marketplaces** 標籤頁，管理 Plugin 的來源：

![img](../images/1QeAPWFyIulNOW5q.webp) 介面列出所有已新增的 Marketplace 源，每個源顯示可用 / 已安裝的 Plugin 數量，以及最後更新時間。

**新增新 Marketplace 源：**

1. 在 Marketplaces 標籤頁選擇"新增源"
2. 輸入源地址（格式：`使用者名稱/倉庫名`）
3. 確認新增後，Discover 標籤頁自動同步新來源的 Plugin

![img](../images/EHfHZVv68Oz2llWl.png)

**推薦 Marketplace 源：**

| 源地址                                     | 內容                                          | 推薦指數 |
| ------------------------------------------ | --------------------------------------------- | -------- |
| `anthropics/skills`                        | 官方 Skills 套件（含 document-skills 全家桶） | ⭐⭐⭐⭐⭐    |
| `anthropics/claude-plugins-official`       | Anthropic 官方 Plugin                         | ⭐⭐⭐⭐     |
| `VoltAgent/awesome-claude-code-subagents`  | 100+ 專家 Subagent（詳見第04章）              | ⭐⭐⭐⭐     |
| `jeremylongshore/claude-code-plugins-plus` | 社群 200+ Plugin，持續更新                    | ⭐⭐⭐      |

**Marketplace 源詳情示例**（`anthropics/skills`）：

```coq
anthropic-agent-skills (anthropics/skills)
3 available · 1 installed · Updated 2026/3/6

  ✅ document-skills (installed)
     Collection of document processing suite including Excel...
  ○  example-skills
     Collection of example skills demonstrating various capabi...
```

> **推薦先裝**：`document-skills`（官方文件處理套件），安裝後自動獲得 pdf、pptx、xlsx 等全套 Skill，一次搞定所有文件格式。

------

## 5. 建立自定義 Plugin

### 5.1 Plugin 結構規範

Plugin 本質上是一個目錄，裡面有個 `.claude-plugin/plugin.json` 清單檔案，加上你要打包的各種能力。

**最小結構（一個 Skill）：**

```nix
my-plugin/
├── .claude-plugin/
│   └── plugin.json      # 必需：Plugin 清單
└── skills/
    └── my-skill/
        └── SKILL.md
```

**完整結構（所有能力）：**

```nix
my-plugin/
├── .claude-plugin/
│   └── plugin.json      # 必需：Plugin 清單（只有這個在 .claude-plugin/ 內）
├── README.md            # 推薦：使用文件
├── LICENSE              # 推薦：開源協議
├── skills/              # 可選：Agent Skills
│   └── my-skill/
│       └── SKILL.md
├── commands/            # 可選：Slash Commands
│   └── my-command.md
├── agents/              # 可選：自定義 Agent 定義
├── hooks/               # 可選：事件鉤子
│   └── hooks.json
├── .mcp.json            # 可選：MCP 服務配置
└── settings.json        # 可選：Plugin 啟用時的預設設定
```

> ⚠️ **常見踩坑**：`commands/`、`skills/`、`agents/`、`hooks/` 都放在**外掛根目錄**，不要放進 `.claude-plugin/` 裡——那裡只放 `plugin.json`。

各目錄職責速查：

| 目錄/檔案                    | 職責                                 |
| ---------------------------- | ------------------------------------ |
| `.claude-plugin/plugin.json` | Plugin 清單，定義名稱/版本/作者      |
| `skills/`                    | Agent Skills（含 SKILL.md 的子目錄） |
| `commands/`                  | Slash 命令（Markdown 檔案）          |
| `agents/`                    | 自定義 Agent 定義                    |
| `hooks/`                     | 事件處理器（hooks.json）             |
| `.mcp.json`                  | MCP 服務配置                         |
| `settings.json`              | Plugin 啟用時應用的預設設定          |

### 5.2 plugin.json 詳解

`plugin.json` 放在 `.claude-plugin/` 目錄下，是 Plugin 的「身份證」。

**完整示例：**

```json
{
  "name": "my-awesome-plugin",
  "description": "一句話說明這個 Plugin 做什麼",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  },
  "license": "MIT",
  "homepage": "https://github.com/yourname/my-plugin",
  "repository": "https://github.com/yourname/my-plugin"
}
```

**欄位速查：**

| 欄位          | 是否必填 | 說明                                         |
| ------------- | -------- | -------------------------------------------- |
| `name`        | ✅        | Plugin 唯一標識，同時是 Skill 的名稱空間字首 |
| `description` | ✅        | 功能描述，Marketplace 中用於搜尋和展示       |
| `version`     | ✅        | 語義化版本號（`主.次.補丁`，如 `1.0.0`）     |
| `author`      | 推薦     | 作者資訊（`name` / `email` / `url`）         |
| `license`     | 推薦     | 開源協議（推薦 `MIT` 或 `Apache-2.0`）       |
| `homepage`    | 可選     | 專案主頁或文件地址                           |
| `repository`  | 可選     | 程式碼倉庫地址                                 |

> **關鍵點**：`name` 欄位決定了 Skill 的呼叫字首。Plugin 名叫 `my-plugin`，裡面的 `hello` Skill 就要用 `/my-plugin:hello` 來觸發——名稱空間設計防止多個 Plugin 的 Skill 名稱衝突。

### 5.3 實戰：Hello World Plugin

5 分鐘從零建立並測試你的第一個 Plugin：

**Step 1：建立目錄結構**

```bash
mkdir -p hello-plugin/.claude-plugin
mkdir -p hello-plugin/skills/hello
```

**Step 2：建立清單 `.claude-plugin/plugin.json`**

```json
{
  "name": "hello-plugin",
  "description": "一個簡單的問候示例 Plugin",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  },
  "license": "MIT"
}
```

**Step 3：建立 Skill `skills/hello/SKILL.md`**

```markdown
---
description: Greet the user with a friendly message
---

用友好的方式向使用者打招呼。

步驟：
1. 獲取當前系統時間
2. 根據時間段（上午/下午/晚上）調整問候語
3. 用輕鬆愉快的語氣回覆

示例輸出：
"早上好！現在是 10:23，新的一天，有什麼我能幫你的？"
```

**Step 4：本地測試**

不需要安裝，直接用 `--plugin-dir` 標誌載入：

```bash
# 載入外掛並啟動 Claude Code
claude --plugin-dir ./hello-plugin

# 啟動後在對話裡輸入（注意名稱空間格式）
> /hello-plugin:hello
```

看到問候輸出，第一個 Plugin 就跑通了！

> `--plugin-dir` 是開發專用標誌，每次修改 Skill 後重啟 Claude Code 即可生效，無需安裝。要同時測試多個 Plugin，可以多次指定：`claude --plugin-dir ./plugin-a --plugin-dir ./plugin-b`

**Step 5：帶引數的 Skill**

`$ARGUMENTS` 佔位符可以捕獲使用者輸入的文字，讓 Skill 動態響應：

```markdown
---
description: Greet the user with a personalized message
---

用友好的方式向名叫 "$ARGUMENTS" 的使用者打招呼，讓問候更有溫度。
```

重啟後測試：

```bash
> /hello-plugin:hello 小明
# Claude 會用你傳入的名字問候
```

### 5.4 進階：帶 Skill 的完整 Plugin

建立一個程式碼質量檢查 Plugin，演示 Skill + Commands 的組合威力：

**專案結構：**

```nix
code-quality-checker/
├── .claude-plugin/
│   └── plugin.json
├── README.md
├── skills/
│   └── code-review/
│       └── SKILL.md
└── commands/
    └── check.md
```

**`.claude-plugin/plugin.json`：**

```json
{
  "name": "code-quality-checker",
  "description": "自動檢查程式碼質量，按嚴重程度給出改進建議",
  "version": "1.0.0",
  "author": { "name": "Your Name" },
  "license": "MIT"
}
```

**`skills/code-review/SKILL.md`：**

```markdown
---
description: Reviews code for best practices, security issues, and quality problems. Use when reviewing code, checking PRs, or analyzing code quality.
---

# 程式碼質量檢查專家

## 角色定義
你是一位資深程式碼審查專家，擅長髮現程式碼質量問題並給出具體改進建議。

## 檢查維度
1. **命名規範**：變數名/函式名是否語義清晰
2. **函式複雜度**：單個函式是否過長或巢狀過深
3. **重複程式碼**：是否存在可抽取的重複邏輯
4. **錯誤處理**：異常邊界是否覆蓋
5. **安全隱患**：是否存在注入/XSS 等風險

## 輸出格式
按嚴重程度排序：
- 🔴 嚴重：必須修復
- 🟡 警告：建議修復
- 🟢 建議：可以改進

每條包含：問題描述 + 程式碼位置 + 修復建議
```

**`commands/check.md`：**

```markdown
對指定程式碼進行質量檢查。

引數：$ARGUMENTS（可選，指定檢查的檔案路徑）

步驟：
1. 如果指定了檔案路徑，只檢查該檔案
2. 如果未指定，檢查最近修改的檔案（透過 git diff --name-only 獲取）
3. 按 5 個維度逐項分析，輸出分級報告
```

**測試：**

```bash
claude --plugin-dir ./code-quality-checker

# 觸發 Skill（自動識別）
> 幫我檢查這段程式碼的質量

# 顯式呼叫命令（注意名稱空間）
> /code-quality-checker:check src/app.ts
```

> Plugin 的「超集」威力在這裡體現得很清楚：**Commands 提供觸發入口，Skills 提供專業能力**，打包在一起就是可分享的完整工具。

### 5.5 開發最佳實踐

**1. 先用獨立配置，再轉 Plugin**

| 階段     | 方式                     | 原因                                             |
| -------- | ------------------------ | ------------------------------------------------ |
| 實驗期   | 直接放 `.claude/skills/` | Skill 名短（`/hello`），迭代快                   |
| 準備共享 | 打包成 Plugin            | Skill 帶名稱空間（`/my-plugin:hello`），便於分發 |

**2. 語義化版本號**

```gml
版本號格式：主.次.補丁（如 1.2.3）
  - 主版本（1.x.x）：破壞性變更，不向後相容
  - 次版本（x.2.x）：新增功能，向後相容
  - 補丁版（x.x.3）：Bug 修復
```

**3. README 必須包含四個部分**

| 部分     | 內容                                      |
| -------- | ----------------------------------------- |
| 功能說明 | 這個 Plugin 做什麼，解決什麼問題          |
| 安裝方法 | 從 Marketplace 或 GitHub 安裝的命令       |
| 使用示例 | 至少一個真實使用場景（含 Skill 呼叫格式） |
| 配置說明 | 如果有可配置項的話                        |

**4. Skill description 是關鍵**

`SKILL.md` frontmatter 中的 `description` 決定 Claude 能否自動識別場景並啟用 Skill：

```markdown
# ❌ 太模糊，自動啟用不準
description: Code review tool

# ✅ 明確觸發場景，自動識別準確
description: Reviews code for best practices and potential issues. Use when reviewing code, checking PRs, or analyzing code quality.
```

------

## 6. 釋出與分享

### 6.1 釋出前檢查清單

**必須完成：**

- ✅ `.claude-plugin/plugin.json` 格式正確，`name`/`description`/`version` 填寫完整
- ✅ `README.md` 包含安裝和使用說明（含 Skill 呼叫格式 `/外掛名:skill名`）
- ✅ `LICENSE` 檔案存在（推薦 MIT）
- ✅ 用 `claude --plugin-dir .` 本地測試透過，所有 Skill 和命令正常工作

**推薦完成：**

- ⭐ `CHANGELOG.md` 記錄每個版本的變更內容
- ⭐ GitHub 倉庫新增 Topics 標籤（如 `claude-code-plugin`），便於被搜尋
- ⭐ README 中註明最低 Claude Code 版本要求

### 6.2 釋出到 GitHub

```bash
# 1. 初始化倉庫
cd my-plugin
git init
git add .
git commit -m "feat: initial release v1.0.0"

# 2. 推送到 GitHub
git remote add origin https://github.com/yourname/my-plugin.git
git branch -M main
git push -u origin main
```

**建立 Release（讓別人能按版本安裝）：**

1. 進入 GitHub 倉庫頁面，點選 **Releases → Draft a new release**
2. Tag version 填 `v1.0.0`（必須以 `v` 開頭）
3. 填寫本次釋出說明
4. 點選 **Publish release**

釋出後，其他人就能透過 GitHub URL 直接安裝：

```bash
# 在 /plugin 介面的 Discover 頁頂部輸入 GitHub 地址安裝
# 或用 CLI
claude plugin install https://github.com/yourname/my-plugin
```

> 在 README 中加個版本徽章，一眼看出當前版本：
>
> ```markdown
> [Version](https://img.shields.io/github/v/release/yourname/my-plugin)
> ```

### 6.3 提交到官方 Marketplace

想讓全球 Claude Code 使用者都能搜到你的 Plugin？直接用**應用內提交表單**，不需要 Fork 倉庫、提 PR，一個表單搞定：

| 平臺              | 提交入口                             |
| ----------------- | ------------------------------------ |
| Claude.ai         | `claude.ai/settings/plugins/submit`  |
| Anthropic Console | `platform.claude.com/plugins/submit` |

**提交前確認：**

| 稽核項                       | 要求                                  |
| ---------------------------- | ------------------------------------- |
| `.claude-plugin/plugin.json` | 格式正確，必填欄位完整                |
| README                       | 安裝和使用說明完整，含 Skill 呼叫格式 |
| 程式碼安全                     | 無惡意程式碼，依賴來源可信              |
| 功能完整                     | `--plugin-dir` 測試全部透過           |

提交後等待 Anthropic 稽核（通常 1-3 個工作日）。稽核透過後，你的 Plugin 就會出現在官方 Marketplace，全球 Claude Code 使用者都能一鍵安裝。

------

## 7. 故障排查

### 7.1 安裝問題

| 現象                 | 原因                                | 解決方法                                           |
| -------------------- | ----------------------------------- | -------------------------------------------------- |
| `Plugin not found`   | 名稱拼寫錯誤或 Marketplace 源未新增 | 先在 Marketplaces 標籤頁新增源，再到 Discover 搜尋 |
| 下載超時             | 網路問題                            | 設定代理或切換 npm 映象源                          |
| `/plugin` 命令不存在 | Claude Code 版本過低                | 升級到 v1.0.33+（執行 `claude --version` 確認）    |

```bash
# 網路問題？換用其他 npm 映象源
npm config set registry https://registry.npmmirror.com

# 需要代理？（根據自己的代理埠修改）
export HTTP_PROXY="http://127.0.0.1:7897"
export HTTPS_PROXY="http://127.0.0.1:7897"
```

### 7.2 執行時問題

| 現象               | 原因                               | 解決方法                                          |
| ------------------ | ---------------------------------- | ------------------------------------------------- |
| Skill 呼叫格式不對 | 忘記名稱空間字首                   | Plugin 內的 Skill 用 `/外掛名:skill名` 格式       |
| Skill 未自動啟用   | SKILL.md 的 description 描述太模糊 | 明確寫出觸發場景，如 "Use when reviewing code..." |
| Hook 指令碼許可權錯誤  | 指令碼缺少執行許可權                   | `chmod +x hooks/my-hook.sh`                       |
| 配置修改不生效     | 未重啟 Claude Code                 | 修改 Plugin 內容後需重啟                          |

### 7.3 開發除錯

| 現象                    | 原因             | 解決方法                                                |
| ----------------------- | ---------------- | ------------------------------------------------------- |
| `--plugin-dir` 載入失敗 | 目錄結構不正確   | 確認 `.claude-plugin/plugin.json` 存在於外掛根目錄      |
| Plugin 中 Skill 找不到  | skills/ 放錯位置 | `skills/` 必須在外掛根目錄，不能在 `.claude-plugin/` 內 |
| plugin.json 解析報錯    | JSON 格式錯誤    | 用線上 JSON 驗證工具檢查，確認冒號後有空格、無多餘逗號  |

```bash
# 啟用詳細日誌排查問題
export CLAUDE_LOG_LEVEL=debug
claude --plugin-dir ./my-plugin
```

------

## 8. 常見問題 FAQ

**Q1：Plugin 和 Skill 到底啥區別？**

一句話：**Skill 是能力本身，Plugin 是把能力打包成可安裝、可分享的形式。** Plugin 可以包含 Skill，也可以包含 Commands、Hooks、MCP 配置等。

**Q2：Plugin 更新會覆蓋我的配置嗎？**

不會。更新時保留你的 `config.json`（個人配置），只更新 Plugin 程式碼檔案（skills/、commands/ 等）。

**Q3：Plugin 開發需要懂程式設計嗎？**

| 型別                    | 需要程式設計？ | 說明                    |
| ----------------------- | ---------- | ----------------------- |
| 只有 Commands 的 Plugin | ❌ 不需要   | 寫 Markdown 就行        |
| 包含 Skills 的 Plugin   | ❌ 不需要   | 寫 Markdown（SKILL.md） |
| 帶指令碼的 Plugin         | ✅ 需要     | Python/JavaScript 基礎  |
| 帶 MCP Server 的 Plugin | ✅ 需要     | Node.js/Python 開發經驗 |

**Q4：Plugin 可以離線使用嗎？**

安裝在本地的 Plugin 可以離線使用。但如果 Plugin 內部呼叫了外部 API（如 GitHub API），那部分功能需要聯網。

**Q5：Plugin 支援哪些程式語言？**

| 語言                  | 支援度 | 適用場景                       |
| --------------------- | ------ | ------------------------------ |
| JavaScript/TypeScript | ⭐⭐⭐⭐⭐  | MCP 整合、CLI 工具             |
| Python                | ⭐⭐⭐⭐⭐  | 資料處理、AI 整合              |
| Shell Script          | ⭐⭐⭐⭐   | 系統操作、自動化               |
| Go / Rust             | ⭐⭐     | 高效能工具，需編譯為可執行檔案 |

**Q6：如何檢視 Plugin 使用了多少 Token？**

可以透過 `/cost` 命令檢視整體 Token 消耗。Plugin 本身不單獨計費，Token 消耗取決於 Plugin 載入的提示詞量和對話內容。

**Q7：可以同時安裝多個版本的 Plugin 嗎？**

不可以。同一個 Plugin 只能安裝一個版本。如果需要在不同專案使用不同版本，可以用專案級安裝（預設）隔離。

**Q8：Plugin 報錯如何獲取幫助？**

1. 檢視 Plugin 的 README 和 GitHub Issues
2. 在 Anthropic Discord 的 `#claude-code-plugins` 頻道提問
3. 提 GitHub Issue 時包含：系統環境、Claude Code 版本、Plugin 版本、完整錯誤資訊

------

## 9. 總結

本章你已掌握：

1. **Plugin 本質**：可分享的 Commands + Skills + Hooks + MCP 打包體，一鍵安裝、自動更新
2. **核心區別**：Plugin 是"超集"概念，解決了 Commands/Skills 無法便捷分享的痛點
3. **生態現狀**：官方 Marketplace + 社群 200+ Plugin，按需選擇
4. **安裝管理**：`/plugin` 介面的 Discover / Installed / Marketplaces 三大標籤頁，全程圖形化操作
5. **自定義開發**：`.claude-plugin/plugin.json` 清單 + `skills/` + `commands/` 標準結構，`--plugin-dir` 秒測試
6. **釋出分享**：GitHub Release 釋出 + 官方 Marketplace 表單提交，讓全世界用上你的 Plugin
