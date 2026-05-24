# 第一章：從零到起飛，10分鐘讓AI為你寫程式碼

## 1. 前言

Claude Code 是 Anthropic 推出的革命性 AI 程式設計助手，它不是簡單的程式碼補全工具，而是一個能夠理解你的需求、主動思考、執行操作的"程式設計夥伴"。

與傳統 AI 工具不同，**Claude Code 直接在終端執行**，可以讀寫檔案、執行命令、分析程式碼，真正做到"說人話，幹實事"。

本文將透過實際場景，帶你快速掌握 Claude Code 的核心用法。

**適用人群**：前端/後端開發者、技術寫作者、程式碼審查者、任何想提升程式設計效率的人

## 2. 快速上手：第一次使用Claude Code

### 2.1 環境準備（必須先完成）

在安裝 Claude Code 之前，你需要確保系統滿足以下條件：

#### 2.1.1 安裝 Git（必需）

下載地址：[git-scm.com](https://git-scm.com/downloads)，按預設步驟安裝。

**關鍵配置**：設定環境變數 `CLAUDE_CODE_GIT_BASH_PATH`

```Bash
D:\Program Files\Git\bin\bash.exe
```

（根據你的 Git 安裝路徑調整）

**驗證安裝**：

```Bash
git --version
```

#### 2.1.2 安裝 Node.js（必需）

下載地址：[nodejs.org](https://nodejs.org/)，安裝 Node.js 18 及以上版本。推薦24.14.0

**驗證安裝**：

```Bash
node -v
npm -v
```

![image.png](../images/sbF8uf1Y6aaRQ5tG.webp)

![img](../images/3g5gKTh737r3gxFS.png)

#### 2.1.3 獲取 API 金鑰

Claude Code 需要 官方賬號登入 或者 API 金鑰才能執行，你有兩種選擇。

API Key 是一串以 `sk-ant-` 開頭的金鑰字串，格式類似：

```gradle
sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**方式一：官方渠道**

1. 訪問 [Anthropic Console](https://console.anthropic.com/settings/keys)
2. 註冊賬戶（三種方式任選）：
   - Google 賬號登入（推薦，最快）
   - 郵箱 + 密碼註冊
   - GitHub 賬號登入
3. 在 **API Keys** 頁面建立新金鑰
4. 複製並妥善儲存（只顯示一次！）

### 2.2 安裝 Claude Code

#### 2.2.1 方案一：官方推薦安裝（推薦）

**第一步：安裝 Claude Code 參考官方：[Quickstart - Claude Code Docs](https://code.claude.com/docs/en/quickstart#native-install-recommended)**

選擇適合你的系統的安裝指令碼：

| 系統               | 安裝命令                                                     |
| ------------------ | ------------------------------------------------------------ |
| macOS、Linux、WSL  | `curl -fsSL https://claude.ai/install.sh | bash`             |
| Windows PowerShell | `irm https://claude.ai/install.ps1 | iex`                    |
| Windows CMD        | `curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd` |

官方安裝會自動更新，保持最新版本。

**第二步：登入賬戶**

啟動 Claude Code 並登入：

```Bash
claude
# 首次使用會提示登入
/login
# 按照提示完成賬戶登入
```

**支援的賬戶型別：**

- ✅ Claude Pro、Max、Teams、Enterprise（推薦）
- ✅ Claude Console（API 訪問，需要預付費額度）
- ✅ Amazon Bedrock、Google Vertex AI、Microsoft Foundry（企業雲服務）

登入後憑證會自動儲存，無需重複登入。需要切換賬戶時使用 `/login` 命令。

#### 2.2.2 方案二：IDE 擴充套件安裝（VS Code / Cursor / IDEA）

除了終端命令啟動，你也可以在編輯器內透過擴充套件/外掛使用 Claude Code，獲得視覺化介面和深度整合體驗。

**VS Code（官方擴充套件）**

1. 按 `Ctrl/Cmd + Shift + X` 開啟擴充套件市場
2. 搜尋 `Claude Code`，找到 Anthropic 官方釋出的擴充套件，點選 Install
3. 安裝後左側活動欄出現 ⚡ 火花圖示，點選即可開啟 Claude Code 面板

擴充套件相比終端 CLI 的額外能力：

| 功能            | 說明                            |
| --------------- | ------------------------------- |
| 側邊欄面板      | 程式碼和對話分離，互不干擾        |
| 內聯差異顯示    | 修改內容實時高亮                |
| Checkpoint 回滾 | 按 Esc 兩次可回退到上一個檢查點 |
| @提及           | 智慧引用檔案和函式              |

> 參考文件：https://code.claude.com/docs/en/vs-code

**Cursor（VSIX 手動安裝）**

Cursor 基於 VS Code，但 Claude Code 擴充套件無法自動檢測 Cursor，需要手動安裝：

1. 從 VS Code Marketplace 下載 Claude Code 擴充套件的 VSIX 檔案

2. 在 Cursor 中安裝：

   ```Bash
   cursor --install-extension /path/to/claude-code.vsix
   ```

   或直接將 VSIX 檔案拖拽到 Cursor 的擴充套件面板

3. 重啟 Cursor，左側出現 Claude Code 圖示即成功

> 詳細教程：https://www.cursor-ide.com/blog/claude-code-cursor-extension-guide

**IntelliJ IDEA（Claude Code GUI 外掛）**

[Claude Code GUI](https://plugins.jetbrains.com/plugin/26200-claude-code-gui) 是一款 JetBrains 市場 4.8 高評分的視覺化介面外掛，將 Claude Code 和 OpenAI Codex 雙重 AI 工具直接整合到 IntelliJ IDEA 中。

1. 按 `Ctrl/Cmd + ,` 開啟設定 → Plugins → Marketplace
2. 搜尋 `Claude Code GUI`，點選 Install
3. 重啟 IDEA，工具視窗中出現 Claude Code 面板即成功

![img](../images/D3SHh5VkdJkq1bGA.png)

### 2.3 首次啟動與配置

```Bash
# 進入你的專案目錄
cd ~/my-project

# 啟動 Claude Code
claude
```


| 環境               | 設定臨時環境變數的命令 | 生效範圍             |
| ------------------ | ---------------------- | -------------------- |
| Linux/macOS 終端   | `export 變數名=值`     | 當前終端會話         |
| Windows CMD        | `set "變數名=值"`      | 當前 CMD 視窗        |
| Windows PowerShell | `$env:變數名="值"`     | 當前 PowerShell 會話 |

```text
export ANTHROPIC_BASE_URL=http:xxx.xx
export ANTHROPIC_AUTH_TOKEN=API_Key
```

#### 2.3.1 啟動引數速查

除了直接輸入 `claude` 啟動，還可以透過引數控制啟動行為：

| 引數                                    | 作用                     | 適用場景                 |
| --------------------------------------- | ------------------------ | ------------------------ |
| `claude`                                | 預設啟動（會詢問許可權）   | 日常使用                 |
| `claude --dangerously-skip-permissions` | 跳過許可權詢問，直接執行   | 信任的個人專案，快速開發 |
| `claude -p "你的問題"`                  | 直接提問模式，回答後退出 | 快速查詢，不需要對話     |
| `claude --headless`                     | 無介面模式               | 指令碼自動化               |

**關於 `--dangerously-skip-permissions`**

這個引數會讓 Claude Code 跳過所有許可權確認，直接執行讀寫檔案、執行命令等操作。Anthropic 官方稱之為 **"Safe YOLO mode"**。

名字裡帶 "dangerously" 是因為 AI 可能誤修改程式碼、刪除檔案或執行非預期命令，跳過確認意味著你來不及阻止。

| 場景                                | 是否推薦 |
| ----------------------------------- | -------- |
| 自己的學習/個人專案，程式碼已提交 Git | ✅ 可以用 |
| 只讀操作（查詢、分析）              | ✅ 可以用 |
| 公司專案、開源專案                  | ❌ 不要用 |
| 第一次使用 Claude Code              | ❌ 不要用 |
| 包含敏感資料的專案                  | ❌ 不要用 |

> **新手建議**：前 1 個月不要加這個引數。讓 AI 每次操作都問你，既能學到它在做什麼，又能避免誤操作。等你熟悉了 Claude Code 的行為模式後，在個人專案中再考慮使用，但務必先把程式碼提交到 Git，確保隨時可回滾。

#### API 金鑰配置關鍵資訊

在配置 API 時，最重要的兩個引數是：

- **API Key**（認證憑證）
- **請求地址**（API 端點）

![img](../images/AAPgUx4S4uqYj6So.png)


#### 2.3.2 配置檔案結構

Claude Code 的配置分為**全域性**和**專案**兩級，理解這個結構對後續章節（CLAUDE.md、Commands、Hooks 等）很重要：

```pgsql
~/.claude/                      ← 全域性配置目錄（所有專案共享）
├── config.json                 ← 全域性配置檔案
├── auth-token.json             ← 認證令牌
├── trusted-directories.json    ← 信任的目錄列表
├── cache/                      ← 快取目錄
└── logs/                       ← 日誌目錄

專案目錄/.claude/              ← 專案級配置（僅當前專案生效）
├── config.json                 ← 專案配置（覆蓋全域性同名配置）
├── commands/                   ← 自定義命令（第03章詳解）
├── skills/                     ← 自定義技能（第06章詳解）
└── hooks/                      ← 自定義鉤子（第05章詳解）
```

## 3. 核心命令速查表

### 3.1 高頻命令（建議收藏）

| 命令     | 功能           | 使用場景                        |
| -------- | -------------- | ------------------------------- |
| /init    | 初始化專案文件 | 第一次使用時，讓AI理解專案結構  |
| /clear   | 清空對話歷史   | 切換任務時釋放上下文，節省token |
| /compact | 壓縮對話歷史   | 會話過長時保留摘要，繼續對話    |
| /add-dir | 新增工作目錄   | 需要同時操作多個專案時          |
| /export  | 匯出對話記錄   | 儲存重要的對話內容              |
| /model   | 切換AI模型     | 切換到 Opus 或其他模型          |
| /memory  | 編輯記憶檔案   | 自定義AI的長期記憶              |
| /resume  | 恢復上次對話   | 繼續之前的工作                  |

### 3.2 快捷操作

| 操作     | 快捷鍵/語法                       | 說明             |
| -------- | --------------------------------- | ---------------- |
| 引用檔案 | @檔名                           | 讓AI關注特定檔案 |
| 貼上圖片 | Ctrl + V / ALt + V 看具體終端不同 | 傳送截圖讓AI分析 |
| 換行輸入 | Shift + Alt+ Enter                | 多行輸入         |
| 執行Bash | !ls -l                            | 直接執行系統命令 |
| 歷史命令 | ↑ / ↓                             | 快速切換歷史輸入 |
| 中斷執行 | Esc                               | 停止AI當前操作   |

## 4. 總結

Claude Code 的核心優勢在於：

1. **自然語言互動**：不需要記複雜的命令，說人話就行
2. **主動執行能力**：不只是建議，而是直接幫你改程式碼、建立檔案
3. **上下文理解**：理解專案結構，給出符合專案規範的程式碼
4. **多模態支援**：可以處理圖片、分析截圖

**記住這句話：Claude Code 最大的優勢是理解自然語言，所以直接說出你的需求，做好指揮官，讓它為你工作！**

