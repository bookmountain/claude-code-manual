# Claude Code实战指南

# 第一章：从零到起飞，10分钟让AI为你写代码

## 1. 前言

Claude Code 是 Anthropic 推出的革命性 AI 编程助手，它不是简单的代码补全工具，而是一个能够理解你的需求、主动思考、执行操作的"编程伙伴"。

与传统 AI 工具不同，**Claude Code 直接在终端运行**，可以读写文件、执行命令、分析代码，真正做到"说人话，干实事"。

本文将通过实际场景，带你快速掌握 Claude Code 的核心用法。

**适用人群**：前端/后端开发者、技术写作者、代码审查者、任何想提升编程效率的人

## 2. 快速上手：第一次使用Claude Code

### 2.1 环境准备（必须先完成）

在安装 Claude Code 之前，你需要确保系统满足以下条件：

#### 2.1.1 安装 Git（必需）

下载地址：[git-scm.com](https://git-scm.com/downloads)，按默认步骤安装。

**关键配置**：设置环境变量 `CLAUDE_CODE_GIT_BASH_PATH`

```Bash
D:\Program Files\Git\bin\bash.exe
```

（根据你的 Git 安装路径调整）

**验证安装**：

```Bash
git --version
```

#### 2.1.2 安装 Node.js（必需）

下载地址：[nodejs.org](https://nodejs.org/)，安装 Node.js 18 及以上版本。推荐24.14.0

**验证安装**：

```Bash
node -v
npm -v
```

![image.png](https://pic.code-nav.cn/post_picture/1738833787455823874/sbF8uf1Y6aaRQ5tG.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/3g5gKTh737r3gxFS.png)

#### 2.1.3 获取 API 密钥

Claude Code 需要 官方账号登录 或者 API 密钥才能运行，你有两种选择。

API Key 是一串以 `sk-ant-` 开头的密钥字符串，格式类似：

```gradle
sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**方式一：官方渠道**

1. 访问 [Anthropic Console](https://console.anthropic.com/settings/keys)
2. 注册账户（三种方式任选）：
   - Google 账号登录（推荐，最快）
   - 邮箱 + 密码注册
   - GitHub 账号登录
3. 在 **API Keys** 页面创建新密钥
4. 复制并妥善保存（只显示一次！）

> **手机验证提示**：注册时可能需要手机验证，支持中国大陆号码（+86），成功率约 80%。如果多次收不到验证码，可尝试语音验证或使用 Google Voice 等虚拟号码。

**方式二：国内中转站（推荐国内用户）**

💡 官方 API 需要海外信用卡且价格较高，国内用户可以选择以下中转站，**价格更优惠、支付更方便**（仅个人使用）：

也可以通过监控平台 [RelayPulse - 实时监测API中转服务可用性矩阵](https://relaypulse.top/?service=cc) 选择使用中转站，用多少充多少~

| 平台              | 注册链接                                  |
| ----------------- | ----------------------------------------- |
| AnyRouter（公益） | https://anyrouter.top/register?aff=xzkV   |
| gemai 哈基米      | https://api.gemai.cc/register?aff=Odrb    |
| Linkapi           | https://linkapi.ai/register?aff=1rM2      |
| Ikun              | https://api.ikuncode.cc/register?aff=l978 |
| ClaudeCN          | https://claudecn.top/register?aff=p0mt    |
| DuckCoding        | https://duckcoding.com/register?aff=HMtz  |

🎁 **福利提示**：通过上方链接注册，你我都能获得额外额度！

### 2.2 安装 Claude Code

#### 2.2.1 方案一：官方推荐安装（推荐）

**第一步：安装 Claude Code 参考官方：[Quickstart - Claude Code Docs](https://code.claude.com/docs/en/quickstart#native-install-recommended)**

选择适合你的系统的安装脚本：

| 系统               | 安装命令                                                     |
| ------------------ | ------------------------------------------------------------ |
| macOS、Linux、WSL  | `curl -fsSL https://claude.ai/install.sh | bash`             |
| Windows PowerShell | `irm https://claude.ai/install.ps1 | iex`                    |
| Windows CMD        | `curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd` |

官方安装会自动更新，保持最新版本。

**第二步：登录账户**

启动 Claude Code 并登录：

```Bash
claude
# 首次使用会提示登录
/login
# 按照提示完成账户登录
```

**支持的账户类型：**

- ✅ Claude Pro、Max、Teams、Enterprise（推荐）
- ✅ Claude Console（API 访问，需要预付费额度）
- ✅ Amazon Bedrock、Google Vertex AI、Microsoft Foundry（企业云服务）

登录后凭证会自动保存，无需重复登录。需要切换账户时使用 `/login` 命令。

#### 2.2.2 方案二：一键智能安装 ZCF（推荐新手）

**什么是 ZCF？** Zero-Config Code Flow，一个为 Claude Code 设计的零配置工具。它会自动为你：

- 📦 安装 Claude Code
- 🔧 配置 API 和认证
- 📋 导入主流工作流模板
- 🔌 安装 主流MCP 服务
- 🌍 支持中文界面

**一键启动：**

```Bash
npx zcf
```

按照交互菜单提示，选择语言 → 选择"完整初始化" → 自动配置完成！

**参考图片：**

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/Jl4eUEl8N20B4biD.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/VHRaU4aXDfobF8gf.webp)

**教程参考资源：**

- [ZCF 官方文档](https://zcf.ufomiao.com/zh-CN/getting-started/installation)
- [ZCF 博客园教程](https://www.cnblogs.com/gyc567/p/19207551)
- [ZCF 知乎专栏](https://zhuanlan.zhihu.com/p/1971966528405631388)

#### 2.2.3 方案三：IDE 扩展安装（VS Code / Cursor / IDEA）

除了终端命令启动，你也可以在编辑器内通过扩展/插件使用 Claude Code，获得可视化界面和深度集成体验。

**VS Code（官方扩展）**

1. 按 `Ctrl/Cmd + Shift + X` 打开扩展市场
2. 搜索 `Claude Code`，找到 Anthropic 官方发布的扩展，点击 Install
3. 安装后左侧活动栏出现 ⚡ 火花图标，点击即可打开 Claude Code 面板

扩展相比终端 CLI 的额外能力：

| 功能            | 说明                            |
| --------------- | ------------------------------- |
| 侧边栏面板      | 代码和对话分离，互不干扰        |
| 内联差异显示    | 修改内容实时高亮                |
| Checkpoint 回滚 | 按 Esc 两次可回退到上一个检查点 |
| @提及           | 智能引用文件和函数              |

> 参考文档：https://code.claude.com/docs/en/vs-code

**Cursor（VSIX 手动安装）**

Cursor 基于 VS Code，但 Claude Code 扩展无法自动检测 Cursor，需要手动安装：

1. 从 VS Code Marketplace 下载 Claude Code 扩展的 VSIX 文件

2. 在 Cursor 中安装：

   ```Bash
   cursor --install-extension /path/to/claude-code.vsix
   ```

   或直接将 VSIX 文件拖拽到 Cursor 的扩展面板

3. 重启 Cursor，左侧出现 Claude Code 图标即成功

> 详细教程：https://www.cursor-ide.com/blog/claude-code-cursor-extension-guide

**IntelliJ IDEA（Claude Code GUI 插件）**

[Claude Code GUI](https://plugins.jetbrains.com/plugin/26200-claude-code-gui) 是一款 JetBrains 市场 4.8 高评分的可视化界面插件，将 Claude Code 和 OpenAI Codex 双重 AI 工具直接整合到 IntelliJ IDEA 中。

1. 按 `Ctrl/Cmd + ,` 打开设置 → Plugins → Marketplace
2. 搜索 `Claude Code GUI`，点击 Install
3. 重启 IDEA，工具窗口中出现 Claude Code 面板即成功

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/D3SHh5VkdJkq1bGA.png)

### 2.3 首次启动与配置

```Bash
# 进入你的项目目录
cd ~/my-project

# 启动 Claude Code
claude
```

❌ 配置对应环境变量 - 默认一次性配置 或者 系统级别配置（建议采用 cc-switch 工具进行管理，下文介绍）

| 环境               | 设置临时环境变量的命令 | 生效范围             |
| ------------------ | ---------------------- | -------------------- |
| Linux/macOS 终端   | `export 变量名=值`     | 当前终端会话         |
| Windows CMD        | `set "变量名=值"`      | 当前 CMD 窗口        |
| Windows PowerShell | `$env:变量名="值"`     | 当前 PowerShell 会话 |

```text
export ANTHROPIC_BASE_URL=http:xxx.xx
export ANTHROPIC_AUTH_TOKEN=API_Key
```

#### 2.3.1 启动参数速查

除了直接输入 `claude` 启动，还可以通过参数控制启动行为：

| 参数                                    | 作用                     | 适用场景                 |
| --------------------------------------- | ------------------------ | ------------------------ |
| `claude`                                | 默认启动（会询问权限）   | 日常使用                 |
| `claude --dangerously-skip-permissions` | 跳过权限询问，直接执行   | 信任的个人项目，快速开发 |
| `claude -p "你的问题"`                  | 直接提问模式，回答后退出 | 快速查询，不需要对话     |
| `claude --headless`                     | 无界面模式               | 脚本自动化               |

**关于 `--dangerously-skip-permissions`**

这个参数会让 Claude Code 跳过所有权限确认，直接执行读写文件、运行命令等操作。Anthropic 官方称之为 **"Safe YOLO mode"**。

名字里带 "dangerously" 是因为 AI 可能误修改代码、删除文件或执行非预期命令，跳过确认意味着你来不及阻止。

| 场景                                | 是否推荐 |
| ----------------------------------- | -------- |
| 自己的学习/个人项目，代码已提交 Git | ✅ 可以用 |
| 只读操作（查询、分析）              | ✅ 可以用 |
| 公司项目、开源项目                  | ❌ 不要用 |
| 第一次使用 Claude Code              | ❌ 不要用 |
| 包含敏感数据的项目                  | ❌ 不要用 |

> **新手建议**：前 1 个月不要加这个参数。让 AI 每次操作都问你，既能学到它在做什么，又能避免误操作。等你熟悉了 Claude Code 的行为模式后，在个人项目中再考虑使用，但务必先把代码提交到 Git，确保随时可回滚。

#### 2.3.2 常见报错：Unable to connect to Anthropic services

国内第一次用 Claude Code，大概率会遇到这个报错：

```smali
Unable to connect to Anthropic services
Failed to connect to api.anthropic.com: ERR_BAD_REQUEST
Please check your internet connection and network settings.
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/09BsXBCEOCUwA3HO.webp)

**原因**：Claude Code 默认检测地区，国内 IP 会被拦截。

**解决方法（一分钟搞定）**：

找到用户主目录下的 `.claude.json` 文件：

```stylus
C:\Users\你的用户名\.claude.json
```

用任意文本编辑器打开，在 JSON 对象中加入以下字段（注意给上一行末尾加逗号）：

```json
"hasCompletedOnboarding": true
```

保存后重启 Claude Code，报错消失，正常启动。

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/LAOlQgMgOdp88sMW.png)

------

#### 2.3.3 使用 cc-switch 配置和多 API 源快速切换

我们可以配置需要的大模型供应商，国内比较推荐的模型是 GLM-4.7、Kimi-K2.5，国外无脑上 Claude 4.6、GPT 5.2 即可。

如果你想在多个 API 提供商（官方、国内中转站、本地模型等）之间快速切换，推荐使用 **cc-switch**：

**安装**：访问 [GitHub Release](https://github.com/farion1231/cc-switch/releases) 下载对应系统版本，Windows 推荐下载 msi 安装包。

Windows：https://github.com/farion1231/cc-switch/releases/download/v3.11.0/CC-Switch-v3.11.0-Windows.msi

无脑下一步即可~

**功能**：

- 🔄 在不同 API 源之间快速切换，无需重启
- 🔌 支持多个供应商配置管理
- 📋 支持 MCP 配置同步
- 🖥️ 支持 WSL 环境穿透配置

**使用**：安装后在应用主界面或系统托盘选择所需的站点资源即可切换。CLI 使用需重启 Claude Code，插件版可即时生效。

**教程参考资源：**

- [cc-switch 官方文档](https://docs.packyapi.com/docs/ccswitch/)
- [cc-switch 知乎教程](https://zhuanlan.zhihu.com/p/1972328772964446521)
- [cc-switch 掘金深度指南](https://juejin.cn/post/7597252004713922602)

#### API 密钥配置关键信息

在配置 API 时，最重要的两个参数是：

- **API Key**（认证凭证）
- **请求地址**（API 端点）

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/AAPgUx4S4uqYj6So.png)

#### 国内 API 服务对比

除官方渠道外，也可选择国内 API 服务提供商。以下列出主要选择：

| 服务商                            | 特点                             | 价格模式    | 适用场景             |
| --------------------------------- | -------------------------------- | ----------- | -------------------- |
| **官方渠道**（Anthropic Console） | 最稳定、功能完整、更新及时       | 付费        | 生产环境、企业应用   |
| **LongCat AI**（美团旗下）        | 免费额度、界面简洁、支持基础功能 | 免费 + 付费 | 初学者试用、轻量应用 |
| **国内中转站**（多家）            | 功能兼容、定价灵活、快速响应     | 多为付费    | 特定需求、成本优化   |

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/YpygVZCVSKxIMIma.webp)

**推荐做法**：优先使用官方渠道或 cc-switch 工具进行配置管理，确保安全性和稳定性。如需尝试国内服务，可先用免费额度体验。

#### 2.3.4 配置文件结构

Claude Code 的配置分为**全局**和**项目**两级，理解这个结构对后续章节（CLAUDE.md、Commands、Hooks 等）很重要：

```pgsql
~/.claude/                      ← 全局配置目录（所有项目共享）
├── config.json                 ← 全局配置文件
├── auth-token.json             ← 认证令牌
├── trusted-directories.json    ← 信任的目录列表
├── cache/                      ← 缓存目录
└── logs/                       ← 日志目录

项目目录/.claude/              ← 项目级配置（仅当前项目生效）
├── config.json                 ← 项目配置（覆盖全局同名配置）
├── commands/                   ← 自定义命令（第03章详解）
├── skills/                     ← 自定义技能（第06章详解）
└── hooks/                      ← 自定义钩子（第05章详解）
```

## 3. 核心命令速查表

### 3.1 高频命令（建议收藏）

| 命令     | 功能           | 使用场景                        |
| -------- | -------------- | ------------------------------- |
| /init    | 初始化项目文档 | 第一次使用时，让AI理解项目结构  |
| /clear   | 清空对话历史   | 切换任务时释放上下文，节省token |
| /compact | 压缩对话历史   | 会话过长时保留摘要，继续对话    |
| /add-dir | 添加工作目录   | 需要同时操作多个项目时          |
| /export  | 导出对话记录   | 保存重要的对话内容              |
| /model   | 切换AI模型     | 切换到 Opus 或其他模型          |
| /memory  | 编辑记忆文件   | 自定义AI的长期记忆              |
| /resume  | 恢复上次对话   | 继续之前的工作                  |

### 3.2 快捷操作

| 操作     | 快捷键/语法                       | 说明             |
| -------- | --------------------------------- | ---------------- |
| 引用文件 | @文件名                           | 让AI关注特定文件 |
| 粘贴图片 | Ctrl + V / ALt + V 看具体终端不同 | 发送截图让AI分析 |
| 换行输入 | Shift + Alt+ Enter                | 多行输入         |
| 执行Bash | !ls -l                            | 直接执行系统命令 |
| 历史命令 | ↑ / ↓                             | 快速切换历史输入 |
| 中断执行 | Esc                               | 停止AI当前操作   |

## 4. 总结

Claude Code 的核心优势在于：

1. **自然语言交互**：不需要记复杂的命令，说人话就行
2. **主动执行能力**：不只是建议，而是直接帮你改代码、创建文件
3. **上下文理解**：理解项目结构，给出符合项目规范的代码
4. **多模态支持**：可以处理图片、分析截图

**记住这句话：Claude Code 最大的优势是理解自然语言，所以直接说出你的需求，做好指挥官，让它为你工作！**



# 第二章：30+命令与快捷键，编程效率直接翻倍

## 1. 术语表（小白必读）

| 术语              | 英文全称               | 通俗解释                          | 生活类比                           |
| ----------------- | ---------------------- | --------------------------------- | ---------------------------------- |
| CLI               | Command Line Interface | 命令行界面，通过打字操作电脑      | 发短信指挥别人干活                 |
| 交互模式          | Interactive Mode       | 可以连续对话的模式，AI 记住上下文 | 打电话聊天，可以连续说很多轮       |
| REPL              | Read-Eval-Print-Loop   | 读取-执行-打印-循环               | 你说一句 AI 回一句，不停循环       |
| 打印模式          | Print Mode             | 只输出结果，没有额外格式          | 只给答案，不说废话                 |
| Slash 命令        | Slash Commands         | 以 `/` 开头的特殊命令             | 微信的"@某人"，快速触发功能        |
| Token             | -                      | AI 处理文字的计费单位             | 打的士按公里计费，AI 按 Token 计费 |
| Checkpoint        | -                      | 代码和对话的存档点                | 游戏存档，随时可以读档重来         |
| Rewind            | -                      | 回退到之前的检查点                | 游戏读档                           |
| Compact           | -                      | 压缩对话历史，节省 Token          | 整理房间，扔掉不重要的东西         |
| Extended Thinking | -                      | 扩展思考模式，让 AI 深度分析      | 让 AI 写解题过程，不只是答案       |
| MCP               | Model Context Protocol | 让 Claude 连接外部工具的插件系统  | 手机安装 App，扩展功能             |

------

## 2. 第一次使用 Claude Code

> 前置条件：请确保已完成[第一章](https://xn--01:,10ai-4g0mr1c1go9cm3oqrb5r0459bvgk9jby92q4shl92bl0k0uk.md/)的环境准备和安装步骤。

### 2.1 启动与第一次对话

打开终端（Windows `Win+R` → `powershell`；macOS `Cmd+Space` → `Terminal`；Linux `Ctrl+Alt+T`），进入项目目录后启动：

```Bash
cd ~/你的项目路径    # 没有项目可以先 mkdir test-claude && cd test-claude
claude
```

看到 `You: █` 光标闪烁就是启动成功。试着输入第一句话：

```avrasm
You: 你好，介绍一下你自己
```

Claude 会回复自我介绍并列出它能做的事（编写代码、修复 Bug、搜索文件等）。能正常收到回复，说明一切就绪。

### 2.2 验证与退出

**快速验证**：让 Claude 创建一个文件，确认它能正常读写：

```avrasm
You: 创建一个hello.py文件，内容是打印"Hello Claude Code"
```

Claude 会请求确认 → 按回车 → 文件创建成功。用 `cat hello.py` 验证内容。

**退出方式**：输入 `/exit`，或按 `Ctrl+D`（macOS/Linux）/ `Ctrl+Z` 回车（Windows）。

### 2.3 初始化项目（强烈推荐！）

> ⚠️ **关键**：新项目必须初始化。更关键的是：**每次项目有重大变化时，也可以重新运行 `/init` 或 `/zcf:init-project` 来更新 Claude 的上下文！**

#### 为什么要初始化？

让 Claude 自动理解项目结构、技术栈、编码规范和目标，后续对话都会自动应用这些信息。

#### 两种初始化方式

**标准初始化**：

```bash
You: /init
```

自动扫描项目 → 生成/更新 `CLAUDE.md` → 后续对话自动带上上下文

**增强初始化**（ZCF 工具链）：

```bash
You: /zcf:init-project
```

额外配置 MCP 服务、插件推荐、多级 CLAUDE.md

#### 核心建议：每次迭代都可以更新

不要把 `/init` 只看作一次性操作！项目演进时，随时可以重新初始化：

| 场景                  | 建议             |
| --------------------- | ---------------- |
| 🆕 新项目第一次使用    | **必须** `/init` |
| 🔄 调整了项目结构/目录 | 重新 `/init`     |
| 🏗️ 添加新的大型模块    | 重新 `/init`     |
| 📝 更新了编码规范      | 重新 `/init`     |
| 🛠️ 改用新框架/技术栈   | 重新 `/init`     |
| 💻 仅改动代码逻辑      | 无需 `/init`     |

#### 典型工作流

```bash
# Day 1：初始化
You: /init  # 第一次完整扫描

# 开发迭代，完成认证模块
You: 实现用户登录功能

# Day 2：项目更新
You: /init  # 重新扫描，更新上下文（添加了新的 API 服务层）

# 现在 Claude 知道新的 API 层规范
You: 在新 API 层实现数据缓存

# Day 3：规范升级
You: /init  # 重新同步最新规范

# AI 按新规范生成代码
You: 重构认证模块
```

#### 验证初始化

```bash
You: /memory
# 查看生成的 CLAUDE.md，确认项目信息已正确加载
```

------

#### 相关截图

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/8y3WWT7kxZ05rwLA.png)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/YQN5n0un2CnZtIhw.png) ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/VDGeT31ElXoJ953W.png)

## 3. 交互模式与启动选项

交互模式（REPL）是 Claude Code 的核心方式：你说一句，AI 回一句，始终记住上下文，循环往复。

启动时可以附加参数控制行为：

```Bash
claude                                  # 默认启动
claude --project /path/to/project       # 指定项目目录，不需要先 cd
```

| 选项             | 简写 | 作用             | 适用场景         |
| ---------------- | ---- | ---------------- | ---------------- |
| `--verbose`      | 无   | 显示详细日志     | 调试排查问题     |
| `--model <name>` | `-m` | 指定 AI 模型     | 切换到特定模型   |
| `--continue`     | `-c` | 恢复最近一次会话 | 继续昨天的工作   |
| `--resume <id>`  | `-r` | 恢复指定会话     | 恢复某次特定对话 |

> 基础启动参数（`--dangerously-skip-permissions`、`-p`、`--headless`）见[第一章 2.3.1](https://xn--01:,10ai-4g0mr1c1go9cm3oqrb5r0459bvgk9jby92q4shl92bl0k0uk.md/#231-启动参数速查)。

### 3.1 三种操作模式

Claude Code 有三种操作模式，**按 `Shift + Tab` 循环切换**，右上角状态栏实时显示当前模式：

| 模式         | 状态栏显示  | 行为                                                    | 适用场景                               |
| ------------ | ----------- | ------------------------------------------------------- | -------------------------------------- |
| 默认模式     | （无标记）  | 每次文件修改、执行命令都会暂停询问你确认                | 新手、陌生项目、敏感操作               |
| 自动接受编辑 | `Auto-edit` | 文件读写自动确认，Bash 命令仍需手动确认                 | 熟悉项目、大量代码修改时               |
| 规划模式     | `Plan mode` | Claude 只分析和规划，不执行任何操作，输出"我打算做什么" | 复杂任务拆解、评估风险后再决定是否执行 |

**切换方法**：

- 键盘：`Shift + Tab`（循环切换，默认 → 自动接受编辑 → 规划模式 → 默认）
- 鼠标：点击输入框左下角的模式状态标签

> **新手建议**：前期保持默认模式，每次操作都看一眼 Claude 要做什么再确认。熟悉后再切到自动接受编辑提升速度；遇到复杂任务先用规划模式摸清思路，确认无误再切回执行。

------

## 4. 输入技巧

### 4.1 快捷输入符号

| 前缀 | 作用                                 | 示例                     |
| ---- | ------------------------------------ | ------------------------ |
| `#`  | 添加内容到记忆文件（CLAUDE.md）      | `# 本项目使用TypeScript` |
| `@`  | 文件路径自动补全，让 AI 关注特定文件 | `@src/app.js`            |
| `!`  | 直接执行 Bash 命令                   | `!npm test`              |

### 4.2 多行输入

| 方法       | 快捷键         | 说明                        |
| ---------- | -------------- | --------------------------- |
| 反斜杠换行 | `\` + Enter    | 所有终端通用                |
| macOS 默认 | Option + Enter | macOS 终端                  |
| 终端配置后 | Shift + Enter  | 运行 `/terminal-setup` 配置 |
| 控制序列   | Ctrl + J       | 换行符                      |
| 直接粘贴   | 粘贴代码块     | 自动识别多行                |

------

## 5. 对话管理技巧

| 命令       | 效果     | 保留内容          | Token 节省 | 适用场景                           |
| ---------- | -------- | ----------------- | ---------- | ---------------------------------- |
| `/clear`   | 完全清空 | 仅 CLAUDE.md 配置 | 100%       | 切换到完全不同的新任务             |
| `/compact` | 压缩历史 | 关键信息摘要      | 40-60%     | 同一任务内响应变慢、Token 接近上限 |

> **一句话原则**：换任务用 `/clear`，觉得慢了用 `/compact`。

------

## 6. Slash 命令大全

> 所有 Slash 命令都必须在交互模式中使用（输入 `claude` 进入后才能用）。

### 6.1 命令速查总表

**基础控制**

| 命令       | 作用             | 备注                                |
| ---------- | ---------------- | ----------------------------------- |
| `/help`    | 显示所有可用命令 | 忘记命令时随时查                    |
| `/exit`    | 退出 Claude Code | 也可用 `Ctrl+D`                     |
| `/clear`   | 清空对话历史     | CLAUDE.md 配置不会丢失              |
| `/compact` | 压缩对话历史     | 可带指令：`/compact 保留数据库讨论` |

**上下文与费用**

| 命令       | 作用                                |
| ---------- | ----------------------------------- |
| `/context` | 可视化 Token 使用情况（彩色进度条） |
| `/cost`    | 显示当前会话的 Token 用量和费用     |
| `/usage`   | 显示账户整体用量和限额（订阅用户）  |

**模型与会话**

| 命令      | 作用           | 备注                                       |
| --------- | -------------- | ------------------------------------------ |
| `/model`  | 切换 AI 模型   | 也可直接 `/model claude-opus-4-5-20251101` |
| `/resume` | 恢复之前的会话 | 列出最近会话供选择                         |
| `/export` | 导出对话记录   | 支持 Markdown / JSON / HTML                |
| `/rename` | 重命名当前会话 | 方便后续查找                               |

**项目配置**

| 命令           | 作用                          |
| -------------- | ----------------------------- |
| `/init`        | 分析项目并创建 CLAUDE.md 配置 |
| `/memory`      | 打开编辑器修改 CLAUDE.md      |
| `/permissions` | 查看和修改 Claude 的权限设置  |

**开发辅助**

| 命令      | 作用                     |
| --------- | ------------------------ |
| `/review` | 审查未提交的代码变更     |
| `/todos`  | 列出对话中追踪的 TODO 项 |
| `/agents` | 查看活跃的子代理状态     |

**诊断与状态**

| 命令      | 作用                                      |
| --------- | ----------------------------------------- |
| `/doctor` | 系统健康检查（Node.js、API 连接、MCP 等） |
| `/status` | 显示版本、模型、账户等完整状态            |

**MCP 与插件**

| 命令      | 作用                      |
| --------- | ------------------------- |
| `/mcp`    | 查看和管理 MCP 服务器连接 |
| `/plugin` | 安装、启用、禁用插件      |
| `/hooks`  | 配置事件触发的自动化脚本  |

**其他**

| 命令              | 作用                                 |
| ----------------- | ------------------------------------ |
| `/stats`          | 使用习惯统计（会话数、消息数、费用） |
| `/vim`            | 启用 Vim 模式编辑                    |
| `/release-notes`  | 查看最新版本更新日志                 |
| `/bug`            | 向 Anthropic 提交 Bug 报告           |
| `/terminal-setup` | 配置终端以支持 Shift+Enter 换行      |

------

### 6.2 上下文与费用管理

`/context` 会用彩色进度条显示 Token 使用占比，帮助你判断是否需要 `/compact`：

```mathematica
████████████░░░░░░░░  60% (120K / 200K tokens)
```

`/cost` 显示当前会话的实际费用，适合按量付费的用户随时关注开销。

### 6.3 模型切换

```bash
/model                              # 交互选择模型
/model claude-opus-4-5-20251101     # 直接指定
```

快捷键：macOS `Option+P` / Windows `Alt+P`

| 模型   | 速度 | 能力 | 成本 | 适用场景           |
| ------ | ---- | ---- | ---- | ------------------ |
| Haiku  | 最快 | 基础 | 最低 | 简单任务、快速查询 |
| Sonnet | 中等 | 强大 | 中等 | 日常开发（推荐）   |
| Opus   | 较慢 | 最强 | 最高 | 复杂任务、关键决策 |

### 6.4 Checkpoint 与 Rewind（回退功能）

Checkpoint（检查点）= 游戏存档，Rewind（回退）= 读档。Claude Code 在每次文件修改时自动创建检查点，让你大胆实验、随时回退。

**触发方式**：

- 快速按两次 `Esc` 键（最快）
- 输入 `/rewind` 命令

**三种恢复选项**：

| 选项       | 效果                         | 适用场景                  |
| ---------- | ---------------------------- | ------------------------- |
| 仅恢复对话 | 保留代码改动，重置 AI 上下文 | AI 理解错了，但代码改对了 |
| 仅恢复代码 | 保留对话历史，回退文件修改   | 代码改错了，但讨论有价值  |
| 同时恢复   | 代码和对话都回到之前状态     | 完全走错方向，从头来      |

> **重要限制**：Checkpoint 只追踪 Claude 的文件编辑工具（Write、Edit），**不追踪 Bash 命令的修改**（如 `!mv`、`!rm`）。重要操作尽量让 Claude 用文件工具修改，并配合 Git 使用。

### 6.5 会话管理

```Bash
# 命令行快速恢复
claude -c                    # 恢复最近一次会话
claude -r ses_abc123         # 恢复指定会话

# 交互模式中恢复
/resume                      # 列出最近会话供选择
```

导出对话：

```elm
/export                      # 默认 Markdown 格式
/export --clipboard          # 导出到剪贴板
/export --format json        # 指定 JSON 格式
```

给会话命名（方便后续查找）：

```clean
/rename auth-module-implementation
```

### 6.6 项目配置

- `/init`：自动分析项目结构并生成 CLAUDE.md，让 Claude 理解你的项目（详见第一章）
- `/memory`：打开编辑器修改 CLAUDE.md，也可以用 `# 前缀` 快速添加记忆
- `/permissions`：查看当前权限设置（文件读写、Bash 命令等），按需调整

### 6.7 开发辅助

- `/review`：审查未提交的代码变更，Claude 会分析安全问题、性能隐患和代码风格
- `/todos`：列出对话中追踪的 TODO 项及完成状态
- `/agents`：查看正在运行的子代理（用于复杂任务分解时）

### 6.8 诊断与状态

遇到问题时优先用这两个命令排查：

- `/doctor`：全面健康检查（Node.js 版本、API 连接、MCP 状态等），类似"体检报告"
- `/status`：显示当前版本、模型、账户、MCP 连接等完整状态信息

### 6.9 MCP 与插件

- `/mcp`：查看已连接的 MCP 服务器及其提供的工具列表
- `/plugin`：管理已安装的插件（启用/禁用）
- `/hooks`：查看已配置的事件钩子（如写文件前自动 lint、提交后通知等）

> MCP、Plugins、Hooks 的详细配置分别在第04、07、05章展开。

### 6.10 其他命令

- `/stats`：查看使用习惯统计（会话数、消息数、费用趋势）
- `/vim`：启用 Vim 模式编辑输入框（`h/j/k/l` 移动，`i` 插入，`Esc` 普通模式）
- `/release-notes`：查看最新版本更新日志
- `/bug`：向 Anthropic 提交 Bug 报告（引导式描述问题）
- `/terminal-setup`：配置终端支持 Shift+Enter 换行输入

------

## 7. 快捷键速查

### 7.1 通用控制

| 快捷键                   | 作用                   | 备注                                                         |
| ------------------------ | ---------------------- | ------------------------------------------------------------ |
| `Ctrl + C`               | 取消当前输入或中断生成 | 标准中断信号                                                 |
| `Ctrl + D`               | 退出 Claude Code       | EOF 信号                                                     |
| `Ctrl + L`               | 清除终端屏幕           | 对话历史不受影响                                             |
| `Ctrl + O`               | 切换详细输出           | 显示/隐藏工具调用细节                                        |
| `Ctrl + R`               | 反向搜索历史命令       | 详见 [7.2](https://www.codefather.cn/post/2034534765402554370#72-历史搜索ctrlr) |
| `Esc + Esc`              | 打开 Rewind 菜单       | 回退代码/对话，详见 [6.4](https://www.codefather.cn/post/2034534765402554370#64-checkpoint-与-rewind回退功能) |
| `Tab`                    | 切换 Extended Thinking | 开/关扩展思考模式                                            |
| `Shift + Tab`            | 切换权限模式           | 自动/计划/普通                                               |
| `↑` / `↓`                | 浏览历史命令           | 快速复用之前的输入                                           |
| `Option + P` / `Alt + P` | 切换 AI 模型           | macOS 用 Option，Windows/Linux 用 Alt                        |
| `Ctrl + V` / `Alt + V`   | 粘贴图片               | macOS/Linux 用 `Ctrl+V`，Windows 用 `Alt+V`                  |

> 多行输入快捷键见 [4.2 多行输入](https://www.codefather.cn/post/2034534765402554370#42-多行输入)。

### 7.2 历史搜索（Ctrl+R）

1. 按 `Ctrl + R` 进入搜索模式
2. 输入关键词，自动匹配历史命令
3. 再按 `Ctrl + R` 浏览更早的匹配
4. `Tab` 或 `Esc` 接受当前匹配，`Enter` 直接执行，`Ctrl + C` 取消

### 7.3 后台运行

| 操作                 | 方式                     |
| -------------------- | ------------------------ |
| 提示 Claude 后台运行 | 在提示词中说"在后台运行" |
| 手动转后台           | `Ctrl + B`               |
| tmux 用户            | 按两次 `Ctrl + B`        |

适合后台的任务：构建工具（[Webpack](https://www.mianshiya.com/bank/1831174878121283585)、vite）、测试运行器（jest、pytest）、开发服务器等。

### 7.4 Vim 模式

输入 `/vim` 启用后，输入框支持 Vim 风格编辑：

| 操作         | 按键              | 说明                       |
| ------------ | ----------------- | -------------------------- |
| 进入普通模式 | `Esc`             | 退出插入模式               |
| 插入         | `i` / `a` / `o`   | 光标前 / 光标后 / 下方新行 |
| 移动         | `h` `j` `k` `l`   | 左 / 下 / 上 / 右          |
| 按词移动     | `w` / `b`         | 下一个词 / 上一个词        |
| 行首/行尾    | `0` / `$`         |                            |
| 删除         | `x` / `dd` / `dw` | 删字符 / 删整行 / 删单词   |
| 修改整行     | `cc`              | 清空当前行并进入插入模式   |
| 重复上次操作 | `.`               |                            |

------

## 8. 最佳实践

### 8.1 日常工作流程

推荐的每日流程：

```Bash
$ claude -c                          # 1. 恢复昨天的会话
You: /status                         # 2. 检查状态
You: 我今天要完成用户认证模块          # 3. 开始工作
You: /context                        # 4. 工作中定期检查 Token 使用
You: /compact                        # 5. Token 超过 60% 时压缩
You: /export ~/docs/auth.md          # 6. 完成重要功能后导出对话
You: /rename auth-module-day2        # 7. 下班前重命名会话
```

### 8.2 省钱技巧

**Token 优化**：

| 技巧                                         | 节省比例 |
| -------------------------------------------- | -------- |
| 简单问题关闭 Extended Thinking（`Tab` 切换） | ~70%     |
| 定期使用 `/compact`                          | 40-60%   |
| 完成任务后 `/clear`                          | 100%     |
| 使用 Sonnet 而非 Opus                        | ~80%     |
| 简洁描述需求，避免冗余上下文                 | ~30%     |

**模型选择策略**：

```undefined
简单查询（函数解释、格式转换）  → Haiku（最便宜）
日常开发（编码、重构、调试）    → Sonnet（性价比最高）
关键决策（架构设计、复杂分析）  → Opus（最强）
```

### 8.3 配置别名提高效率

**macOS / Linux**（添加到 `~/.bashrc` 或 `~/.zshrc`）：

```Bash
alias cc="claude --dangerously-skip-permissions"   # 快速启动
alias cr="claude -c"                               # 恢复会话
alias ccv="claude --verbose"                        # 调试模式
alias cco="claude --model claude-opus-4-5-20251101" # 使用 Opus
```

**Windows PowerShell**（添加到 `$PROFILE`）：

```PowerShell
function cc { claude --dangerously-skip-permissions }
function cr { claude -c }
function ccv { claude --verbose }
```

### 8.4 善用 Checkpoint 大胆实验

Checkpoint 让你可以放心尝试激进方案：

```avrasm
You: 帮我用新架构重构这个模块     # 尝试方案 A（自动创建检查点）
[Esc + Esc → 回退]                # 不满意？回退
You: 换工厂模式重构               # 尝试方案 B
[Esc + Esc → 回退]                # 还不满意？继续回退
You: 用策略模式试试               # 尝试方案 C，直到找到满意的
```

### 8.5 团队协作

**分享会话**：

```elm
/export --format html shared/auth-discussion.html
```

**创建可复用的团队命令**：

```Bash
mkdir -p .claude/commands
echo "Review this code for security and performance issues:" > .claude/commands/security-review.md
```

提交到 Git 后，团队成员都可以用 `/security-review` 触发统一的代码审查流程。

------

## 附录：完整命令速查表

**CLI 启动选项**

| 选项                             | 简写 | 作用                   |
| -------------------------------- | ---- | ---------------------- |
| `--version`                      | `-v` | 显示版本               |
| `--help`                         | `-h` | 显示帮助               |
| `--print`                        | `-p` | 打印模式（回答后退出） |
| `--model <name>`                 | `-m` | 指定模型               |
| `--continue`                     | `-c` | 恢复最近会话           |
| `--resume <id>`                  | `-r` | 恢复指定会话           |
| `--project <path>`               | 无   | 指定项目目录           |
| `--verbose`                      | 无   | 详细输出               |
| `--dangerously-skip-permissions` | 无   | 跳过权限确认           |

**Slash 命令**

| 命令       | 作用            |      | 命令             | 作用       |
| ---------- | --------------- | ---- | ---------------- | ---------- |
| `/help`    | 显示帮助        |      | `/init`          | 初始化项目 |
| `/exit`    | 退出            |      | `/memory`        | 编辑记忆   |
| `/clear`   | 清空对话        |      | `/permissions`   | 管理权限   |
| `/compact` | 压缩对话        |      | `/review`        | 代码审查   |
| `/context` | 查看 Token 使用 |      | `/todos`         | 查看待办   |
| `/cost`    | 查看费用        |      | `/rewind`        | 回退功能   |
| `/model`   | 切换模型        |      | `/mcp`           | 管理 MCP   |
| `/status`  | 查看状态        |      | `/plugin`        | 管理插件   |
| `/doctor`  | 系统诊断        |      | `/hooks`         | 管理 Hooks |
| `/resume`  | 恢复会话        |      | `/vim`           | Vim 模式   |
| `/export`  | 导出对话        |      | `/stats`         | 使用统计   |
| `/rename`  | 重命名会话      |      | `/usage`         | 使用量     |
|            |                 |      | `/release-notes` | 更新日志   |
|            |                 |      | `/bug`           | 报告 Bug   |

**快捷键**

| 快捷键   | 作用         |      | 快捷键         | 作用                   |
| -------- | ------------ | ---- | -------------- | ---------------------- |
| `Ctrl+C` | 取消/中断    |      | `Esc+Esc`      | Rewind 菜单            |
| `Ctrl+D` | 退出         |      | `Tab`          | 切换 Extended Thinking |
| `Ctrl+L` | 清屏         |      | `Shift+Tab`    | 切换权限模式           |
| `Ctrl+O` | 切换详细输出 |      | `Option/Alt+P` | 切换模型               |
| `Ctrl+R` | 搜索历史     |      | `Ctrl/Alt+V`   | 粘贴图片               |
| `Ctrl+B` | 转后台运行   |      | `↑` / `↓`      | 浏览历史命令           |

------

## 总结

本章你已掌握：

1. **交互模式**：REPL 核心工作方式
2. **30+ Slash 命令**：从基础控制到 MCP 管理
3. **Checkpoint/Rewind**：大胆实验、随时回退
4. **快捷键操作**：高效控制、后台运行、Vim 模式
5. **最佳实践**：省钱技巧、别名配置、团队协作

# 第三章：告别重复提示词，自定义Commands让AI秒懂你

## 1. 前言

学完前两章，你已经能熟练启动 Claude Code、使用各种 Slash 命令和快捷键。

但你可能发现一个痛点：**每次让 Claude 做同类型的事，都要重复一大段要求**。

Commands（自定义命令）就是解决这个问题的——**把重复的提示词压缩成一个词，一次配置，永久生效。**

------

## 2. Commands 是什么

### 2.1 什么是 Slash 命令

Slash 命令是 Claude Code 的"快捷方式"：输入 `/命令名` 触发预设操作。

**工作原理**：输入 `/write AI教程` → 找到 `.claude/commands/write.md` → 读取内容作为提示词 → 把 `AI教程` 赋值给 `$ARGUMENTS` → 执行。

核心等式：**命令名 = 文件名（不含 `.md`）**，**参数 = `$ARGUMENTS`**。

### 2.2 命令的三大类型

| 类型         | 存放位置              | 生效范围                        |
| ------------ | --------------------- | ------------------------------- |
| 内置命令     | 程序内部（不可改）    | 所有项目                        |
| 项目级自定义 | `.claude/commands/`   | 仅当前项目，可提交 Git 团队共享 |
| 用户级自定义 | `~/.claude/commands/` | 所有项目，个人通用工具          |

选择原则：会话管理/诊断用内置；项目专属工作流用项目级；跨项目通用工具用用户级。

### 2.3 为什么要学 Commands

| 对比维度 | 手动输入     | 使用 Commands      |
| -------- | ------------ | ------------------ |
| 效率     | 每次重复输入 | 一次配置，永久使用 |
| 一致性   | 容易遗漏要求 | 标准化执行         |
| 可复用   | 困在聊天记录 | 团队共享、版本控制 |

------

## 3. 创建第一个自定义命令

**Step 1：建目录**

```Bash
# macOS / Linux
mkdir -p .claude/commands

# Windows PowerShell
New-Item -ItemType Directory -Path ".claude\commands" -Force
```

**Step 2：创建命令文件** `.claude/commands/hello.md`

```markdown
# 问候命令

用户想要问候的对象是：$ARGUMENTS

如果没有提供名字，请使用"朋友"作为默认称呼。
请用热情友好的方式问候，并询问今天可以帮助什么。
```

> 推荐新手直接在 Claude Code 对话框说："帮我创建文件 `.claude/commands/hello.md`，内容是……"，让 AI 帮你写文件。

**Step 3：测试**

```nix
claude
You: /hello 张三   → 你好，张三！……
You: /hello        → 你好，朋友！……
```

> **小技巧**：输入 `/` 后按 `Tab` 键可查看所有可用命令。

------

## 4. 自定义命令开发进阶

### 4.1 命令文件结构

命令文件由两部分组成：**YAML frontmatter 配置区**（机器读）+ **Markdown 正文**（AI 读）。

```markdown
---
description: 公众号文章创作命令
argument-hint: <主题关键词>
allowed-tools:
  - Read
  - Write
  - WebSearch
model: claude-sonnet-4-5-20250929
---

# 公众号文章创作

你是一位资深的公众号写作专家。
主题：$ARGUMENTS

写作要求：接地气 · 1500-2000字 · 金句开头 → 核心内容 → 行动号召
```

### 4.2 作用域与优先级

**优先级**：项目级 > 用户级 > 内置命令（非核心）

> `/clear`、`/help`、`/compact` 等核心内置命令受保护，自定义命令无法覆盖。

支持子目录，用 `:` 作命名空间：

```verilog
.claude/commands/
├── write.md              # /write
├── dev/
│   └── code-review.md    # /dev:code-review
└── test/
    └── generate.md       # /test:generate
```

### 4.3 frontmatter 配置详解

| 配置项                     | 作用                                   |
| -------------------------- | -------------------------------------- |
| `description`              | 命令描述，显示在 `/help` 和 Tab 补全中 |
| `argument-hint`            | 输入命令后显示的参数占位符提示         |
| `allowed-tools`            | 限制可调用的工具（安全边界）           |
| `model`                    | 强制指定模型，覆盖当前会话模型         |
| `disable-model-invocation` | 设为 `true` 时只做文本替换，不调用 AI  |

**`disable-model-invocation` 示例**（节省 Token 的纯模板命令）：

```markdown
---
description: 快速插入版权声明
disable-model-invocation: true
---

© 2025 $ARGUMENTS. All rights reserved.
```

执行 `/copyright 凯神` → 直接输出 `© 2025 凯神. All rights reserved.`，不经过 AI 处理。

### 4.4 $ARGUMENTS 参数处理

`$ARGUMENTS` 接收命令后的全部输入（整段字符串）：

```bash
/write AI工具            → $ARGUMENTS = "AI工具"
/write AI工具 技术 3000  → $ARGUMENTS = "AI工具 技术 3000"
/write                   → $ARGUMENTS = ""（空）
```

多参数解析和空值校验直接用自然语言在提示词中描述即可：

```markdown
$ARGUMENTS 格式：<主题> [风格] [字数]
- 第一个词：主题（必需，若为空请提示用户补充）
- 第二个词：风格（可选，默认"接地气"）
- 第三个词：字数（可选，默认 1500）
```

### 4.5 可调用的工具

| 工具名      | 功能             | 常用场景              |
| ----------- | ---------------- | --------------------- |
| `Read`      | 读取文件         | 分析代码、读取配置    |
| `Write`     | 写入新文件       | 创建文件、保存结果    |
| `Edit`      | 编辑已有文件     | 修改代码              |
| `Bash`      | 执行命令         | 运行测试、Git 操作    |
| `WebSearch` | 网络搜索         | 获取最新信息          |
| `WebFetch`  | 抓取网页内容     | 下载指定页面分析      |
| `Glob`      | 按文件名匹配查找 | 批量找 `*.md`、`*.ts` |
| `Grep`      | 按内容搜索文件   | 找含 TODO 的代码      |
| `Task`      | 启动子代理       | 并行执行复杂任务      |
| `TodoWrite` | 任务管理         | 创建和更新待办清单    |

> **最小权限原则**：审查类只需 `Read, Grep`；写代码加 `Write, Edit`；跑命令才开 `Bash`。
>
> MCP 工具命名格式：`mcp__服务器名__工具名`（如 `mcp__github__create_issue`），详见第04章。

### 4.6 条件逻辑设计

Markdown 不支持代码逻辑，但 Claude 能理解自然语言描述的条件分支：

```markdown
根据 $ARGUMENTS 判断：
- 包含"深度"或"详细" → 深度分析，输出 3000 字以上完整报告
- 包含"快速"或"简要" → 快速分析，输出 500 字以内摘要
- 其他情况（默认）    → 标准分析，输出 1500 字标准报告
检查 $ARGUMENTS 的第一个关键词：
- "测评" → 测评模板，重点写优缺点对比
- "教程" → 教程模板，重点写步骤和代码
- "对比" → 对比模板，重点写表格和结论
- 其他   → 通用模板
```

### 4.7 实战：完整写作命令

文件：`.claude/commands/write.md`

```markdown
---
description: 公众号文章全自动创作，从信息收集到成稿保存
argument-hint: <主题关键词>
allowed-tools:
  - Read
  - Write
  - WebSearch
  - Grep
---

# 公众号文章创作系统

你是资深公众号写作专家，擅长创作接地气、有深度的技术科普文章。

**主题**：$ARGUMENTS

## 执行步骤

1. **信息收集**：WebSearch 搜索"$ARGUMENTS 最新资讯 2025"，收集核心概念、最新动态、用户痛点
2. **构思大纲**：金句开头 → 问题引入(2-3段) → 核心内容(5-8段) → 总结号召
3. **撰写文章**：说人话、用类比、多短句，字数 1500-2000，每段≤150字
4. **保存文章**：Write 保存到 `articles/drafts/[日期]_[主题].md`
5. **生成标题**：5个备选标题（含数字、引发好奇、≤30字）

## 输出格式

# [选定标题]

[文章正文]

---
## 备选标题
1. [标题1] ... 5. [标题5]
```

使用：`/write Claude Code入门` → 自动完成搜索、构思、撰写、保存全流程。

------

## 5. 命令高级用法

> 命名空间（子目录组织）见 [4.2 作用域与优先级](https://www.codefather.cn/post/2035230703787999233#42-作用域与优先级)。

### 5.1 命令组合与链式调用

单个命令可以描述多步骤工作流，Claude 会按顺序执行：

```markdown
# 完整发布流程

1. WebSearch 搜索 "$ARGUMENTS 最新动态"
2. 根据搜索结果撰写文章并 Write 保存
3. Read 读取文章，进行自我审查并输出修改意见
4. 输出最终版本与 5 个备选标题
```

多命令串联：先 `/research 主题` 生成素材文件，再 `/write 主题` 读取该文件写作，每个命令职责单一、可单独复用。

### 5.2 模块化设计

把多个命令共用的角色设定、写作风格提取为**共享片段**，存入 `.claude/modules/`：

```nix
.claude/
├── commands/
│   ├── write.md        # 引用 modules/writer-role.md
│   └── review.md       # 引用 modules/writer-role.md
└── modules/
    └── writer-role.md  # 共享角色设定，修改一次全部生效
```

在命令文件中加载模块（需在 `allowed-tools` 开启 `Read`）：

```markdown
请先读取 `.claude/modules/writer-role.md` 作为角色设定，再执行以下任务……
```

### 5.3 社区命令资源

| 资源                 | 搜索关键词         | 内容                       |
| -------------------- | ------------------ | -------------------------- |
| Claude Command Suite | GitHub 搜索        | 审查、测试、文档类命令集合 |
| Awesome Claude Code  | GitHub 搜索        | 社区精选命令、模板、工作流 |
| 官方文档示例         | docs.anthropic.com | 官方推荐命令写法           |

> 使用社区命令前，先审查 `allowed-tools` 列表，避免权限过宽。

### 5.4 故障排查

| 现象                   | 原因          | 解决方法                                    |
| ---------------------- | ------------- | ------------------------------------------- |
| 输入命令无响应         | 文件路径错误  | 确认路径：`.claude/commands/命令名.md`      |
| 命名空间命令找不到     | 目录层级错误  | `/dev:review` 对应 `commands/dev/review.md` |
| frontmatter 配置未生效 | YAML 格式有误 | 检查缩进用空格、冒号后有空格                |
| 工具调用被拒绝         | 工具未声明    | 将所需工具加入 `allowed-tools` 列表         |
| 参数被截断             | 特殊字符问题  | 用引号包裹：`/write "AI 教程 2025"`         |

------

## 6. 内置命令速查

> 详细用法见[第二章 6. Slash 命令大全](https://xn--02:30+,-ix3k85d6ye67rjn7ajwjpsam0rhr0e8fmzqnlzdmvbu38bdqedy8m.md/#6-slash-命令大全)，这里提供速查表。

| 分类       | 命令                            | 功能                       | 重要度 |
| ---------- | ------------------------------- | -------------------------- | ------ |
| 会话管理   | `/clear` `/compact` `/resume`   | 清空/压缩/恢复会话         | ⭐⭐⭐    |
|            | `/export` `/rename`             | 导出/重命名会话            | ⭐⭐     |
| 上下文控制 | `/context` `/model`             | 查看Token / 切换模型       | ⭐⭐⭐    |
|            | `/cost` `/usage`                | 查看费用/用量              | ⭐⭐     |
| 项目配置   | `/init` `/add-dir`              | 初始化CLAUDE.md / 添加目录 | ⭐⭐⭐    |
|            | `/memory` `/permissions`        | 编辑记忆 / 管理权限        | ⭐⭐     |
| 开发辅助   | `/rewind` `/review` `/todos`    | 回退/审查/待办             | ⭐⭐⭐    |
|            | `/agents`                       | 管理子代理                 | ⭐⭐     |
| 诊断工具   | `/doctor` `/status`             | 健康检查/完整状态          | ⭐⭐     |
| MCP 相关   | `/mcp` `/hooks`                 | 管理MCP/Hooks              | ⭐⭐⭐    |
| 其他       | `/help` `/bug` `/release-notes` | 帮助/报告Bug/更新日志      | ⭐⭐     |

------

## 7. 总结

本章你已掌握：

1. **Commands 本质**：`.claude/commands/` 下的 Markdown 文件，文件名即命令名，`$ARGUMENTS` 接收参数
2. **三种类型**：内置 / 项目级 / 用户级，按需选择
3. **frontmatter**：5 个配置项控制描述、参数提示、工具权限、模型、是否调用 AI
4. **最小权限原则**：按角色只开放必要工具
5. **条件逻辑**：自然语言描述分支，Claude 正确执行
6. **高级用法**：链式调用多步骤工作流、模块化共享片段、社区命令资源借力

# 第四章：让Claude连上一切——MCP、Hooks与Subagent实战

## 1. 前言

学完 Commands，你已经能把重复提示词压缩成一个词。

但 Claude 本身有能力边界——它不能直接操作数据库、不能搜网页、不能推代码到 GitHub。

**MCP 和 Hooks 就是突破这个边界的两把钥匙：**

| 工具  | 解决什么问题                                       | 类比                     |
| ----- | -------------------------------------------------- | ------------------------ |
| MCP   | 让 Claude 调用外部服务（数据库/GitHub/搜索）       | 给 Claude 装"插件"       |
| Hooks | 让 Claude 在操作前后自动触发脚本（lint/测试/通知） | 给 Claude 设"自动触发器" |

------

## 2. MCP 集成

### 2.1 MCP 是什么

MCP（Model Context Protocol）是 AI 连接外部工具的**"USB 标准"**——统一协议，任何 MCP Server 都能即插即用地被 Claude 调用。

| 对比     | 没有 MCP         | 有 MCP               |
| -------- | ---------------- | -------------------- |
| 对接成本 | 每个工具单独开发 | 一次开发，处处复用   |
| 兼容性   | 各平台不通用     | 开放标准，跨平台     |
| 生态     | 各自为战         | 社区共建，直接拿来用 |

### 2.2 配置方式

**方式一：配置文件（推荐团队）**

在项目根目录创建 `.mcp.json`：

```json
{
  "mcpServers": {
    "服务器名": {
      "command": "npx",
      "args": ["-y", "包名", "附加参数"],
      "env": {
        "API_KEY": "${环境变量名}"
      }
    }
  }
}
```

> `${GITHUB_TOKEN}` 会自动读取同名环境变量，**不要把密钥硬写进文件**。

**方式二：CLI 快速添加（个人测试）**

```bash
claude mcp add <具体mcp地址>   # 添加
claude mcp list                          # 查看所有
claude mcp remove <名称>                 # 删除
claude mcp add filesystem -s user -- npx -y @modelcontextprotocol/server-filesystem D:/Desktop D:/develop
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/TtKlQo64ZevYLYm1.webp)

```bash
claude mcp list
或者/mcp
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/VHphYfq5r7pqJNCX.webp)

```nsis
claude mcp remove filesystem -s user
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/O6mndJpFTW79fQ0F.png)

删除成功：

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/i1Q0sCWmNRYwKAVH.png)

**作用域指定：**

```bash
claude mcp add --scope project <名称> ...  # 项目级（默认）
claude mcp add --scope user <名称> ...     # 用户级（全局）
```

### 2.3 常用服务器速查

| 分类   | 服务器       | 包名                                        | 需 API Key    | 推荐 |
| ------ | ------------ | ------------------------------------------- | ------------- | ---- |
| 文件   | filesystem   | `@modelcontextprotocol/server-filesystem`   | ❌             | ⭐⭐⭐  |
| 文件   | memory       | `@modelcontextprotocol/server-memory`       | ❌             | ⭐⭐   |
| 数据库 | sqlite       | `@modelcontextprotocol/server-sqlite`       | ❌             | ⭐⭐⭐  |
| 数据库 | postgres     | `@modelcontextprotocol/server-postgres`     | ❌（需连接串） | ⭐⭐   |
| 开发   | github       | `@modelcontextprotocol/server-github`       | ✅             | ⭐⭐⭐  |
| 开发   | git          | `@modelcontextprotocol/server-git`          | ❌             | ⭐⭐   |
| 搜索   | brave-search | `@modelcontextprotocol/server-brave-search` | ✅             | ⭐⭐⭐  |
| 搜索   | fetch        | `@modelcontextprotocol/server-fetch`        | ❌             | ⭐⭐   |
| 知识   | context7     | `@upstash/context7-mcp`                     | ❌             | ⭐⭐⭐  |
| 自动化 | puppeteer    | `@modelcontextprotocol/server-puppeteer`    | ❌             | ⭐⭐   |

**典型配置示例（Filesystem + GitHub）：**

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "."],
      "env": {}
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_TOKEN": "${GITHUB_TOKEN}" }
    }
  }
}
```

启动 `claude` 时看到 `✓ filesystem` `✓ github` 即配置成功，C盘目录下 用户名下的 .claude.json文件。

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/BSe7IE58RE9Spu00.png)

![image.png](https://pic.code-nav.cn/post_picture/1738833787455823874/uniP4tDC7ddbC0W9.webp)

### 2.4 三大作用域

| 作用域  | 存储位置                     | 优先级 | 适用场景                 |
| ------- | ---------------------------- | ------ | ------------------------ |
| Local   | `~/.claude.json`（项目条目） | 最高   | 含 API Key，绝不提交 Git |
| Project | 项目根 `.mcp.json`           | 中     | 团队共享，版本控制       |
| User    | `~/.claude.json`（全局）     | 最低   | 个人通用工具，跨项目可用 |

> **选择原则**：含密钥 → Local；团队必需 → Project；个人常用 → User。

### 2.5 在 Commands 中调用 MCP

第三章的 `allowed-tools` 直接支持 MCP 工具，格式：`mcp__服务器名__工具名`

```markdown
---
allowed-tools:
  - mcp__github__create_issue
  - mcp__filesystem__read_file
  - mcp__brave-search__brave_web_search
---
```

这样 Commands 就能直接驱动 GitHub、文件系统、搜索等外部服务，形成完整自动化工作流。

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/1RhJSJcXnIKJ6KJV.webp)

### 2.6 故障排查

| 现象                    | 原因                   | 解决方法                                                 |
| ----------------------- | ---------------------- | -------------------------------------------------------- |
| 启动时看不到 MCP 服务器 | 配置文件路径或格式错误 | 确认 `.mcp.json` 在项目根目录，JSON 格式正确             |
| 服务器启动失败          | Node.js 版本过低       | 升级到 v18+                                              |
| `${VAR}` 环境变量未生效 | 变量未导出或终端未重启 | `echo $VAR` 验证，重启终端                               |
| 工具调用被拒            | `allowed-tools` 未声明 | 在 Commands frontmatter 加入工具名                       |
| npx 下载超时            | 网络问题               | `npm config set registry https://registry.npmmirror.com` |

------

## 3. Hooks 系统

### 3.1 Hooks 是什么

Hooks 是**事件驱动的自动化触发器**——Claude 执行特定操作时，自动运行你预设的 shell 脚本。

比如可以在ClaudeCode 写完代码后，自动执行某些命令的格式化，以便让最终的代码更加美观，更加符合我们的需求

| Hook 时机          | 触发事件                | 典型用途                                 |
| ------------------ | ----------------------- | ---------------------------------------- |
| `PreToolUse`       | Claude 调用工具**之前** | 安全拦截危险命令、参数校验               |
| `PostToolUse`      | Claude 调用工具**之后** | 自动 lint / 测试 / 格式化                |
| PostToolUseFailure | Claude 调用工具失败后   | 错误日志记录、重试机制触发、失败原因分析 |
| `Notification`     | Claude 发送通知时       | 桌面弹窗、音效提醒                       |
| `Stop`             | Claude 完成一轮回复后   | 自动保存、发送完成通知                   |

> 类比：MCP 是给 Claude 装插件，Hooks 是给 Claude 装"自动触发器"——它做完某件事就自动帮你跑一段脚本。

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/0ihOzv1ihV09RZE2.webp)

### 3.2 配置方式

Hooks 写在 `settings.json` 的 `hooks` 字段，支持两个位置：

| 位置   | 路径                      | 生效范围               |
| ------ | ------------------------- | ---------------------- |
| 项目级 | `.claude/settings.json`   | 仅当前项目，可提交 Git |
| 用户级 | `~/.claude/settings.json` | 所有项目               |

**配置格式：**

```json
{
  "hooks": {
    "事件名": [
      {
        "matcher": "工具名正则",
        "hooks": [
          {
            "type": "command",
            "command": "要执行的 shell 命令"
          }
        ]
      }
    ]
  }
}
```

**`matcher` 正则匹配规则详解**：

`matcher` 用于精确控制 Hook 触发的工具范围，支持正则表达式：

| 模式          | 含义              | 示例                               |
| ------------- | ----------------- | ---------------------------------- |
| 空字符串 `""` | 匹配所有工具      | 任何工具操作都触发                 |
| 精确匹配      | 工具名相同        | `Write` 仅匹配 Write 工具          |
| 竖线 `|`      | 逻辑 OR，多个工具 | `Write|Edit` 同时匹配两个工具      |
| `.`           | 匹配任意单字符    | `Wr.te` 匹配 Write                 |
| `^`           | 字符串开始        | `^Bash$` 精确匹配 Bash，避免误匹配 |
| `$`           | 字符串末尾        | `Tool$` 匹配以 Tool 结尾的工具     |

**常见 matcher 模式示例**：

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "",
        "hooks": [{"type": "command", "command": "echo '任何工具都会触发'"}]
      },
      {
        "matcher": "Write",
        "hooks": [{"type": "command", "command": "echo '仅 Write 工具触发'"}]
      },
      {
        "matcher": "^Bash$",
        "hooks": [{"type": "command", "command": "echo '精确匹配 Bash，避免 BashScript 误触发'"}]
      },
      {
        "matcher": "Write|Edit",
        "hooks": [{"type": "command", "command": "prettier --write $CLAUDE_FILE_PATHS"}]
      },
      {
        "matcher": "Read.*",
        "hooks": [{"type": "command", "command": "echo 'Read 开头的工具'"}]
      }
    ]
  }
}
```

**最佳实践**：

- 使用 `^精确匹配$` 避免正则范围过宽导致的意外触发
- 在 PreToolUse 中用严格正则防御危险命令
- PostToolUse 可用较宽松的正则（如 `Write|Edit`）

### 3.3 实战示例

**写完文件自动格式化（最常用）**提取路径 + 格式化文件

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | xargs prettier --write"
          }
        ]
      }
    ]
  }
}
```

### 3.4 可用环境变量

Hook 脚本执行时，Claude 会注入以下变量：

| 变量                  | 含义                         | 示例值                    |
| --------------------- | ---------------------------- | ------------------------- |
| `$CLAUDE_TOOL_NAME`   | 当前调用的工具名             | `Write`                   |
| `$CLAUDE_FILE_PATHS`  | 被操作的文件路径（空格分隔） | `src/app.ts src/utils.ts` |
| `$CLAUDE_PROJECT_DIR` | 项目根目录                   | `/Users/me/project`       |
| `$CLAUDE_TOOL_INPUT`  | 工具的完整输入（JSON）       | `{"command":"ls -la"}`    |

### 3.5 常用场景速查

| 场景                | 事件        | 工具 matcher | 脚本示意                                   |
| ------------------- | ----------- | ------------ | ------------------------------------------ |
| 保存后自动 prettier | PostToolUse | `Write|Edit` | `prettier --write $CLAUDE_FILE_PATHS`      |
| 保存后自动 ESLint   | PostToolUse | `Write|Edit` | `eslint --fix $CLAUDE_FILE_PATHS`          |
| 写完跑单元测试      | PostToolUse | `Write`      | `npm test -- --passWithNoTests`            |
| 记录所有 Bash 命令  | PreToolUse  | `Bash`       | `echo $CLAUDE_TOOL_INPUT >> audit.log`     |
| 完成后播放音效      | Stop        | （空）       | `afplay /System/Library/Sounds/Glass.aiff` |
| 完成后桌面通知      | Stop        | （空）       | `osascript -e 'display notification...'`   |

> **注意**：`PreToolUse` Hook 退出码为 `2` 时会**阻止**该工具调用，其余退出码不会阻断执行。

### 3.6 故障排查

| 现象               | 原因                              | 解决方法                                 |
| ------------------ | --------------------------------- | ---------------------------------------- |
| Hook 没有触发      | settings.json 路径或格式错误      | 确认文件位置，JSON 格式用在线工具验证    |
| 脚本报"命令未找到" | 脚本用了 shell 别名或 PATH 不完整 | 写完整路径，如 `/usr/local/bin/prettier` |
| PreToolUse 误拦截  | matcher 正则范围太宽              | 精确化正则，如 `^Bash$` 而非 `Bash`      |
| 文件路径变量为空   | 工具不涉及文件操作                | 改用 `$CLAUDE_TOOL_INPUT` 获取完整输入   |

------

## 4. Subagent 子代理体系

### 4.1 Subagent 是什么

学完 MCP 和 Hooks，你已经能扩展 Claude 的能力边界——让它能调用外部服务、自动运行脚本。

但还有个更深的问题——**一个 Claude 怎么同时精通 100+ 个专业领域？**

**Subagent（子代理）\**就是答案：Claude Code 通过 Task 工具启动的\**专业化 AI 代理**，每个都是该领域的专家。

| 工具         | 解决什么问题               | 类比                       |
| ------------ | -------------------------- | -------------------------- |
| MCP          | 让 Claude 调用外部服务     | 给 Claude 装"插件"         |
| Hooks        | 让 Claude 自动运行脚本     | 给 Claude 设"自动触发器"   |
| **Subagent** | **让 Claude 调动专家团队** | **给 Claude 配"顾问团队"** |

#### Subagent 的核心优势

**并行协作**：同时启动多个专家代理，处理不同任务，效率翻倍。

```gauss
单个 Claude 顺序处理：
  代码审查 → 性能优化 → 安全审计 → 文档生成（耗时）

多个 Subagent 并行处理：
  code-reviewer  ─────┐
  performance-pro ────┼──→ 同时并行，结果聚合（快速）
  security-auditor ───┤
  doc-writer  ────────┘
```

**领域专业化**：每个 Subagent 都是特定领域的深度专家，质量远高于通用 Claude。

**按需扩展**：100+ 专家代理库，你只需说一句话，Claude 自动调用最合适的专家。

> **⚠️ 重要提醒**：使用多 Agent 并行调用的 token 消耗量巨大。每启动一个子代理都会消耗独立的上下文窗口。**建议按需调用，不要一次性启动太多代理。**

------

### 4.2 快速安装

#### 方法一：交互式脚本安装（推荐）

```bash
claude plugin marketplace add VoltAgent/awesome-claude-code-subagents
claude plugin install <plugin-name>
```

或者/plugin Installed界面自行安装

#### 方法二：手动安装（完全控制）

1. **确定存放路径**：
   - 全局可用：`~/.claude/agents/`
   - 项目专用：`.claude/agents/`（项目根目录）
2. **复制文件**：从仓库的 `categories/` 文件夹中找到你需要的 `.md` 代理定义文件，复制到上述路径即可。

**验证安装**：

```bash
# 查看已启用的子代理
claude /agents
```

### 故障排查与相关截图：

如果是网络问题需要检查自己的代理软件（🪜）

可能安装过程需要代理软件，看自己的个人配置（自己的代理接口）或者手动安装

```elixir
$env:HTTP_PROXY = "http://127.0.0.1:7897"
$env:HTTPS_PROXY = "http://127.0.0.1:7897"
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/gH8BmqDE2vlvmzXQ.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/DMNdlRCd7MMcs0qJ.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/xVV6A1k8rUy8W3Nv.webp)

------

### 4.3 /agents 交互式创建（从零搭建）

除了安装现成的代理库，你还可以用 `/agents` 命令**从零创建自己的 Subagent**——整个过程全程交互式引导，不需要手写任何配置文件。

#### 第一步：输入 `/agents`

在 Claude Code 对话中输入 `/agents`，你会看到当前已有的代理列表，底部有 **Create new agent** 选项：

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/eMqkDnJpuWVCfiRx.png)

#### 第二步：选择存放位置

| 选项                           | 说明           | 适合场景             |
| ------------------------------ | -------------- | -------------------- |
| `Project (.claude/agents/)`    | 仅当前项目可用 | 项目专用代理         |
| `Personal (~/.claude/agents/)` | 全局可用       | 通用代理，跨项目复用 |

> ![image.png](https://pic.code-nav.cn/post_picture/1738833787455823874/JRvLVkSd8sFuTjcl.webp)

#### 第三步：选择创建方式

| 方式                             | 说明                                    | 适合               |
| -------------------------------- | --------------------------------------- | ------------------ |
| **Generate with Claude（推荐）** | 你只需描述需求，Claude 自动生成完整配置 | 新手首选           |
| Manual configuration             | 手动填写每个字段                        | 需要精确控制的场景 |

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/YXWYjSKLyb0FXOVc.png)

#### 第四步：描述代理职责

用自然语言描述这个代理应该做什么、什么时候被调用。**写得越详细，生成效果越好：**

```1c
这是一个用于代码审核的 SubAgent。在用户要求"代码审核"的时候调用它。
```

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/6OJCCWUetBmrBz3I.webp)

#### 第五步：等待 Claude 生成

Claude 会根据你的描述自动生成代理的名称、系统提示词、工具选择等配置：

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/WuNHMYgszTZ8aY3b.png)

#### 第六步：选择工具权限

选择这个代理可以使用哪些工具。根据代理职责按需勾选：

| 工具类别        | 包含工具            | 说明               |
| --------------- | ------------------- | ------------------ |
| Read-only tools | Glob、Grep、Read 等 | 只读，安全无副作用 |
| Edit tools      | Edit、Write 等      | 可修改文件         |
| Execution tools | Bash 等             | 可执行命令         |
| MCP tools       | 已配置的 MCP 服务   | 调用外部服务       |

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/dD6t3ZKZP44nEuxx.webp)

#### 第七步：选择模型

| 模型                | 特点                     | 建议场景            |
| ------------------- | ------------------------ | ------------------- |
| **Sonnet**          | 性能均衡，速度与质量兼顾 | **日常代理首选**    |
| Opus                | 最强推理能力，成本最高   | 复杂架构 / 深度分析 |
| Haiku               | 速度快、成本低           | 简单任务 / 批量处理 |
| Inherit from parent | 继承主会话模型           | 跟随当前设置        |

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/IqzBGsyexDXgaUGo.webp)

#### 第八步：选择颜色标识

给代理设置一个背景色，方便在会话中一眼识别它的输出（比如代码审核用绿色、安全审计用红色）。

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/a0w7FIrrSfOXPNpb.webp)

#### 第九步：配置记忆

| 选项                               | 说明                                  | 建议             |
| ---------------------------------- | ------------------------------------- | ---------------- |
| **Enable (.claude/agent-memory/)** | 项目级记忆，代理会记住历史上下文      | **推荐**         |
| None                               | 无持久记忆                            | 一次性任务       |
| User scope                         | 全局记忆（`~/.claude/agent-memory/`） | 跨项目通用代理   |
| Local scope                        | 本地记忆，不提交 Git                  | 含敏感信息的场景 |

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/K4Vdtrk0ttsyIvJo.webp)

#### 第十步：确认保存

最终会展示代理的完整配置，确认无误后按 `s` 或 `Enter` 保存：

```gradle
Name:        code-reviewer
Location:    .claude/agents/code-reviewer.md
Tools:       Glob, Grep, Read, WebFetch, WebSearch
Model:       Sonnet
Memory:      Project (.claude/agent-memory/)

Description: Use this agent when the user explicitly requests a
             '代码审核' (code review), '审查代码', '检查代码'...

System prompt:
你是一位资深代码审核专家，拥有超过15年的软件工程经验，
精通多种编程语言和架构模式...
```

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/BYHgvgLiHx4siiIf.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/69SOe1Aiohj4OsLW.webp)

#### 实战调用

保存完成后，直接在对话里说 **"给我做下代码审核"**——Claude 会自动识别并调用刚刚创建的 `code-reviewer` 代理。

你会看到**绿色标识**，表示 Subagent 正在独立执行审核任务：

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/qtPAa5lxgFjd6Toj.webp)

审核完成后，代理会返回完整的审核报告，收工：

> ![img](https://pic.code-nav.cn/post_picture/1738833787455823874/FMN5AMyzTzV5I4NZ.webp)

> **凯神提醒**：`/agents` 交互式创建是目前最推荐的方式——不需要手写 `.md` 文件，Claude 帮你自动生成完整配置（名称、描述、系统提示词、工具权限全都有），新手 2 分钟就能搞定一个专属代理。

------

### 4.4 代理目录总览

VoltAgent 提供的 10 大类专家代理（100+ 代理），按需安装：

#### 1️⃣ 核心开发 (Core Development)

api-designer / backend-developer / electron-pro / frontend-developer / fullstack-developer / graphql-architect / microservices-architect / mobile-developer / ui-designer / websocket-engineer / wordpress-master

#### 2️⃣ 语言专家 (Language Specialists)

typescript-pro / [Python](https://www.mianshiya.com/bank/1810643768400019458)-pro / rust-engineer / golang-pro / [Java](https://www.mianshiya.com/bank/1860871861809897474)-architect / [JavaScript](https://www.mianshiya.com/bank/1810644471159848962)-pro / [React](https://www.mianshiya.com/bank/1817900465338241026)-expert / [Vue](https://www.mianshiya.com/bank/1817900864917000193)-expert / angular-architect / nextjs-developer / swift-expert / kotlin-expert / cpp-pro / csharp-developer / php-pro / sql-pro / django-developer / laravel-expert / rails-expert / spring-boot-engineer / flutter-expert / elixir-expert / dotnet-core-expert / powershell-pro

#### 3️⃣ 基础设施 (Infrastructure)

cloud-architect / devops-engineer / kubernetes-expert / terraform-engineer / database-admin / sre / deployment-engineer / azure-infra-engineer / network-engineer / platform-engineer / security-engineer / incident-responder / windows-infra-admin

#### 4️⃣ 质量与安全 (Quality & Security)

code-reviewer / security-auditor / qa-automation-engineer / performance-engineer / debugging-expert / error-detective / penetration-tester / architecture-reviewer / accessibility-tester / chaos-engineer / compliance-auditor / testing-automation-expert

#### 5️⃣ 数据与人工智能 (Data & AI)

ai-engineer / llm-architect / ml-engineer / data-engineer / data-scientist / data-analyst / database-optimizer / postgres-pro / mlops-engineer / nlp-engineer / prompt-engineer

#### 6️⃣ 开发者体验 (Developer Experience)

refactoring-expert / documentation-engineer / git-workflow-manager / legacy-code-modernizer / mcp-developer / build-engineer / cli-developer / dependency-manager / dx-optimizer / tooling-engineer

#### 7️⃣ 专业领域 (Specialized Domains)

blockchain-developer / game-developer / fintech-engineer / iot-engineer / embedded-systems-engineer / api-documenter / seo-specialist / mobile-app-developer / m365-admin

#### 8️⃣ 业务与产品 (Business & Product)

product-manager / business-analyst / project-manager / scrum-master / technical-writer / ux-researcher / customer-success-manager / sales-engineer / legal-advisor / content-marketing-specialist

#### 9️⃣ 元数据与编排 (Meta & Orchestration)

multi-agent-coordinator / workflow-orchestrator / agent-organizer / agent-installer / context-manager / task-dispatcher / error-coordinator / performance-monitor / knowledge-synthesizer / it-ops-orchestrator

**推荐新手起点**：

- `code-reviewer`（代码审查）
- `debugging-expert`（调试）
- `refactoring-expert`（重构）
- `documentation-engineer`（文档）

------

### 4.5 并行调用多个专家

#### 自动识别调用

当你的描述符合某个子代理的专业领域时，Claude 会**自动调用**对应的专家：

```prolog
你：这段代码有性能问题
Claude：[自动识别] 调用 performance-engineer 代理...
        基于性能优化的最佳实践，我来分析瓶颈...

你：帮我检查代码质量
Claude：[自动识别] 调用 code-reviewer 代理...
        我注意到以下代码质量问题...
```

#### 显式调用多个专家

对于复杂任务，**显式并行调用**多个专家：

```asciidoc
并行调用各个专家查看/解决 XXXX 问题

需要：
- code-reviewer 检查代码质量
- performance-engineer 分析性能
- security-auditor 审计安全漏洞
```

Claude 会同时启动 3 个子代理，返回综合报告。

#### 常见场景示例

| 场景             | 调用代理                                              | 效果             |
| ---------------- | ----------------------------------------------------- | ---------------- |
| **代码审查**     | code-reviewer                                         | 快速找出质量问题 |
| **性能优化**     | performance-engineer + database-optimizer             | 全面分析瓶颈     |
| **安全审计**     | security-auditor + penetration-tester                 | 深度安全检查     |
| **新项目启动**   | architecture-reviewer + project-manager + tech-writer | 快速生成架构文档 |
| **重构遗留代码** | legacy-code-modernizer + refactoring-expert           | 系统现代化       |
| **API 设计**     | api-designer + api-documenter                         | 完整的设计方案   |

------

### 4.6 故障排查

| 现象                     | 原因                            | 解决方法                                                |
| ------------------------ | ------------------------------- | ------------------------------------------------------- |
| `/agents` 看不到任何代理 | 安装路径错误或仓库未克隆        | 确认代理文件在 `~/.claude/agents/` 或 `.claude/agents/` |
| 代理安装成功但不被调用   | Subagent 定义文件格式错误       | 检查 `.md` 文件的 frontmatter 格式                      |
| 并行调用代理导致超时     | 启动的代理太多，超过 token 限制 | 减少并行代理数量，改为分批调用                          |
| 代理返回结果不符合预期   | 代理描述匹配度不高              | 在调用时更明确地说明需求，或显式指定代理                |
| Token 消耗过多           | 每个子代理都有独立上下文        | 按需调用，避免一次性启动太多代理                        |

------

## 5. 总结

本章你已掌握：

1. **MCP 本质**：AI 连接外部工具的 USB 标准，`.mcp.json` 配置，`npx` 启动
2. **常用服务器**：filesystem / github / sqlite / context7 等 10 个主流 Server 速查
3. **三大作用域**：Local（私密）> Project（团队）> User（全局），按需选择
4. **Commands 联动**：`mcp__服务器名__工具名` 在 Commands 中直接调用 MCP
5. **Hooks 本质**：事件驱动的 shell 脚本，PreToolUse / PostToolUse / Stop 三大时机
6. **Hooks 实战**：自动格式化、安全日志、完成通知，一次配置永久生效
7. **Subagent 本质**：Claude 调动的专家团队，100+ 代理库，按需并行协作
8. **/agents 创建**：交互式引导从零搭建专属代理，2 分钟完成，不需手写配置
9. **Subagent 实战**：快速安装、自动识别、显式并行调用，提升开发效率 10 倍



# 第五章：Skills定制——给Claude装上专属能力包

## 1. 前言

学完 Commands，你已经能把重复提示词压缩成一个命令。

但有个更深的问题——**Commands 是一次性触发，没有记忆，不能积累知识**。每次换个项目、换个场景，还得从零教 Claude。

**Skills 就是突破这个边界的答案：**

| 对比     | Commands             | Skills              |
| -------- | -------------------- | ------------------- |
| 定位     | 触发器（按钮）       | 能力包（APP）       |
| 知识容量 | 几百到几千字         | 可达数万字          |
| 触发方式 | 必须显式输入 `/命令` | 自动识别 + 显式调用 |
| 脚本集成 | 有限                 | 支持 Python/JS 脚本 |
| 可维护性 | 简单直接             | 模块化分层          |

> 类比：Commands 是快捷键，Skills 是手机里的 APP——装上之后，Claude 瞬间变成该领域专家。

------

## 2. Skills 核心概念

### 2.1 Skills 是什么

Skills 是 Claude Code 的**"能力 APP"**——把特定领域的知识、规则、工具打包成可复用的模块。

**没有 Skills 的困境**：

```jboss-cli
你：帮我写一篇公众号文章
Claude：好的，请问什么风格？字数多少？有什么特殊要求？

...下次对话...

你：再帮我写一篇
Claude：好的，请问什么风格？（又从零开始）
```

**有了 Skills 之后**：

```prolog
你：帮我写一篇公众号文章
Claude：[自动加载公众号写作 Skill，读取风格规范、爆款公式]
       好的！基于你的写作规范，我来帮你...
```

Skills 的核心价值：

| 场景       | 效果                         |
| ---------- | ---------------------------- |
| 领域专业化 | 预置大量领域知识，即用即专业 |
| 团队协作   | 一次配置，全员共享标准       |
| 知识积累   | 集中管理，版本可控           |
| 质量一致   | 标准化流程，输出稳定         |

### 2.2 Skills vs Commands

**一句话区分**：Commands 是"入口"，Skills 是"能力"，两者通常配合使用。

| 对比维度 | Commands（斜杠命令） | Skills（能力包） |
| -------- | -------------------- | ---------------- |
| 文件结构 | 单个 `.md` 文件      | 多文件目录       |
| 触发方式 | 必须输入 `/命令名`   | 关键词自动识别   |
| 状态管理 | 无状态               | 可维护配置和状态 |
| 工具集成 | 写在 `.md` 里        | 可调用外部脚本   |
| 适用场景 | 单一任务             | 复杂工作流       |

**协作关系**：

```applescript
用户输入
   │
   ├──→ Commands（触发层）：/write 公众号文章
   │          │
   │          ▼
   └──→ Skills（能力层）：自动加载写作规范、调用脚本
```

最佳实践：

- 简单任务 → 直接用 Command
- 复杂工作流 → Command 作入口 + Skill 提供能力

### 2.3 渐进式披露原理

Skills 采用**按需加载**设计，核心思想：只在用户需要时才展示复杂功能，避免内存浪费。

| 层级           | 内容                                        | 何时加载     | 内存占用         |
| -------------- | ------------------------------------------- | ------------ | ---------------- |
| 第一层：元数据 | YAML Frontmatter 的 `name` 和 `description` | 始终常驻     | 极小（<100字节） |
| 第二层：指令   | SKILL.md 的 Markdown Body                   | Skill 激活时 | 按需加载         |
| 第三层：资源   | `scripts/`、`templates/`、`config/`         | 调用时才读取 | 用完即释放       |

> 这就是为什么有几十个 Skills 也不会拖慢 Claude——元数据极小，详细内容按需加载。

------

## 3. 准备工作

### 3.1 账号要求

| 账户类型          | Skills 支持 | 说明             |
| ----------------- | ----------- | ---------------- |
| Claude Pro        | ✅ 支持      | 推荐，功能最完整 |
| Claude Teams      | ✅ 支持      | 企业用户推荐     |
| Claude Enterprise | ✅ 支持      | 企业级，功能最强 |
| 免费版            | ❌ 不支持    | 暂无此功能       |
| 中转站 (API)      | ✅ 支持      | 国内用户推荐     |

> **中转站用户**：通过 API 密钥使用 Claude Code 的中转站用户也支持 Skills。推荐使用 AnyRouter、gemai 等稳定的中转站。

### 3.2 环境要求

**必需工具**：

- **Claude Desktop**（网页版或桌面版均可）

  - 下载地址：https://www.anthropic.com/claude-desktop
  - 最低版本：2.0+（推荐最新版）

- **Claude Code CLI**（用于本地开发）

  ```bash
  # 验证安装
  claude --version
  
  # 如未安装，按第一章步骤重新安装
  ```

- **Python 3.8+**（如需使用脚本）

  ```bash
  python --version
  ```

------

## 4. 官方 Skills 速查

Anthropic 官方提供的核心技能包：

> **官方资源**：
>
> - [Anthropic 官方 Claude Plugins 仓库](https://github.com/anthropics/claude-plugins-official)
> - [SkillsMP - Skills 市场](https://skillsmp.com/zh)
> - [ComposioHQ - Awesome Claude Skills 合集](https://github.com/ComposioHQ/awesome-claude-skills)
> - [sickn33 - Antigravity Awesome Skills](https://github.com/sickn33/antigravity-awesome-skills)

| 技能包                  | 功能         | 核心能力                                    | 适用场景                         |
| ----------------------- | ------------ | ------------------------------------------- | -------------------------------- |
| **document-skills**     | 文档处理     | 解析 Excel/Word/PPT/PDF，提取数据，生成报告 | 数据分析、报告自动生成、内容提取 |
| **example-skills**      | 技能开发示例 | Skill 创建模板、MCP 构建示例                | 学习如何开发自定义 Skill         |
| **planning-with-files** | 文件规划     | 项目文档整理、任务分解、甘特图生成          | 项目管理、任务规划               |
| **frontend-design**     | 前端设计     | UI/UX 设计指导、代码生成、组件库推荐        | 前端开发、设计稿转代码           |

**推荐使用顺序**：

1. 先装 `example-skills` 学习 Skill 开发
2. 根据需求装 `document-skills`（文档处理最常用）
3. 按场景选装其他技能包

------

## 5. 安装 Skills

### 5.1 官方/第三方 Skills 安装

**方式一：网页版/桌面版安装（最简单）**

```jboss-cli
1. 打开 Claude 官网或桌面版
2. 进入"设置" → "功能" → "Skills"
3. 找到要启用的官方技能，点击开关启用
4. 或点击"上传技能"，选择 .skill 文件上传第三方技能
```

**方式二：Claude Code CLI 安装（推荐开发者）**

Step 1：添加官方技能市场 或者通过skills查找网站进行搜索自己需要的 自行安装

[Agent Skills 市场 - Claude、Codex 和 ChatGPT Skills | SkillsMP](https://skillsmp.com/zh)

```bash
/plugin marketplace add anthropics/skills
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/CCTjR2hQr3w5Ix7g.png)

或者通过原空间安装

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/Aoz0vyScp0vE6EXw.webp)

Step 2：安装官方技能包（可选多个）

```bash
# 文档处理技能（Excel、Word、PPT、PDF 等）
/plugin install document-skills@anthropic-agent-skills

# 示例技能包（学习自定义 Skill 开发的好素材）
/plugin install example-skills@anthropic-agent-skills
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/NyfMrQxzKof6LCMy.webp)

| 选项                                                         | 通俗解释                                                     | 适用场景                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------------------------------- |
| Install for you (user scope)                                 | **用户级安装**：插件仅对你当前的账号生效，不管你打开哪个仓库 / 项目，都能使用这个插件 | 个人使用、想在所有项目中用这个示例插件学习               |
| Install for all collaborators on this repository (project scope) | **项目级安装**：插件仅对当前这个代码仓库生效，且仓库的所有协作者都能看到 / 使用这个插件 | 团队协作、仅需要在特定项目中测试示例技能                 |
| Install for you, in this repo only (local scope)             | **本地仓库级安装**：插件仅对你自己生效，且仅在当前这个仓库中可用 | 只想在某个项目中测试，不想影响其他项目，也不想让团队看到 |
| Back to plugin list                                          | 放弃安装，返回插件列表                                       | 暂时不想装这个插件                                       |

或者在安装了元空间的 仓库下 /plugin Discover 选择自己需要安装的插件skills

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/h8EQeHBCK6vbPfpg.webp)

Step 3：重启 Claude Code 完成激活

```bash
# 退出并重新启动
claude
```

**方式三：手动安装（进阶用户）**

将 Skill 文件夹放置在以下任一位置，Claude 会自动识别：

官方安装的会在plugins/marketplaces/官方/skills 下

```awk
# 个人级（所有项目可用）
~/.claude/skills/your-skill-name/

# 项目级（仅当前项目可用）
/path/to/project/.claude/skills/your-skill-name/
```

### 5.2 手动安装skills 实战

```nix
# 创建插件目录（建议放在用户目录下，方便查找）
mkdir -p ~/claude-plugins/connect-apps-plugin
# 进入该目录
cd ~/claude-plugins/connect-apps-plugin
# 克隆插件仓库（如果没有git，先安装：brew install git / apt install git）
git clone https://github.com/ComposioHQ/awesome-claude-skills.git .
# cmd 命令拷贝到 .claude\skills\ 目录下
xcopy "%USERPROFILE%\claude-plugins\connect-apps-plugin" "%USERPROFILE%\.claude\skills\" /E /H /Y
# 检查是否安装
claude
/skills
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/7aEXQgx0zhhpJB4F.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/Jm8puuOAU2cWEDUo.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/n2BfakLyKSFxr8YB.webp)

**powershell**

```nix
# 1. 确保目标目录存在（不存在则创建）
New-Item -Path "~\.claude\skills" -ItemType Directory -Force

# 2. 复制源目录下的所有文件/子文件夹到目标目录（关键：末尾加 \*）
Copy-Item -Path "~\claude-plugins\connect-apps-plugin\*" -Destination "~\.claude\skills" -Recurse -Force
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/4RA5UU8ukMjolu9h.webp)

### 5.3 自定义 Skill 开发（本地安装）

一旦你创建了自定义 Skill，可以通过以下方式安装：

**放入标准目录**

```bash
# macOS/Linux
mkdir -p ~/.claude/skills/my-skill
cp -r ./my-skill/* ~/.claude/skills/my-skill/

# Windows PowerShell
New-Item -ItemType Directory -Path "$env:USERPROFILE\.claude\skills\my-skill" -Force
Copy-Item -Recurse ".\my-skill\*" "$env:USERPROFILE\.claude\skills\my-skill\" -Force
```

------

## 6. 创建第一个自定义 Skill

### 6.1 目录结构

每个 Skill 是 `.claude/skills/` 下的独立目录：

```nix
.claude/skills/[skill-name]/
├── SKILL.md          # [必需] 核心定义文件（YAML元数据 + Markdown指令）
├── scripts/          # [可选] 工具脚本（Python/JS）
├── templates/        # [可选] 输出模板
├── config/           # [可选] 配置文件
└── data/             # [可选] 静态数据
```

| 文件/目录    | 是否必需 | 用途                    |
| ------------ | -------- | ----------------------- |
| `SKILL.md`   | ✅ 必需   | Skill 的身份证 + 说明书 |
| `scripts/`   | 可选     | 可执行的自动化脚本      |
| `templates/` | 可选     | 输出格式模板            |
| `config/`    | 可选     | 运行时配置参数          |

> **命名规范**：目录名只能用小写字母、数字、连字符（`-`），不能有空格或下划线。

### 6.2 SKILL.md 配置详解

`SKILL.md` 由两部分组成：**YAML Frontmatter**（机器读）+ **Markdown Body**（AI 读）。

**YAML Frontmatter 字段表**（必填字段只有 2 个）：

| 字段          | 类型   | 是否必填 | 说明                                      |
| ------------- | ------ | -------- | ----------------------------------------- |
| `name`        | string | ✅        | Skill 名称，必须与目录名一致              |
| `description` | string | ✅        | 触发场景描述，Claude 用此判断是否自动激活 |
| `version`     | string | 可选     | 版本号（如 1.0.0）                        |
| `author`      | string | 可选     | 作者名称                                  |

**最小配置示例**：

```markdown
---
name: code-commenter
description: 当用户要求"添加注释"、"代码注释"或"注释代码"时激活
---

# 代码注释生成器

## 角色定义
你是一位代码审查专家，擅长编写清晰的中文注释。

## 注释原则
- 解释"为什么"而不是"是什么"
- 使用简洁的中文
- 专业术语保持英文（如 API、JWT）
```

**description 写法对比**：

| 写法                                       | 效果                     |
| ------------------------------------------ | ------------------------ |
| ✅ `当用户要求"添加注释"或"代码注释"时激活` | 明确触发词，自动识别准确 |
| ❌ `代码注释工具`                           | 太模糊，自动激活不准     |

**Markdown Body 推荐结构**：

```markdown
# Skill 名称

## 一、角色定义
[AI 扮演的角色和专业背景]

## 二、核心能力
[列出 3-5 个核心能力]

## 三、工作流程
### 步骤1：[名称]
[详细说明]

## 四、规则约束
[必须遵守的规则]

## 五、输出格式
[输出结构定义]
```

### 6.3 实战：5分钟创建代码注释 Skill

**Step 1：建目录**

```bash
# macOS / Linux
mkdir -p .claude/skills/code-commenter

# Windows PowerShell
New-Item -ItemType Directory -Path ".claude\skills\code-commenter" -Force
```

**Step 2：创建 SKILL.md**

创建文件 `.claude/skills/code-commenter/SKILL.md`：

~~~markdown
---
name: code-commenter
description: 当用户要求"添加注释"、"给代码加注释"或"注释代码"时，自动为代码添加清晰的中文注释
---

# 代码注释生成器

## 角色定义
你是一位经验丰富的代码审查专家，擅长编写清晰、准确、有价值的代码注释。

## 何时激活
当用户说以下内容时激活本 Skill：
- "帮我添加注释"
- "给这段代码加注释"
- "comment this code"

## 注释原则

### 1. 解释"为什么"而不是"是什么"
```python
# ❌ 差：循环遍历列表
for item in items:
    process(item)

# ✅ 好：过滤已过期订单，避免重复发货
for item in items:
    process(item)
~~~

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/q8mrHfzg54OUM29I.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/ZbFCZFuOBcVGpqra.png)

### 2. 注释格式规范

- **函数/方法**：说明功能、参数、返回值
- **复杂逻辑**：解释业务背景
- **魔法数字**：说明数值含义（如 86400 = 24小时）

### 3. 语言要求

- 使用简洁中文
- 专业术语保持英文（如 API、JWT、JSON）

### 6.4 测试 Skill

**Step 1：启动 Claude Code**

```bash
claude
```

**Step 2：测试触发**

在对话中输入：

```kotlin
帮我给这段代码添加注释

def calculate_discount(price, user_level):
    if user_level == "vip":
        return price * 0.8
    elif user_level == "svip":
        return price * 0.7
    else:
        return price
```

**Step 3：验证预期响应**

Claude 应该自动激活 `code-commenter` Skill，并返回带详细中文注释的代码：

```python
def calculate_discount(price, user_level):
    """
    根据用户等级计算折扣后的价格

    Args:
        price: 原始价格
        user_level: 用户等级（vip/svip/普通）

    Returns:
        折扣后的价格
    """
    # VIP用户享受8折优惠
    if user_level == "vip":
        return price * 0.8
    # SVIP用户享受7折优惠
    elif user_level == "svip":
        return price * 0.7
    # 普通用户无折扣
    else:
        return price
```

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/U5HDYntg97c5rHEy.webp)

**🎯 Hot Reloading 体验**

修改 `SKILL.md` 后，**无需重启 Claude Code**，下次对话时修改会自动生效！

尝试：

1. 编辑 `.claude/skills/code-commenter/SKILL.md`，修改注释原则
2. 回到 Claude Code，继续对话（不用重启）
3. 观察新的规则是否立即应用

------

## 7. Skills 使用方法

### 7.1 自动激活 vs 手动触发

**自动激活（推荐）**：

Claude 自动识别用户输入中的触发关键词，激活对应的 Skill：

```armasm
用户：帮我给这段代码添加注释
Claude：[自动识别"添加注释" → 激活 code-commenter Skill]
```

关键是写好 `description` 字段，列举明确的触发词：

```yaml
---
name: code-commenter
description: 当用户要求"添加注释"、"给代码加注释"或"代码注释"时激活
---
```

**手动触发**：

用户显式在开始时声明使用某个 Skill：

```ruby
我需要用 code-commenter Skill，帮我给这段代码添加注释
def calculate():
    ...
```

### 7.2 Skill 交互模式

| 模式         | 使用场景             | 示例                                       |
| ------------ | -------------------- | ------------------------------------------ |
| **单词触发** | 一句话激活，继续对话 | "帮我添加注释" → 输入代码 → 自动应用       |
| **链式调用** | 多个 Skill 协作      | 先用 title-generator → 再用 content-writer |
| **反复迭代** | 同一 Skill 多次使用  | 生成标题 → 用户反馈 → 再生成               |

### 7.3 与 Commands 的配合

**最佳实践**：Command 作为入口，Skill 提供能力

```gauss
命令层：/write 《标题》
   ↓
Skill 层：自动加载 title-generator 和 content-writer
   ↓
输出：完整文章
```

在 Commands 的 `.md` 中调用 Skill：

```markdown
# /write 命令

帮我写一篇关于「{topic}」的公众号文章。

> 使用 Skill：title-generator + gongzhonghao-writer
```

------

## 8. 进阶使用

### 8.1 提示词组织技巧

本节目的：掌握在 SKILL.md 中组织提示词的最佳实践。

> **2.10+ 重大变化**：所有提示词内容统一写在 SKILL.md 的 Markdown Body 中，无需单独的 `prompts/` 文件夹。

#### 8.1.1 提示词组织方式

推荐**按功能分章节**组织，保持清晰的层次：

```markdown
# [Skill名称]

## 一、角色定义
[AI扮演的角色]

## 二、核心能力
[3-5个核心能力列表]

## 三、工作流程
### 步骤1：...
### 步骤2：...

## 四、规则约束
[必须遵守的规则]

## 五、示例展示
[好/坏示例对比]

## 六、输出格式
[输出结构定义]
```

#### 8.1.2 章节命名规范

| 命名模式        | 示例                    | 说明       |
| --------------- | ----------------------- | ---------- |
| `## 一、xxx`    | `## 一、角色定义`       | 主要章节   |
| `## {功能}规范` | `## 标题生成规范`       | 功能说明   |
| `### {子功能}`  | `### 公式1：工具推荐型` | 子功能细节 |

**最佳实践**：保持 3 级以内的层次，使用清晰中文标题。

#### 8.1.3 提示词结构模板

```markdown
---
name: skill-name
description: 当用户[具体场景]时激活
version: 1.0.0
---

# Skill 名称

## 一、角色定义
你是一位[专业背景]的专家...

## 二、核心能力
1. [能力1]
2. [能力2]
3. [能力3]

## 三、工作流程
### 步骤1：[分析/准备]
### 步骤2：[执行]
### 步骤3：[验证]

## 四、规则约束
- 必须遵守的规则1
- 必须遵守的规则2

## 五、示例展示
✅ **好的示例**
❌ **差的示例**
```

#### 8.1.4 提示词版本管理

在 SKILL.md 开头记录版本历史：

```markdown
---
name: my-skill
version: 2.0.0
---

## 版本历史
### V2.0.0 (2025-01)
- 新增：XXX
- 优化：YYY

### V1.0.0 (2024-12)
- 初版发布
```

#### 8.1.5 提示词优化技巧

**1. 用代码块强调公式**

```markdown
### 标题公式
[品牌词] + [数字] + [推荐词]
```

**2. 用表格对比版本**

| 版本 | 改进点   |
| ---- | -------- |
| V1.0 | 基础功能 |
| V2.0 | 新增XXX  |

**3. 用强指令替代建议**

- ❌ "建议使用中文"
- ✅ "必须使用简洁中文"

### 8.2 Python 脚本集成

**什么时候需要脚本？**

| 任务类型   | Claude 原生 | 脚本增强      |
| ---------- | ----------- | ------------- |
| 文本分析   | 模糊判断    | 精确 NLP 分析 |
| 数字计算   | 可能出错    | 100% 准确     |
| 文件批处理 | 效率低      | 高效批量处理  |
| 复杂校验   | 难以一致    | 确定性校验    |

**标准脚本模板**（放入 `scripts/` 目录）：

```python
#!/usr/bin/env <a href="https://www.mianshiya.com/bank/1810643768400019458" class="keyword-highlight" target="_blank" rel="noopener noreferrer">Python</a>3
# -*- coding: utf-8 -*-
"""脚本功能简述"""
import sys
import json

def process(input_data: str) -> dict:
    """核心处理逻辑"""
    # 在这里实现具体功能
    return {
        "success": True,
        "data": {"result": input_data},
        "message": "处理成功"
    }

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print(json.dumps({"success": False, "message": "缺少参数"}))
        sys.exit(1)

    result = process(sys.argv[1])
    print(json.dumps(result, ensure_ascii=False, indent=2))
    sys.exit(0 if result["success"] else 1)
```

**在 SKILL.md 中调用脚本**：

```markdown
## 工具调用
- 质量检测：`python scripts/quality_detector.py "文章内容" --json`
- 标题生成：`python scripts/title_generator.py "主题关键词"`
```

**参数传递方式速查**：

| 方式       | 适用场景 | 示例                                 |
| ---------- | -------- | ------------------------------------ |
| 命令行参数 | 简单参数 | `python script.py "topic"`           |
| 标准输入   | 大量文本 | `echo "content" | python script.py`  |
| 文件传递   | 复杂数据 | `python script.py --input file.json` |

### 8.3 多步骤工作流

在 SKILL.md 的 Markdown Body 中用自然语言描述完整工作流：

```markdown
## 工作流程

### 步骤1：选题过滤
判断三个维度：时效性、爆款潜力、是否值得写
- 不值得写 → 直接给出建议，结束流程
- 值得写 → 继续下一步

### 步骤2：信息收集（按需）
如果主题需要最新数据：
- 使用 WebSearch 搜索"主题 最新资讯 2025"
- 整理关键数据和观点

### 步骤3：创作文章
应用写作风格规范，控制字数 1500-2000 字

### 步骤4：质量检测
调用 `scripts/quality_detector.py` 检测 AI 腔、自然度
- 检测通过 → 保存文章
- 检测失败 → 按建议修改后重新检测
```

> Commands 可作为工作流入口，Skill 提供底层能力：`/write 主题` → 触发 Command → Command 调用公众号写作 Skill。

------

## 9. 故障排查

| 现象                     | 原因                       | 解决方法                                                     |
| ------------------------ | -------------------------- | ------------------------------------------------------------ |
| Skill 未自动激活         | `description` 描述不清晰   | 在 description 中明确列出触发关键词，如"当用户提到"或"当用户要求" |
| AI 回复不符合规范        | Markdown Body 指令太模糊   | 用 `必须`、`禁止` 等强指令替代 `建议`，提高执行一致性        |
| 官方 Skill 安装失败      | 网络问题或账户权限不足     | 检查网络连接、确认是付费账户，尝试重启 Claude Code           |
| 脚本执行失败             | Python 路径或权限问题      | `python --version` 验证，macOS/Linux 加 `chmod +x` 执行权限  |
| YAML 解析报错            | 冒号后无空格或 `---` 缺失  | 检查格式：`name: skill-name`，注意冒号后有空格               |
| 文件路径问题             | 目录名与 `name` 字段不一致 | 确认目录名和 YAML 中的 `name` 字段完全一致                   |
| 中转站用户 Skills 不可用 | 中转站不支持 Skills 功能   | 更换支持 Skills 的中转站（如 AnyRouter、gemai），或使用官方账户 |

**YAML 格式快速验证**：

```bash
# 用 Python 验证 SKILL.md 的 YAML 部分
python3 -c "
import yaml
with open('.claude/skills/你的skill/SKILL.md', 'r', encoding='utf-8') as f:
    content = f.read()
# 提取 --- 包裹的 YAML 部分
parts = content.split('---')
yaml.safe_load(parts[1])
print('✅ YAML 格式正确')
"
```

# 第六章：Plugins全攻略——一键安装海量扩展，还能自己造轮子

## 1. 前言

学完 Skills，你已经能给 Claude 装上各种专属能力包了。

但你有没有想过一个问题——**辛辛苦苦写好的 Commands + Skills + Hooks 配置，换个项目又得重来一遍？想分享给团队成员？手动复制粘贴？**

**Plugin 就是解决这个问题的终极方案：**

| 痛点               | Plugin 怎么解决                    | 类比         |
| ------------------ | ---------------------------------- | ------------ |
| 配置不可移植       | 一个 Plugin 打包所有配置，一键安装 | 手机备份恢复 |
| 分享靠手动复制     | Marketplace 搜一下装一下           | App Store    |
| 更新全靠自己盯     | 自动更新，作者推了新版你自动获得   | APP 自动更新 |
| 找好用的工具费时间 | 社区 200+ Plugin 直接选            | 排行榜推荐   |

说白了：**Plugin = 可分享、可安装、可自动更新的 Commands + Skills + Hooks + MCP 打包体。**

------

## 2. Plugin 核心概念

### 2.1 Plugin 是什么

Plugin 是 Claude Code 的**扩展包**——把 Commands、Skills、Hooks、MCP 配置打包成一个可安装、可分享、可自动更新的整体。

**类比理解：**

| 手机                    | Claude Code        |
| ----------------------- | ------------------ |
| 操作系统（iOS/Android） | Claude Code 核心   |
| App Store               | Plugin Marketplace |
| 安装的 APP              | 已安装的 Plugins   |
| APP 自动更新            | Plugin 自动更新    |

**核心价值：**

| 价值     | 说明                                    |
| -------- | --------------------------------------- |
| 可复用   | 一次开发，多个项目使用                  |
| 可分享   | 通过 Marketplace 一键安装，不用手动复制 |
| 模块化   | 每个 Plugin 专注一个领域，互不干扰      |
| 社区驱动 | 200+ 社区 Plugin 开箱即用               |

### 2.2 Plugin vs Commands / Skills / MCP

很多人问："我已经有 Commands 和 Skills 了，为什么还要 Plugin？"

一张表说清楚：

| 维度     | Commands            | Skills            | MCP           | **Plugins**        |
| -------- | ------------------- | ----------------- | ------------- | ------------------ |
| 定义     | Markdown 提示词     | 专业 Agent 能力   | 外部服务集成  | **打包的扩展**     |
| 存放位置 | `.claude/commands/` | `.claude/skills/` | `.mcp.json`   | `.claude/plugins/` |
| 可分享性 | ❌ 手动复制          | ❌ 手动复制        | ⚠️ 需配置      | ✅ 一键安装         |
| 自动更新 | ❌ 手动更新          | ❌ 手动更新        | ⚠️ 部分支持    | ✅ 自动更新         |
| 包含内容 | 单个提示词          | 多个文件+配置     | 服务器配置    | **全部都能包含**   |
| 适用场景 | 简单重复任务        | 复杂专业任务      | 外部 API 调用 | **所有场景**       |

> **关键区别**：Plugin 是一个**"超集"**概念——`Plugin = Commands + Skills + Hooks + MCP 配置 + 文档`，打包成一个可以一键安装和分享的整体。

**何时用什么？决策指南：**

- **Commands**：项目内简单重复任务（如 `/format-code`）——够用就行，别上 Plugin
- **Skills**：项目内复杂专业任务（如代码注释生成）——能力需要积累和复用
- **MCP**：需要调用外部服务（如 GitHub API、数据库）——解决连接问题
- **Plugins**：✅ **想分享给团队或社区的任何功能**——打包分发的最佳选择

### 2.3 生态现状

**三大 Marketplace：**

| 平台                       | 地址                                                | 特点                  |
| -------------------------- | --------------------------------------------------- | --------------------- |
| Anthropic 官方 Marketplace | code.claude.com/plugins                             | 审核严格，质量保证    |
| Jeremy Longshore 社区合集  | github.com/jeremylongshore/claude-code-plugins-plus | 200+ Plugin，持续更新 |
| Composio Integration       | composio.dev                                        | 集成 2000+ 外部工具   |

**热门 Plugin 分类速查：**

| 分类     | 典型 Plugin        | 用途                       | 来源           | 热度  |
| -------- | ------------------ | -------------------------- | -------------- | ----- |
| 文档处理 | document-skills    | PDF/PPTX/XLSX 全套文档处理 | Anthropic 官方 | ⭐⭐⭐⭐⭐ |
| 示例学习 | example-skills     | 官方 Skill 开发示例        | Anthropic 官方 | ⭐⭐⭐   |
| 代码质量 | code-review-expert | 自动代码审查               | 社区           | ⭐⭐⭐⭐  |
| 项目管理 | task-master-ai     | 任务拆解和跟踪             | 社区           | ⭐⭐⭐⭐  |
| API 集成 | connect-apps       | Gmail/Slack/GitHub 联动    | 社区           | ⭐⭐⭐⭐⭐ |
| 数据分析 | data-viz-pro       | 数据可视化                 | 社区           | ⭐⭐⭐   |

> **说明**：`document-skills` 是 Anthropic 官方出品的文档处理套件（来自 `anthropics/skills` 源），安装后包含 `document-skills:pdf`、`document-skills:pptx`、`document-skills:xlsx` 等多个 Skill，一次安装全部可用。

------

## 3. 5 分钟安装第一个 Plugin

### 3.1 前置检查

```bash
# 1. 确认 Claude Code 版本（需 v2.1+）
claude --version

# 2. 确认在项目目录中
cd /path/to/your/project
```

> Plugin 功能于 2025 年 10 月 9 日随 Claude Code v2.1 发布。如果版本过低，先升级。

### 3.2 浏览 Marketplace

**方式一：对话内 `/plugin` 命令（最方便）**

在 Claude Code 对话中直接输入：

```bash
/plugin
```

会进入 Plugin 管理界面，切换到 `Marketplace` 标签页即可浏览所有可用 Plugin。

**方式二：CLI 命令**

```bash
# 添加社区 Marketplace 源（第一次用需要先添加）
claude plugin marketplace add anthropics/skills

# 查看已添加的 Marketplace 源
claude plugin marketplace list
```

添加成功后，就能从该源浏览和安装 Plugin 了。

![image.png](https://pic.code-nav.cn/post_picture/1738833787455823874/TCRVPlKTNAHEa3JN.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/ca0fDOBjTMEUt7pO.webp)

**实战：添加 Marketplace 源并安装 Plugin**

以添加 VoltAgent Subagent 代理库为例，完整流程：

```bash
# 1. 添加 Marketplace 源
claude plugin marketplace add VoltAgent/awesome-claude-code-subagents
# 2. 从该源安装你需要的 Plugin
claude plugin install <plugin-name>
```

或者在对话中输入 `/plugin`，切换到 `Installed` 界面自行浏览安装。

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/Mf04IaM5EfoHxHI0.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/uOS6EACM700JHJMs.webp)

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/NEGrXQ1K0EE2KE1a.webp)

> **网络问题？** 如果安装过程中遇到超时或下载失败，需要检查代理软件配置：
>
> ```powershell
> # Windows PowerShell（根据自己的代理端口修改）
> $env:HTTP_PROXY = "http://127.0.0.1:7897"
> $env:HTTPS_PROXY = "http://127.0.0.1:7897"
> # macOS / Linux
> export HTTP_PROXY="http://127.0.0.1:7897"
> export HTTPS_PROXY="http://127.0.0.1:7897"
> ```

**方式三：Web 浏览器**

直接访问官方 Marketplace 网页：`https://code.claude.com/plugins`

------

## 4. Plugin 管理全流程

在 Claude Code 对话中输入 `/plugin`，进入图形化管理界面。界面顶部有四个标签页，覆盖所有管理场景：

| 标签页           | 功能                          |
| ---------------- | ----------------------------- |
| **Discover**     | 浏览并安装 Plugin（默认打开） |
| **Installed**    | 查看和管理已安装的 Plugin     |
| **Marketplaces** | 管理 Plugin 源                |
| **Errors**       | 排查加载错误                  |

> **界面导航**：`↑↓` 上下移动，`空格` 快速安装/切换，`回车` 进入详情，`ESC` 返回上级

### 4.1 安装 Plugin（Discover 标签页）

打开 `/plugin`，默认进入 **Discover** 标签页，列出所有已添加 Marketplace 源中的可用 Plugin：

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/galctWb54V7eOUuH.webp)

**安装步骤：**

1. 用 `↑↓` 移动光标，选中想安装的 Plugin
2. 按**回车**查看详情（或直接按**空格**快速安装）
3. 在详情页选择**安装范围**，确认安装

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/UfAf3bnnI5SPnKHe.webp)

**安装范围说明：**

| 范围                                                         | 说明                           | 适用场景               |
| ------------------------------------------------------------ | ------------------------------ | ---------------------- |
| Install for you (user scope)                                 | 个人级：你的所有项目都可用     | 日常通用工具（推荐）   |
| Install for all collaborators on this repository (project scope) | 项目级：整个仓库的协作者共享   | 团队协作项目           |
| Install for you, in this repo only (local scope)             | 本地仓库级：仅自己在此项目可用 | 本地测试、不想影响他人 |

**三种安装来源：**

| 来源                       | 操作方式                                     |
| -------------------------- | -------------------------------------------- |
| Marketplace Plugin（推荐） | 在 Discover 标签页直接选中安装               |
| GitHub URL                 | 在 Discover 页顶部输入 GitHub 仓库地址       |
| 本地目录                   | 在 Discover 页顶部输入本地路径（开发测试用） |

> **找不到想装的 Plugin？** 先去 **Marketplaces** 标签页添加对应的源，再回 Discover 刷新列表。

### 4.2 管理已安装的 Plugin（Installed 标签页）

切换到 **Installed** 标签页，查看所有已启用的 Plugin：

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/jtEek0SPMBIfWbD4.webp)

列表中同时显示 Plugin 系统安装的扩展和 MCP 连接，每条显示名称、版本和状态。

**更新 / 禁用 / 卸载操作：**

选中某个 Plugin，按**回车**进入详情，可执行以下操作：

| 操作 | 效果                               |
| ---- | ---------------------------------- |
| 更新 | 升级到最新版本（有新版本时显示）   |
| 禁用 | 临时停用，保留文件，下次可重新启用 |
| 卸载 | 彻底删除 Plugin 及其所有文件       |

> **自动更新**：Claude Code 启动时会自动检查所有 Plugin 更新，无需手动触发。

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/Bs1Hpui9ZB1ukGdd.webp)

### 4.3 管理 Marketplace 源（Marketplaces 标签页）

切换到 **Marketplaces** 标签页，管理 Plugin 的来源：

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/1QeAPWFyIulNOW5q.webp) 界面列出所有已添加的 Marketplace 源，每个源显示可用 / 已安装的 Plugin 数量，以及最后更新时间。

**添加新 Marketplace 源：**

1. 在 Marketplaces 标签页选择"添加源"
2. 输入源地址（格式：`用户名/仓库名`）
3. 确认添加后，Discover 标签页自动同步新来源的 Plugin

![img](https://pic.code-nav.cn/post_picture/1738833787455823874/EHfHZVv68Oz2llWl.png)

**推荐 Marketplace 源：**

| 源地址                                     | 内容                                          | 推荐指数 |
| ------------------------------------------ | --------------------------------------------- | -------- |
| `anthropics/skills`                        | 官方 Skills 套件（含 document-skills 全家桶） | ⭐⭐⭐⭐⭐    |
| `anthropics/claude-plugins-official`       | Anthropic 官方 Plugin                         | ⭐⭐⭐⭐     |
| `VoltAgent/awesome-claude-code-subagents`  | 100+ 专家 Subagent（详见第04章）              | ⭐⭐⭐⭐     |
| `jeremylongshore/claude-code-plugins-plus` | 社区 200+ Plugin，持续更新                    | ⭐⭐⭐      |

**Marketplace 源详情示例**（`anthropics/skills`）：

```coq
anthropic-agent-skills (anthropics/skills)
3 available · 1 installed · Updated 2026/3/6

  ✅ document-skills (installed)
     Collection of document processing suite including Excel...
  ○  example-skills
     Collection of example skills demonstrating various capabi...
```

> **推荐先装**：`document-skills`（官方文档处理套件），安装后自动获得 pdf、pptx、xlsx 等全套 Skill，一次搞定所有文档格式。

------

## 5. 创建自定义 Plugin

### 5.1 Plugin 结构规范

Plugin 本质上是一个目录，里面有个 `.claude-plugin/plugin.json` 清单文件，加上你要打包的各种能力。

**最小结构（一个 Skill）：**

```nix
my-plugin/
├── .claude-plugin/
│   └── plugin.json      # 必需：Plugin 清单
└── skills/
    └── my-skill/
        └── SKILL.md
```

**完整结构（所有能力）：**

```nix
my-plugin/
├── .claude-plugin/
│   └── plugin.json      # 必需：Plugin 清单（只有这个在 .claude-plugin/ 内）
├── README.md            # 推荐：使用文档
├── LICENSE              # 推荐：开源协议
├── skills/              # 可选：Agent Skills
│   └── my-skill/
│       └── SKILL.md
├── commands/            # 可选：Slash Commands
│   └── my-command.md
├── agents/              # 可选：自定义 Agent 定义
├── hooks/               # 可选：事件钩子
│   └── hooks.json
├── .mcp.json            # 可选：MCP 服务配置
└── settings.json        # 可选：Plugin 启用时的默认设置
```

> ⚠️ **常见踩坑**：`commands/`、`skills/`、`agents/`、`hooks/` 都放在**插件根目录**，不要放进 `.claude-plugin/` 里——那里只放 `plugin.json`。

各目录职责速查：

| 目录/文件                    | 职责                                 |
| ---------------------------- | ------------------------------------ |
| `.claude-plugin/plugin.json` | Plugin 清单，定义名称/版本/作者      |
| `skills/`                    | Agent Skills（含 SKILL.md 的子目录） |
| `commands/`                  | Slash 命令（Markdown 文件）          |
| `agents/`                    | 自定义 Agent 定义                    |
| `hooks/`                     | 事件处理器（hooks.json）             |
| `.mcp.json`                  | MCP 服务配置                         |
| `settings.json`              | Plugin 启用时应用的默认设置          |

### 5.2 plugin.json 详解

`plugin.json` 放在 `.claude-plugin/` 目录下，是 Plugin 的「身份证」。

**完整示例：**

```json
{
  "name": "my-awesome-plugin",
  "description": "一句话说明这个 Plugin 做什么",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  },
  "license": "MIT",
  "homepage": "https://github.com/yourname/my-plugin",
  "repository": "https://github.com/yourname/my-plugin"
}
```

**字段速查：**

| 字段          | 是否必填 | 说明                                         |
| ------------- | -------- | -------------------------------------------- |
| `name`        | ✅        | Plugin 唯一标识，同时是 Skill 的命名空间前缀 |
| `description` | ✅        | 功能描述，Marketplace 中用于搜索和展示       |
| `version`     | ✅        | 语义化版本号（`主.次.补丁`，如 `1.0.0`）     |
| `author`      | 推荐     | 作者信息（`name` / `email` / `url`）         |
| `license`     | 推荐     | 开源协议（推荐 `MIT` 或 `Apache-2.0`）       |
| `homepage`    | 可选     | 项目主页或文档地址                           |
| `repository`  | 可选     | 代码仓库地址                                 |

> **关键点**：`name` 字段决定了 Skill 的调用前缀。Plugin 名叫 `my-plugin`，里面的 `hello` Skill 就要用 `/my-plugin:hello` 来触发——命名空间设计防止多个 Plugin 的 Skill 名称冲突。

### 5.3 实战：Hello World Plugin

5 分钟从零创建并测试你的第一个 Plugin：

**Step 1：创建目录结构**

```bash
mkdir -p hello-plugin/.claude-plugin
mkdir -p hello-plugin/skills/hello
```

**Step 2：创建清单 `.claude-plugin/plugin.json`**

```json
{
  "name": "hello-plugin",
  "description": "一个简单的问候示例 Plugin",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  },
  "license": "MIT"
}
```

**Step 3：创建 Skill `skills/hello/SKILL.md`**

```markdown
---
description: Greet the user with a friendly message
---

用友好的方式向用户打招呼。

步骤：
1. 获取当前系统时间
2. 根据时间段（上午/下午/晚上）调整问候语
3. 用轻松愉快的语气回复

示例输出：
"早上好！现在是 10:23，新的一天，有什么我能帮你的？"
```

**Step 4：本地测试**

不需要安装，直接用 `--plugin-dir` 标志加载：

```bash
# 加载插件并启动 Claude Code
claude --plugin-dir ./hello-plugin

# 启动后在对话里输入（注意命名空间格式）
> /hello-plugin:hello
```

看到问候输出，第一个 Plugin 就跑通了！

> `--plugin-dir` 是开发专用标志，每次修改 Skill 后重启 Claude Code 即可生效，无需安装。要同时测试多个 Plugin，可以多次指定：`claude --plugin-dir ./plugin-a --plugin-dir ./plugin-b`

**Step 5：带参数的 Skill**

`$ARGUMENTS` 占位符可以捕获用户输入的文本，让 Skill 动态响应：

```markdown
---
description: Greet the user with a personalized message
---

用友好的方式向名叫 "$ARGUMENTS" 的用户打招呼，让问候更有温度。
```

重启后测试：

```bash
> /hello-plugin:hello 凯神
# Claude 会用你传入的名字问候
```

### 5.4 进阶：带 Skill 的完整 Plugin

创建一个代码质量检查 Plugin，演示 Skill + Commands 的组合威力：

**项目结构：**

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
  "description": "自动检查代码质量，按严重程度给出改进建议",
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

# 代码质量检查专家

## 角色定义
你是一位资深代码审查专家，擅长发现代码质量问题并给出具体改进建议。

## 检查维度
1. **命名规范**：变量名/函数名是否语义清晰
2. **函数复杂度**：单个函数是否过长或嵌套过深
3. **重复代码**：是否存在可抽取的重复逻辑
4. **错误处理**：异常边界是否覆盖
5. **安全隐患**：是否存在注入/XSS 等风险

## 输出格式
按严重程度排序：
- 🔴 严重：必须修复
- 🟡 警告：建议修复
- 🟢 建议：可以改进

每条包含：问题描述 + 代码位置 + 修复建议
```

**`commands/check.md`：**

```markdown
对指定代码进行质量检查。

参数：$ARGUMENTS（可选，指定检查的文件路径）

步骤：
1. 如果指定了文件路径，只检查该文件
2. 如果未指定，检查最近修改的文件（通过 git diff --name-only 获取）
3. 按 5 个维度逐项分析，输出分级报告
```

**测试：**

```bash
claude --plugin-dir ./code-quality-checker

# 触发 Skill（自动识别）
> 帮我检查这段代码的质量

# 显式调用命令（注意命名空间）
> /code-quality-checker:check src/app.ts
```

> Plugin 的「超集」威力在这里体现得很清楚：**Commands 提供触发入口，Skills 提供专业能力**，打包在一起就是可分享的完整工具。

### 5.5 开发最佳实践

**1. 先用独立配置，再转 Plugin**

| 阶段     | 方式                     | 原因                                             |
| -------- | ------------------------ | ------------------------------------------------ |
| 实验期   | 直接放 `.claude/skills/` | Skill 名短（`/hello`），迭代快                   |
| 准备共享 | 打包成 Plugin            | Skill 带命名空间（`/my-plugin:hello`），便于分发 |

**2. 语义化版本号**

```gml
版本号格式：主.次.补丁（如 1.2.3）
  - 主版本（1.x.x）：破坏性变更，不向后兼容
  - 次版本（x.2.x）：新增功能，向后兼容
  - 补丁版（x.x.3）：Bug 修复
```

**3. README 必须包含四个部分**

| 部分     | 内容                                      |
| -------- | ----------------------------------------- |
| 功能说明 | 这个 Plugin 做什么，解决什么问题          |
| 安装方法 | 从 Marketplace 或 GitHub 安装的命令       |
| 使用示例 | 至少一个真实使用场景（含 Skill 调用格式） |
| 配置说明 | 如果有可配置项的话                        |

**4. Skill description 是关键**

`SKILL.md` frontmatter 中的 `description` 决定 Claude 能否自动识别场景并激活 Skill：

```markdown
# ❌ 太模糊，自动激活不准
description: Code review tool

# ✅ 明确触发场景，自动识别准确
description: Reviews code for best practices and potential issues. Use when reviewing code, checking PRs, or analyzing code quality.
```

------

## 6. 发布与分享

### 6.1 发布前检查清单

**必须完成：**

- ✅ `.claude-plugin/plugin.json` 格式正确，`name`/`description`/`version` 填写完整
- ✅ `README.md` 包含安装和使用说明（含 Skill 调用格式 `/插件名:skill名`）
- ✅ `LICENSE` 文件存在（推荐 MIT）
- ✅ 用 `claude --plugin-dir .` 本地测试通过，所有 Skill 和命令正常工作

**推荐完成：**

- ⭐ `CHANGELOG.md` 记录每个版本的变更内容
- ⭐ GitHub 仓库添加 Topics 标签（如 `claude-code-plugin`），便于被搜索
- ⭐ README 中注明最低 Claude Code 版本要求

### 6.2 发布到 GitHub

```bash
# 1. 初始化仓库
cd my-plugin
git init
git add .
git commit -m "feat: initial release v1.0.0"

# 2. 推送到 GitHub
git remote add origin https://github.com/yourname/my-plugin.git
git branch -M main
git push -u origin main
```

**创建 Release（让别人能按版本安装）：**

1. 进入 GitHub 仓库页面，点击 **Releases → Draft a new release**
2. Tag version 填 `v1.0.0`（必须以 `v` 开头）
3. 填写本次发布说明
4. 点击 **Publish release**

发布后，其他人就能通过 GitHub URL 直接安装：

```bash
# 在 /plugin 界面的 Discover 页顶部输入 GitHub 地址安装
# 或用 CLI
claude plugin install https://github.com/yourname/my-plugin
```

> 在 README 中加个版本徽章，一眼看出当前版本：
>
> ```markdown
> [Version](https://img.shields.io/github/v/release/yourname/my-plugin)
> ```

### 6.3 提交到官方 Marketplace

想让全球 Claude Code 用户都能搜到你的 Plugin？直接用**应用内提交表单**，不需要 Fork 仓库、提 PR，一个表单搞定：

| 平台              | 提交入口                             |
| ----------------- | ------------------------------------ |
| Claude.ai         | `claude.ai/settings/plugins/submit`  |
| Anthropic Console | `platform.claude.com/plugins/submit` |

**提交前确认：**

| 审核项                       | 要求                                  |
| ---------------------------- | ------------------------------------- |
| `.claude-plugin/plugin.json` | 格式正确，必填字段完整                |
| README                       | 安装和使用说明完整，含 Skill 调用格式 |
| 代码安全                     | 无恶意代码，依赖来源可信              |
| 功能完整                     | `--plugin-dir` 测试全部通过           |

提交后等待 Anthropic 审核（通常 1-3 个工作日）。审核通过后，你的 Plugin 就会出现在官方 Marketplace，全球 Claude Code 用户都能一键安装。

------

## 7. 故障排查

### 7.1 安装问题

| 现象                 | 原因                                | 解决方法                                           |
| -------------------- | ----------------------------------- | -------------------------------------------------- |
| `Plugin not found`   | 名称拼写错误或 Marketplace 源未添加 | 先在 Marketplaces 标签页添加源，再到 Discover 搜索 |
| 下载超时             | 网络问题                            | 设置代理或切换 npm 镜像源                          |
| `/plugin` 命令不存在 | Claude Code 版本过低                | 升级到 v1.0.33+（运行 `claude --version` 确认）    |

```bash
# 网络问题？换国内镜像源
npm config set registry https://registry.npmmirror.com

# 需要代理？（根据自己的代理端口修改）
export HTTP_PROXY="http://127.0.0.1:7897"
export HTTPS_PROXY="http://127.0.0.1:7897"
```

### 7.2 运行时问题

| 现象               | 原因                               | 解决方法                                          |
| ------------------ | ---------------------------------- | ------------------------------------------------- |
| Skill 调用格式不对 | 忘记命名空间前缀                   | Plugin 内的 Skill 用 `/插件名:skill名` 格式       |
| Skill 未自动激活   | SKILL.md 的 description 描述太模糊 | 明确写出触发场景，如 "Use when reviewing code..." |
| Hook 脚本权限错误  | 脚本缺少执行权限                   | `chmod +x hooks/my-hook.sh`                       |
| 配置修改不生效     | 未重启 Claude Code                 | 修改 Plugin 内容后需重启                          |

### 7.3 开发调试

| 现象                    | 原因             | 解决方法                                                |
| ----------------------- | ---------------- | ------------------------------------------------------- |
| `--plugin-dir` 加载失败 | 目录结构不正确   | 确认 `.claude-plugin/plugin.json` 存在于插件根目录      |
| Plugin 中 Skill 找不到  | skills/ 放错位置 | `skills/` 必须在插件根目录，不能在 `.claude-plugin/` 内 |
| plugin.json 解析报错    | JSON 格式错误    | 用在线 JSON 验证工具检查，确认冒号后有空格、无多余逗号  |

```bash
# 启用详细日志排查问题
export CLAUDE_LOG_LEVEL=debug
claude --plugin-dir ./my-plugin
```

------

## 8. 常见问题 FAQ

**Q1：Plugin 和 Skill 到底啥区别？**

一句话：**Skill 是能力本身，Plugin 是把能力打包成可安装、可分享的形式。** Plugin 可以包含 Skill，也可以包含 Commands、Hooks、MCP 配置等。

**Q2：Plugin 更新会覆盖我的配置吗？**

不会。更新时保留你的 `config.json`（个人配置），只更新 Plugin 代码文件（skills/、commands/ 等）。

**Q3：Plugin 开发需要懂编程吗？**

| 类型                    | 需要编程？ | 说明                    |
| ----------------------- | ---------- | ----------------------- |
| 只有 Commands 的 Plugin | ❌ 不需要   | 写 Markdown 就行        |
| 包含 Skills 的 Plugin   | ❌ 不需要   | 写 Markdown（SKILL.md） |
| 带脚本的 Plugin         | ✅ 需要     | Python/JavaScript 基础  |
| 带 MCP Server 的 Plugin | ✅ 需要     | Node.js/Python 开发经验 |

**Q4：Plugin 可以离线使用吗？**

安装在本地的 Plugin 可以离线使用。但如果 Plugin 内部调用了外部 API（如 GitHub API），那部分功能需要联网。

**Q5：Plugin 支持哪些编程语言？**

| 语言                  | 支持度 | 适用场景                       |
| --------------------- | ------ | ------------------------------ |
| JavaScript/TypeScript | ⭐⭐⭐⭐⭐  | MCP 集成、CLI 工具             |
| Python                | ⭐⭐⭐⭐⭐  | 数据处理、AI 集成              |
| Shell Script          | ⭐⭐⭐⭐   | 系统操作、自动化               |
| Go / Rust             | ⭐⭐     | 高性能工具，需编译为可执行文件 |

**Q6：如何查看 Plugin 使用了多少 Token？**

可以通过 `/cost` 命令查看整体 Token 消耗。Plugin 本身不单独计费，Token 消耗取决于 Plugin 加载的提示词量和对话内容。

**Q7：可以同时安装多个版本的 Plugin 吗？**

不可以。同一个 Plugin 只能安装一个版本。如果需要在不同项目使用不同版本，可以用项目级安装（默认）隔离。

**Q8：Plugin 报错如何获取帮助？**

1. 查看 Plugin 的 README 和 GitHub Issues
2. 在 Anthropic Discord 的 `#claude-code-plugins` 频道提问
3. 提 GitHub Issue 时包含：系统环境、Claude Code 版本、Plugin 版本、完整错误信息

------

## 9. 总结

本章你已掌握：

1. **Plugin 本质**：可分享的 Commands + Skills + Hooks + MCP 打包体，一键安装、自动更新
2. **核心区别**：Plugin 是"超集"概念，解决了 Commands/Skills 无法便捷分享的痛点
3. **生态现状**：官方 Marketplace + 社区 200+ Plugin，按需选择
4. **安装管理**：`/plugin` 界面的 Discover / Installed / Marketplaces 三大标签页，全程图形化操作
5. **自定义开发**：`.claude-plugin/plugin.json` 清单 + `skills/` + `commands/` 标准结构，`--plugin-dir` 秒测试
6. **发布分享**：GitHub Release 发布 + 官方 Marketplace 表单提交，让全世界用上你的 Plugin

# 第七章：从单兵到团队——企业级协作规范、[CI/CD](https://www.codefather.cn/course/1793910103252721665) 与安全合规实战

## 1. 前言

学完前六章，你已经能把 Claude Code 玩得很溜——Commands 定制、MCP 扩展、Plugins 一键装、Skills 打包复用，个人工作流基本满足了。

但问题来了：**换个角色，从个人开发者变成带 5 人、10 人团队的技术负责人，Claude Code 怎么用？**

典型的团队混乱场景，你可能中枪过：

| 混乱现象                     | 根因           | 后果                        |
| ---------------------------- | -------------- | --------------------------- |
| 每人的 CLAUDE.md 各不相同    | 没有统一规范   | AI 产出的代码风格乱成一锅粥 |
| 敏感密钥被 AI 意外提交到仓库 | 没有权限限制   | 安全事故，老板找你谈话      |
| 代码审查全靠人工盯           | 没接入 CI/CD   | 效率低，问题漏网            |
| 换个项目所有配置从头再来     | 没有标准化结构 | 重复劳动，新人懵圈          |
| 团队月账单翻倍超预期         | 没有成本管控   | 财务部门找过来了            |

**本章解决的就是这些问题。**

从团队规范到 CI/CD 集成，从安全合规到成本控制，一章讲完企业级 Claude Code 部署的全部要点。3 人团队能用，100 人团队也能用。

### 本章架构总览

![image-20260524122632653](/Users/book/Library/Application Support/typora-user-images/image-20260524122632653.png)

------

## 2. 团队协作规范

### 2.1 为什么需要团队规范

3 人以下团队，靠沟通凑合；超过 5 人，没有规范就是灾难的开始。

规范要解决三个核心问题：

| 问题              | 解决方案                              |
| ----------------- | ------------------------------------- |
| AI 产出质量不一致 | 统一 CLAUDE.md，全员共享同一套规则    |
| 配置无法传承      | 配置文件入库，随代码一起版本管理      |
| 新人上手慢        | 标准化目录结构 + 入职清单，1 天内跑通 |

### 2.2 项目结构标准化

**推荐的企业级目录结构：**

```nix
project-root/
├── .claude/                      # Claude Code 专用配置（全部入库）
│   ├── settings.json             # 团队统一权限与工具配置
│   ├── settings.local.json       # 个人本地覆盖（禁止入库！）
│   ├── commands/                 # 团队共享 Slash 命令
│   │   ├── code-review.md        # 代码审查命令
│   │   ├── security-check.md     # 安全检查命令
│   │   └── deploy.md             # 部署命令
│   └── skills/                   # 项目专属 Skill
│       └── project-skill/
│           └── SKILL.md
├── .github/
│   └── workflows/
│       └── claude-review.yml     # CI/CD 自动审查
├── docs/
│   └── ai-context/               # 给 AI 看的项目说明书
│       ├── project-structure.md
│       ├── coding-standards.md
│       └── architecture.md
├── src/
├── tests/
├── CLAUDE.md                     # 项目主配置（入库）
├── .mcp.json                     # MCP 服务器配置（入库）
└── .gitignore
```

**什么该入库，什么不该入库——一张表说清楚：**

| 文件/目录                     | 入库策略               | 原因                     |
| ----------------------------- | ---------------------- | ------------------------ |
| `.claude/settings.json`       | ✅ 必须入库             | 团队统一权限配置         |
| `.claude/settings.local.json` | ❌ 禁止入库             | 个人偏好，可能含本地路径 |
| `.claude/commands/`           | ✅ 必须入库             | 团队共享命令             |
| `.claude/skills/`             | ✅ 必须入库             | 项目专属能力             |
| `CLAUDE.md`                   | ✅ 必须入库             | 团队共享项目规范         |
| `.mcp.json`                   | ✅ 必须入库（不含密钥） | 团队共享 MCP 配置        |
| `.env` / `.env.local`         | ❌ 禁止入库             | 含密钥等敏感信息         |

**在 `.gitignore` 中明确写出来，不要靠记忆：**

```gitignore
# 禁止入库
.claude/settings.local.json
.env
.env.local
.env.*.local

# 确保这些不被其他规则误排除
!.claude/settings.json
!.claude/commands/
!.claude/skills/
!CLAUDE.md
!.mcp.json
```

**`docs/ai-context/` 是干嘛的？**

这个目录专门存放给 AI 看的项目上下文，不是给人看的 README，而是帮助 Claude 快速理解项目的「说明书」：

```markdown
# docs/ai-context/project-structure.md 示例

## 技术栈
- 前端：React 18 + TypeScript + Vite
- 后端：Node.js 20 + Fastify
- 数据库：PostgreSQL + Prisma ORM

## 核心模块
### 用户模块 (src/modules/user/)
负责注册、登录、权限管理，依赖 JWT + bcrypt

### 订单模块 (src/modules/order/)
负责下单、支付、状态管理，依赖用户模块和支付网关

## 代码约定
- 所有 API 响应格式：{ data, error, meta }
- 数据库操作必须使用 Prisma Client
- 日期时间统一 UTC
```

把详细内容放这里，CLAUDE.md 只写「详见 docs/ai-context/」，既让 AI 能找到，又不撑爆主配置文件的 token。

### 2.3 CLAUDE.md 三层配置体系

Claude Code 支持三层 CLAUDE.md，优先级从低到高：

| 层级     | 文件位置               | 作用范围       | 入库建议         |
| -------- | ---------------------- | -------------- | ---------------- |
| 全局配置 | `~/.claude/CLAUDE.md`  | 所有项目       | 个人文件，不入库 |
| 项目配置 | 项目根 `CLAUDE.md`     | 当前项目全团队 | ✅ 必须入库       |
| 模块配置 | `src/legacy/CLAUDE.md` | 特定子目录     | ✅ 按需入库       |

**项目 CLAUDE.md 模板（精简版，控制在 1000 tokens 以内）：**

```markdown
# [项目名] - Claude Code 配置

## 1. 项目概览
- **技术栈**：React 18 + Node.js 20 + PostgreSQL
- **当前阶段**：开发中
- **详细上下文**：见 docs/ai-context/

## 2. 代码规范
- 语言：TypeScript，禁止使用 any（特殊情况需注释说明）
- 命名：文件 kebab-case，类 PascalCase，变量 camelCase，常量 UPPER_SNAKE_CASE
- 函数 ≤50 行，类 ≤300 行
- 所有公共 API 必须有 JSDoc 注释，注释使用中文

## 3. 安全规则
- 禁止硬编码 API 密钥、密码等敏感信息
- 禁止提交 .env 文件
- 数据库查询必须参数化，禁止字符串拼接

## 4. 测试要求
- 新功能必须有单元测试，核心逻辑覆盖率 >80%
- 集成测试必须覆盖主要用户流程

## 5. Git 规范
提交格式：`<type>(<scope>): <description>`
类型：feat / fix / docs / refactor / test / chore

## 6. 项目特殊注意
[此处填写项目特有的规则，如遗留代码处理方式、禁用的第三方库等]
```

> **精简原则**：CLAUDE.md 目标控制在 <1,000 tokens。超长的配置文件每次请求都会消耗大量 token，得不偿失。详细内容一律放进 `docs/ai-context/`。

**全局 CLAUDE.md 模板（`~/.claude/CLAUDE.md`）：**

```markdown
# 全局 Claude Code 配置

## 个人偏好
- 使用中文回复
- 代码注释使用中文
- 偏好简洁直接的代码风格

## 安全底线（所有项目通用）
- 永远不在代码中包含真实的 API 密钥
- 不自动执行 rm -rf、DROP TABLE 等危险命令，执行前必须确认
- 不强制推送到 main/master 分支
```

### 2.4 代码审查命令

把代码审查流程标准化，创建团队共享命令 `.claude/commands/code-review.md`：

```markdown
对当前代码变更进行全面审查。

参数：$ARGUMENTS（可选，指定文件路径；不填则审查 git diff 的所有变更）

## 审查维度

### 1. 代码质量
- 命名是否表意，是否有重复代码
- 函数/类是否超出长度限制

### 2. 安全性
- 是否有 SQL 注入、XSS 风险
- 是否有硬编码的敏感信息
- 敏感数据处理是否安全

### 3. 性能
- 是否有 N+1 查询
- 是否有循环内的不必要计算

### 4. 测试
- 新增功能是否有对应测试
- 边界情况是否覆盖

## 输出格式

### 必须修改（Blocking）
- 问题描述 + 代码位置 + 修复建议

### 建议修改（Suggestion）
- 问题描述 + 改进建议

### 做得好的地方（Praise）
- 值得保留的优秀实践
```

使用方式：

```bash
/code-review              # 审查所有最近变更
/code-review src/auth/    # 只审查指定目录
```

### 2.5 新成员入职清单

```markdown
## Claude Code 新成员入职清单

### 第1步：环境准备
- [ ] 安装 Claude Code CLI（参考第一章）
- [ ] 配置全局 ~/.claude/CLAUDE.md（写入个人偏好）
- [ ] 获取 API 密钥并配置到环境变量

### 第2步：项目配置
- [ ] 克隆项目仓库
- [ ] 进入项目目录，运行 `claude` 初始化
- [ ] 输入 `/mcp` 确认 MCP 服务器正常连接
- [ ] 创建个人 .claude/settings.local.json（覆盖个人偏好，不入库）

### 第3步：熟悉规范
- [ ] 阅读项目 CLAUDE.md 和 docs/ai-context/
- [ ] 输入 `/help` 查看团队自定义命令列表
- [ ] 运行一次 `/code-review` 体验审查流程

### 第4步：验证配置
- [ ] 提交一个测试 PR，确认 CI 自动审查触发正常
- [ ] 检查权限配置：尝试执行一条危险命令验证是否被拦截
```

------

## 3. CI/CD 集成

**CI/CD 流程全景图**：

![image-20260524122733811](/Users/book/Library/Application Support/typora-user-images/image-20260524122733811.png)

### 3.1 GitHub Actions 基础配置

Anthropic 提供了官方 GitHub Action：`anthropics/claude-code-action`，直接在 PR 上触发 Claude Code 审查，零代码配置。

**准备工作——先在 GitHub 仓库添加 Secret：**

1. 进入仓库 **Settings → Secrets and variables → Actions**
2. 点击 **New repository secret**
3. 名称：`ANTHROPIC_API_KEY`，值：你的 API Key

**最简配置**（`.github/workflows/claude-review.yml`）：

```yaml
name: Claude Code Review

on:
  pull_request:
    types: [opened, synchronize, reopened]
  issue_comment:
    types: [created]

permissions:
  contents: read
  pull-requests: write
  issues: write

jobs:
  claude-review:
    if: |
      github.event_name == 'pull_request' ||
      (github.event_name == 'issue_comment' &&
       contains(github.event.comment.body, '@claude'))
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0   # 获取完整历史，用于 diff 比较

      - name: Run Claude Code Review
        uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          model: claude-sonnet-4-6-20250929
          max_tokens: 4096
          timeout: 300
```

配置完成后：

- 每次提 PR，Claude 自动审查并在 PR 下方留评论
- 在 PR 或 Issue 评论中 `@claude xxx`，Claude 响应交互式指令

### 3.2 多场景工作流

一个完整的团队工作流通常需要三类并行 Job：

| Job             | 触发时机         | 功能           |
| --------------- | ---------------- | -------------- |
| `review`        | PR 创建/更新     | 代码质量审查   |
| `security-scan` | PR 创建/更新     | 安全漏洞扫描   |
| `interactive`   | 评论含 `@claude` | 响应交互式指令 |

```yaml
name: Claude Code CI

on:
  pull_request:
    types: [opened, synchronize, reopened]
  issue_comment:
    types: [created]

permissions:
  contents: read
  pull-requests: write
  issues: write

env:
  CLAUDE_MODEL: claude-sonnet-4-6-20250929

jobs:
  # ===== 代码审查 =====
  review:
    name: Code Review
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Claude Code Review
        uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          model: ${{ env.CLAUDE_MODEL }}
          max_tokens: 4096
          prompt: |
            请审查这次 PR 的代码变更，重点关注：
            1. 代码质量和可维护性
            2. 潜在的 bug 和安全问题
            3. 性能考量
            4. 测试覆盖建议
            请用中文回复，按「必须修改 / 建议修改 / 优点」三部分输出。

  # ===== 安全扫描 =====
  security-scan:
    name: Security Scan
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Claude Security Scan
        uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          model: ${{ env.CLAUDE_MODEL }}
          max_tokens: 2048
          prompt: |
            请对本次 PR 进行安全扫描，检查：
            1. 硬编码的敏感信息（API Key、密码、token 等）
            2. SQL 注入、XSS、命令注入风险
            3. 不安全的依赖版本
            4. 权限配置问题
            发现高危问题请在开头标注 [SECURITY-CRITICAL]。

  # ===== 交互式指令 =====
  interactive:
    name: Interactive Commands
    if: |
      github.event_name == 'issue_comment' &&
      contains(github.event.comment.body, '@claude')
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Process Command
        uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          model: ${{ env.CLAUDE_MODEL }}
          prompt: ${{ github.event.comment.body }}
```

**交互式指令使用示例（在评论中）：**

```less
@claude 帮我分析这段代码的性能瓶颈
@claude 生成这个模块的单元测试
@claude /code-review src/payment/
```

### 3.3 完整流水线示例

加上 lint、测试、构建、部署的完整 6 阶段流水线：

```yaml
name: Full CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  lint:
    name: Lint & Format
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci && npm run lint && npm run format:check

  test:
    name: Unit Tests
    needs: lint
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci && npm test -- --coverage

  claude-review:
    name: Claude Review
    if: github.event_name == 'pull_request'
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          model: claude-sonnet-4-6-20250929
          max_tokens: 4096
          prompt: 请审查 PR 代码变更，输出质量评估、安全检查、改进建议三部分结果（中文）。

  build:
    name: Build
    needs: [test]
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci && npm run build
      - uses: actions/upload-artifact@v4
        with:
          name: build-output
          path: dist/

  deploy-staging:
    name: Deploy Staging
    if: github.ref == 'refs/heads/develop'
    needs: build
    runs-on: ubuntu-latest
    environment: staging
    steps:
      - uses: actions/download-artifact@v4
        with:
          name: build-output
      - run: echo "部署到 Staging 环境..."

  deploy-production:
    name: Deploy Production
    if: github.ref == 'refs/heads/main'
    needs: build
    runs-on: ubuntu-latest
    environment: production
    steps:
      - uses: actions/download-artifact@v4
        with:
          name: build-output
      - run: echo "部署到 Production 环境..."
```

> **注意**：`claude-review` Job 只在 PR 事件时触发，push 到 main/develop 时不触发，避免浪费 token。

------

## 4. 安全与合规

### 4.1 权限系统配置

Claude Code 采用 **allow / deny 双列表**权限模型：

| 级别        | 行为               | 适用操作                       |
| ----------- | ------------------ | ------------------------------ |
| Allow       | 直接执行，无需确认 | 低风险高频操作（读文件、搜索） |
| Ask（默认） | 执行前弹出确认框   | 有一定影响的操作（编辑文件）   |
| Deny        | 完全拒绝，无法绕过 | 高危操作（删除、强推、sudo）   |

**`.claude/settings.json` 权限配置示例：**

```json
{
  "permissions": {
    "allow": [
      "Read",
      "Glob",
      "Grep",
      "WebFetch",
      "WebSearch",
      "Bash(npm test *)",
      "Bash(git diff *)",
      "Bash(git log *)",
      "Bash(git status)"
    ],
    "deny": [
      "Bash(rm -rf /)",
      "Bash(rm -rf ~)",
      "Bash(git push --force)",
      "Bash(git reset --hard)",
      "Bash(sudo *)",
      "Bash(curl * | bash)",
      "Read(./.env)",
      "Read(./secrets/**)"
    ]
  }
}
```

> **规则说明**：未出现在任一列表中的工具和命令默认走 ask（弹出确认）。deny 优先级高于 allow，支持通配符匹配。

### 4.2 allowedTools 白名单

比 permissions 更细粒度的工具控制，支持路径限制：

```json
{
  "allowedTools": [
    "Read",
    "Glob",
    "Grep",
    "Edit(src/**)",
    "Write(src/**)",
    "Write(tests/**)",
    "Bash(npm *)",
    "Bash(git status)",
    "Bash(git diff *)",
    "Bash(git add *)",
    "Bash(git commit *)",
    "mcp__context7__*",
    "mcp__github__*"
  ],
  "disallowedTools": [
    "Bash(rm -rf *)",
    "Bash(sudo *)",
    "Write(.env*)",
    "Write(**/secrets/*)"
  ]
}
```

**白名单匹配规则速查：**

| 写法                 | 含义               | 示例                        |
| -------------------- | ------------------ | --------------------------- |
| `"Read"`             | 精确匹配工具名     | 只允许 Read 工具            |
| `"Bash(npm *)"`      | 通配符匹配命令参数 | 允许所有 npm 子命令         |
| `"Edit(src/**)"`     | 路径通配符         | 只允许编辑 src 目录下的文件 |
| `"mcp__context7__*"` | MCP 工具通配符     | 允许 context7 的所有功能    |

**分环境配置建议：**

| 环境     | 策略                      | 说明         |
| -------- | ------------------------- | ------------ |
| 开发环境 | 宽松，但保留危险命令 deny | 便于迭代     |
| Staging  | 中等，限制 Write 范围     | 模拟生产     |
| CI/CD    | 严格，只保留必要工具      | 最小权限原则 |

### 4.3 审计日志

**启用审计日志配置（`.claude/settings.json`）：**

```json
{
  "audit": {
    "enabled": true,
    "logPath": "./logs/claude-audit/",
    "retention": "90d",
    "events": [
      "tool_use",
      "file_access",
      "command_execution",
      "permission_change",
      "error"
    ]
  }
}
```

**审计日志格式示例：**

```json
{
  "entries": [
    {
      "timestamp": "2026-01-15T10:30:45.123Z",
      "userId": "dev@company.com",
      "event": "tool_use",
      "tool": "Bash",
      "command": "npm test",
      "status": "success",
      "duration": 5432
    },
    {
      "timestamp": "2026-01-15T10:31:00.456Z",
      "userId": "dev@company.com",
      "event": "permission_denied",
      "tool": "Read",
      "path": ".env.production",
      "reason": "Path in denied list",
      "status": "blocked"
    }
  ]
}
```

**企业合规检查清单：**

| 合规项       | 检查内容                  | 通过条件                  |
| ------------ | ------------------------- | ------------------------- |
| 密钥安全     | API 密钥通过环境变量传入  | 代码中无硬编码密钥        |
| 敏感文件保护 | .env 类文件在 deny 列表中 | AI 无法读取               |
| 危险命令拦截 | rm -rf / sudo 被明确禁止  | deny 列表覆盖             |
| 审计追踪     | 所有工具调用有完整日志    | `audit.enabled = true`    |
| 日志保留     | 保留期符合公司/行业政策   | `retention >= 90d`        |
| 权限最小化   | 每个角色只有必要权限      | allowedTools 明确限定范围 |

------

## 5. 性能与成本优化

### 5.1 上下文管理

**上下文窗口的构成（以 Claude Sonnet 4.6 为例，上限 200K tokens）：**

| 组成部分     | 典型大小           | 优化优先级    |
| ------------ | ------------------ | ------------- |
| 系统提示词   | ~2,000 tokens      | 无法优化      |
| CLAUDE.md    | 1,000–5,000 tokens | ⭐⭐⭐ 重点优化  |
| 对话历史     | 动态增长           | ⭐⭐⭐ 定期清理  |
| 工具返回结果 | 动态增长           | ⭐⭐ 控制读取量 |
| 当前消息     | 用户输入           | ⭐ 精简描述    |

**三个实用优化策略：**

**策略一：精简 CLAUDE.md**

```markdown
# ❌ 冗长写法（每次浪费几千 token）
我们的团队使用以下代码规范。首先，所有代码必须使用 TypeScript 编写。
其次，我们要求所有函数都有 JSDoc 注释。另外，变量命名必须遵循
camelCase 规范……（继续 500 字）

# ✅ 精简写法（同样信息量）
## 代码规范
- 语言：TypeScript，禁用 any
- 注释：JSDoc 必需（中文）
- 命名：变量 camelCase，类 PascalCase
- 行数：函数 ≤50，类 ≤300
```

**策略二：大任务分步拆解**

```1c
# ❌ 一次性大任务（容易超限，Claude 也容易出错）
"重构整个项目的用户模块、订单模块、支付模块..."

# ✅ 分步骤执行
步骤1：分析用户模块现状
步骤2：提出重构方案
步骤3：执行用户模块重构，验证结果
步骤4：继续订单模块
```

**策略三：分层 CLAUDE.md**

```nix
项目根/CLAUDE.md           # 全局规则（目标 <1,000 tokens）
├── src/CLAUDE.md          # 源码特定规则（<500 tokens）
├── tests/CLAUDE.md        # 测试规则（<300 tokens）
└── src/legacy/CLAUDE.md   # 遗留代码专用规则（<300 tokens）
```

**常用对话管理命令：**

| 命令            | 时机                     | 效果                       |
| --------------- | ------------------------ | -------------------------- |
| `/clear`        | 任务完成后，切换新任务前 | 清空对话历史，释放上下文   |
| `/compact`      | 对话过长但需要保留上下文 | 压缩历史为摘要，节省 token |
| `Shift + Enter` | 需要输入多行指令时       | 换行不发送，整理好再提交   |

### 5.2 成本控制

**各模型价格参考（2026 年）：**

| 模型              | 输入    | 输出    | 推荐场景                       |
| ----------------- | ------- | ------- | ------------------------------ |
| Claude Haiku 4.5  | $0.25/M | $1.25/M | 简单代码生成、批量文件处理     |
| Claude Sonnet 4.6 | $3/M    | $15/M   | 日常开发、代码审查（默认推荐） |
| Claude Opus 4.5   | $15/M   | $75/M   | 架构设计、复杂推理任务         |

**单次对话成本估算：**

```asciidoc
成本 = (输入 tokens / 1M × 输入价格) + (输出 tokens / 1M × 输出价格)

示例（Sonnet 4.6，10K 输入 + 2K 输出）：
= (10,000 / 1M × 3) + (2,000 / 1M × 15)
= $0.03 + $0.03 = $0.06/次
```

**成本控制配置（`.claude/settings.json`）：**

```json
{
  "costControl": {
    "dailyLimit": 10.0,
    "monthlyLimit": 200.0,
    "alertThreshold": 0.8,
    "actions": {
      "onDailyLimitReached": "warn",
      "onMonthlyLimitReached": "block"
    }
  }
}
```

**五条省钱建议：**

| 建议                                     | 效果                   |
| ---------------------------------------- | ---------------------- |
| 简单任务用 Haiku，复杂任务用 Opus        | 成本最多降低 80%       |
| 批量处理：一次审查多个文件而不是逐个审查 | 减少重复初始化开销     |
| 用 `/compact` 压缩长对话                 | 降低历史 token 累积    |
| 精简 CLAUDE.md（控制在 1K tokens）       | 减少每次请求的固定成本 |
| CI 中设置 `max_tokens` 上限              | 防止单次超支           |

### 5.3 verbose 调试

开启 verbose 模式，能看到每次请求的完整 token 消耗和工具调用过程，是定位性能瓶颈最直接的工具：

```bash
# 单次开启
claude --verbose

# 持久开启（写入配置）
# .claude/settings.json
{
  "verbose": true
}
```

**关键日志信息解读：**

```routeros
[DEBUG] CLAUDE.md tokens: 1,234          → CLAUDE.md 占用了多少 token
[DEBUG] Context size: 8,432 tokens       → 当前上下文总大小
[DEBUG] Available context: 191,568 tokens → 还剩多少可用空间
[DEBUG] Tool call: Glob → 12 files found  → 某次工具调用的结果
[DEBUG] Input tokens: 8,011              → 本次请求发送了多少 token
[DEBUG] Output tokens: 1,234            → 本次响应返回了多少 token
[DEBUG] Latency: 5,000ms                → 接口响应延迟
[DEBUG] Cost: $0.0234                    → 本次调用花了多少钱
```

**常见性能问题速查：**

| 症状              | 可能原因           | 解决方案                          |
| ----------------- | ------------------ | --------------------------------- |
| 响应慢（>10s）    | 上下文过大         | `/clear` 清空对话，精简 CLAUDE.md |
| 频繁超 token 限制 | 单次任务过大       | 分解成多个步骤执行                |
| 成本快速上涨      | 无效迭代多         | 优化提示词，减少来回修改次数      |
| 工具调用失败      | MCP 服务器连接问题 | 检查 `.mcp.json` 配置和网络连通性 |

------

## 6. 故障排查

### 6.1 团队协作问题

| 现象                                 | 原因                             | 解决方法                                                     |
| ------------------------------------ | -------------------------------- | ------------------------------------------------------------ |
| 不同成员 AI 产出风格差异大           | CLAUDE.md 未统一                 | 确认 `CLAUDE.md` 和 `settings.json` 已入库，团队成员拉取最新版本 |
| CI 自动审查未触发                    | Secrets 未配置或 Action 版本太旧 | 检查 GitHub Secrets 中的 `ANTHROPIC_API_KEY`，升级 Action 到最新版 |
| `settings.local.json` 被意外入库     | `.gitignore` 缺失对应规则        | 补充 `.gitignore`，并从仓库历史中清除                        |
| 团队成员的 `/code-review` 命令找不到 | commands/ 目录未入库             | 确认 `.gitignore` 没有错误排除 `.claude/commands/`           |

### 6.2 安全权限问题

| 现象                        | 原因                        | 解决方法                                                |
| --------------------------- | --------------------------- | ------------------------------------------------------- |
| 危险命令没有被拦截          | deny 列表未配置             | 在 `settings.json` 的 `permissions.deny` 中补充高危命令 |
| allowedTools 设置不生效     | JSON 格式错误（多余逗号等） | 用 JSON 在线验证工具检查格式                            |
| 审计日志目录不存在报错      | 目录未预先创建              | `mkdir -p ./logs/claude-audit/`                         |
| CI 中安全扫描漏掉了高危问题 | prompt 描述不够具体         | 在 prompt 中明确列出要检查的安全类别                    |

### 6.3 性能与成本问题

| 现象                                   | 原因                           | 解决方法                                              |
| -------------------------------------- | ------------------------------ | ----------------------------------------------------- |
| 月账单远超预期                         | 没有成本上限配置               | 配置 `costControl.monthlyLimit` 并设置告警            |
| CLAUDE.md 加载慢，每次响应都慢         | 配置文件过大                   | 精简到 <1,000 tokens，详情移到 `docs/ai-context/`     |
| CI 中 Claude 调用偶发超时              | 没有设置 timeout 和 max_tokens | 在 Action 中配置 `timeout: 300` 和 `max_tokens: 4096` |
| verbose 日志看到 CLAUDE.md tokens 很高 | CLAUDE.md 内容过多             | 审查 CLAUDE.md，删除冗余内容，提取到 ai-context 目录  |

------

## 7. 总结

本章你已掌握：

1. **团队规范**：标准化目录结构、CLAUDE.md 三层配置体系、配置入库策略、新成员入职 SOP
2. **CI/CD 集成**：GitHub Actions 自动审查（`anthropics/claude-code-action`）、多场景工作流（代码审查 + 安全扫描 + 交互指令）、完整 6 阶段流水线
3. **安全合规**：allow/deny 权限模型、allowedTools 白名单精细控制、审计日志配置与合规检查清单
4. **性能优化**：上下文管理三策略、verbose 模式 token 分析、常见性能瓶颈定位
5. **成本控制**：按场景选模型、批量处理、成本预警配置、五条省钱建议

**一句话总结**：个人用 Claude Code 靠感觉，团队用 Claude Code 靠规范。把本章的配置落地到你的项目里，10 人团队也能用得既高效又安全。

# 第八章：企业深水区——密钥安全、团队配置与合规审计全攻略

## 本章安全架构总览

![image-20260524122818054](/Users/book/Library/Application Support/typora-user-images/image-20260524122818054.png)

------

## 1. 术语速查表

凯神先把企业级关键术语拉出来，后面用到的时候直接对照：

| 术语            | 英文全称                           | 通俗解释                                   |
| --------------- | ---------------------------------- | ------------------------------------------ |
| Secrets Manager | -                                  | 密钥管理服务，安全存储 API Key 等敏感信息  |
| Vault           | HashiCorp Vault                    | 企业级密钥管理工具，支持密钥轮换和访问审计 |
| Git Hooks       | -                                  | Git 的钩子脚本，在提交/推送前自动执行检查  |
| ADR             | Architecture Decision Record       | 架构决策记录，记录技术选型的原因和上下文   |
| GDPR            | General Data Protection Regulation | 欧盟通用数据保护条例                       |
| SOC 2           | Service Organization Control 2     | 服务组织控制审计标准                       |
| 2FA             | Two-Factor Authentication          | 双因素认证，增强账户安全                   |
| RPM             | Requests Per Minute                | 每分钟请求数，API 速率限制单位             |
| DPO             | Data Protection Officer            | 数据保护官，负责合规的角色                 |
| Bandit          | -                                  | Python 安全代码扫描工具                    |
| Trivy           | -                                  | 容器镜像安全扫描工具                       |

------

## 2. 团队配置统一化

### 2.1 为什么要统一配置

凯神见过太多团队踩这个坑了：

| 问题                        | 后果                  | 发生概率 |
| --------------------------- | --------------------- | -------- |
| 每个人 `settings.json` 不同 | 代码风格混乱，PR 冲突 | 95%      |
| API Key 直接写在配置文件    | 泄露到 Git 仓库       | 80%      |
| 新人手动配置需要 2 小时     | 效率低下，容易出错    | 100%     |
| 配置更新无法同步            | 部分成员用旧配置      | 70%      |
| 没有版本控制                | 回滚困难              | 60%      |

**统一配置能一次性解决以上所有问题。**

### 2.2 标准配置仓库结构

凯神推荐的团队配置仓库长这样：

```nix
team-claude-config/
├── README.md                    # 配置说明文档
├── .editorconfig                # EditorConfig 通用规则
├── .env.example                 # 环境变量模板（绝对不放真实密钥！）
├── install.sh                   # 一键安装脚本（Linux/macOS）
├── install.ps1                  # 一键安装脚本（Windows）
├── update.sh                    # 配置更新脚本
├── validate.sh                  # 配置验证脚本
├── vscode/                      # VS Code 配置
│   ├── settings.json
│   ├── keybindings.json
│   ├── extensions.json          # 推荐扩展列表
│   └── snippets/
│       ├── python.json
│       └── javascript.json
├── cursor/                      # Cursor 配置
│   ├── settings.json
│   └── keybindings.json
├── claude/                      # Claude Code 专用配置
│   ├── system-prompts/          # 系统提示词
│   │   ├── code-review.md
│   │   ├── refactor.md
│   │   └── testing.md
│   ├── skills/                  # 团队技能包
│   │   └── team-standards/
│   │       ├── SKILL.md
│   │       └── prompts/
│   └── hooks/                   # Git hooks 模板
│       ├── pre-commit
│       ├── pre-push
│       └── commit-msg
├── ci/                          # CI/CD 配置
│   ├── github-actions/
│   │   ├── claude-review.yml
│   │   └── quality-check.yml
│   └── gitlab-ci/
│       └── .gitlab-ci.yml
├── docs/                        # 文档目录
│   ├── onboarding.md            # 新人上手指南
│   ├── troubleshooting.md
│   └── best-practices.md
├── scripts/                     # 工具脚本
│   ├── sync-config.sh
│   ├── check-updates.sh
│   └── backup-config.sh
└── tests/                       # 配置测试
    └── test_config.py
```

### 2.3 配置统一五条原则

| #    | 原则                            | 要求                                                         |
| ---- | ------------------------------- | ------------------------------------------------------------ |
| 1    | **Single Source of Truth**      | 所有配置在 Git 仓库，本地配置 = 仓库的符号链接               |
| 2    | **Environment Variables First** | 敏感信息（API Key）**必须**用环境变量，绝对路径也用环境变量替换 |
| 3    | **Platform Agnostic**           | 脚本支持 Windows/Linux/macOS，路径用相对路径                 |
| 4    | **Automated Validation**        | 每次更新自动验证配置正确性，CI 流水线中运行验证测试          |
| 5    | **Rollback Support**            | 用 Git tag 标记稳定版本，提供一键回滚脚本                    |

### 2.4 一键安装脚本

核心安装脚本结构（`install.sh`）：

```bash
#!/bin/bash
# install.sh - 团队 Claude 配置一键安装脚本
set -e

# ==================== 颜色定义 ====================
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m'

log_info()    { echo -e "${GREEN}[INFO]${NC} $1"; }
log_warn()    { echo -e "${YELLOW}[WARN]${NC} $1"; }
log_error()   { echo -e "${RED}[ERROR]${NC} $1"; }
log_success() { echo -e "${BLUE}[SUCCESS]${NC} $1"; }

# ==================== 检测操作系统 ====================
detect_os() {
    if [[ "$OSTYPE" == "linux-gnu"* ]]; then
        OS="linux"
    elif [[ "$OSTYPE" == "darwin"* ]]; then
        OS="macos"
    elif [[ "$OSTYPE" == "msys" || "$OSTYPE" == "cygwin" ]]; then
        OS="windows"
    else
        log_error "不支持的操作系统: $OSTYPE"
        exit 1
    fi
    log_info "检测到操作系统: $OS"
}

# ==================== 备份现有配置 ====================
backup_existing_config() {
    log_info "备份现有配置..."
    BACKUP_DIR="$HOME/.claude-config-backup-$(date +%Y%m%d-%H%M%S)"
    mkdir -p "$BACKUP_DIR"

    case "$OS" in
        linux)   VSCODE_DIR="$HOME/.config/Code/User" ;;
        macos)   VSCODE_DIR="$HOME/Library/Application Support/Code/User" ;;
        windows) VSCODE_DIR="$APPDATA/Code/User" ;;
    esac

    if [[ -d "$VSCODE_DIR" ]]; then
        cp -r "$VSCODE_DIR" "$BACKUP_DIR/vscode-user"
        log_info "VS Code 配置已备份到: $BACKUP_DIR/vscode-user"
    fi

    log_success "备份完成: $BACKUP_DIR"
}

# ==================== 主函数 ====================
main() {
    echo "================================================"
    echo "  团队 Claude 配置一键安装脚本"
    echo "================================================"
    detect_os
    backup_existing_config
    # ... 后续安装步骤（链接配置文件、安装 hooks 等）
    log_success "安装完成！请重启编辑器使配置生效。"
}

main
```

> 凯神提醒：完整脚本建议放在团队配置仓库里维护，这里展示核心结构。Windows 用户对应写 `install.ps1`。

------

## 3. Git Hooks + Claude Code 深度集成

**Git Hooks 工作流程**：

![image-20260524122851577](/Users/book/Library/Application Support/typora-user-images/image-20260524122851577.png)

### 3.1 为什么需要 Git Hooks

| 问题               | 后果                 | Git Hook 解决方案            |
| ------------------ | -------------------- | ---------------------------- |
| 代码未格式化就提交 | PR 冲突，难以 review | `pre-commit` hook 自动格式化 |
| 提交信息混乱       | Git 历史难以追踪     | `commit-msg` hook 规范化     |
| 未运行测试就 push  | 破坏主分支           | `pre-push` hook 强制测试     |
| 代码有明显 bug     | 浪费 reviewer 时间   | Claude 自动代码审查          |
| 文档未更新         | 文档与代码不一致     | Claude 自动检测提醒          |

**Git Hooks + Claude Code = 自动化代码质量守门员。**

### 3.2 Pre-commit Hook：提交前自动检查

```bash
#!/bin/bash
# .git/hooks/pre-commit - 提交前检查脚本
# 集成 Claude Code 进行自动代码审查
set -e

# ==================== 获取暂存文件 ====================
get_staged_files() {
    git diff --cached --name-only --diff-filter=ACM
}

# ==================== Python 代码格式化 ====================
format_python() {
    echo "[INFO] 格式化 Python 代码..."
    PYTHON_FILES=$(get_staged_files | grep '\.py$' || true)
    if [[ -z "$PYTHON_FILES" ]]; then
        return 0
    fi

    # 使用 Black 格式化
    if command -v black &> /dev/null; then
        echo "$PYTHON_FILES" | xargs black --quiet
        echo "[INFO] Black 格式化完成"
    fi

    # 使用 Ruff 检查
    if command -v ruff &> /dev/null; then
        if ! echo "$PYTHON_FILES" | xargs ruff check; then
            echo "[ERROR] Ruff 检查失败，请修复错误后再提交"
            exit 1
        fi
    fi

    # 重新添加格式化后的文件
    echo "$PYTHON_FILES" | xargs git add
}

# ==================== Claude 代码审查 ====================
claude_code_review() {
    echo "[INFO] 运行 Claude Code 审查..."
    DIFF=$(git diff --cached)
    if [[ -z "$DIFF" ]]; then
        return 0
    fi

    # 调用 Claude API 进行代码审查
    REVIEW_RESULT=$(curl -s https://api.anthropic.com/v1/messages \
      -H "x-api-key: ${ANTHROPIC_API_KEY}" \
      -H "anthropic-version: 2023-06-01" \
      -H "content-type: application/json" \
      -d "{
        \"model\": \"claude-haiku-4-5-20251001\",
        \"max_tokens\": 2048,
        \"messages\": [{
          \"role\": \"user\",
          \"content\": \"请快速审查以下代码变更，仅报告严重问题。如果没有严重问题，回复'通过'。\\n\\n${DIFF}\"
        }]
      }" | jq -r '.content[0].text')

    # 检查是否有严重问题
    if echo "$REVIEW_RESULT" | grep -qi "严重\|critical\|security"; then
        echo "[ERROR] Claude 发现严重问题，提交被拒绝："
        echo "$REVIEW_RESULT"
        exit 1
    fi

    echo "[INFO] Claude 代码审查通过"
}

# ==================== 主函数 ====================
main() {
    echo "[INFO] 开始 pre-commit 检查..."
    format_python
    claude_code_review
    echo "[INFO] 所有检查通过，允许提交"
}

main
```

> 凯神建议：`pre-commit` 调用 Claude 审查时用 **Haiku 模型**（速度快、成本低），只拦截严重问题。详细审查交给 CI/CD 阶段的 Sonnet/Opus。

### 3.3 Commit-msg Hook：规范提交信息

```bash
#!/bin/bash
# .git/hooks/commit-msg - 提交信息规范化脚本

COMMIT_MSG_FILE=$1
COMMIT_MSG=$(cat "$COMMIT_MSG_FILE")

# Conventional Commits 规范检查
TYPES="feat|fix|docs|style|refactor|perf|test|chore|build|ci|revert"
if ! echo "$COMMIT_MSG" | grep -qE "^($TYPES)(\(.+\))?: .+"; then
    echo "[WARN] 提交信息不符合 Conventional Commits 规范"
    echo "[WARN] 格式：type(scope): description"
    echo "[WARN] 示例：feat(auth): 添加 OAuth 登录功能"

    # 可选：调用 Claude 自动生成
    if [[ -n "$ANTHROPIC_API_KEY" ]]; then
        DIFF=$(git diff --cached --stat)
        echo "[INFO] 正在用 Claude 生成规范提交信息..."
        # ... 调用 Claude API 生成 commit message
    fi

    exit 1
fi

echo "[INFO] 提交信息格式检查通过"
```

------

## 4. 团队知识库建设

### 4.1 知识库系统架构

把团队的编码标准、架构模式、最佳实践都沉淀到 Claude 可读的知识库里：

```nix
team-knowledge-base/
├── .claude/
│   ├── skills/
│   │   ├── team-standards/        # 团队编码标准
│   │   │   ├── SKILL.md
│   │   │   └── prompts/
│   │   │       ├── python-style.md
│   │   │       ├── javascript-style.md
│   │   │       └── api-design.md
│   │   ├── architecture/          # 架构模式
│   │   │   ├── SKILL.md
│   │   │   └── prompts/
│   │   │       ├── microservices.md
│   │   │       └── database-design.md
│   │   └── testing/               # 测试规范
│   │       ├── SKILL.md
│   │       └── prompts/
│   │           ├── unit-test.md
│   │           └── integration-test.md
│   └── memory/
│       ├── common-patterns.json   # 常见代码模式
│       ├── team-decisions.json    # 技术决策记录（ADR）
│       └── best-practices.json    # 最佳实践
├── docs/
│   ├── architecture/              # 架构文档
│   ├── api/                       # API 文档
│   └── guides/                    # 开发指南
└── README.md
```

### 4.2 团队编码标准 Skill

在 `SKILL.md` 里定义团队编码标准：

```markdown
---
name: team-standards
description: 团队编码标准和最佳实践
---

# 团队编码标准

## Python 代码规范
- 使用 Black 格式化，行宽 88
- 类型注解覆盖所有公开函数
- Docstring 使用 Google 风格
- 导入顺序：标准库 → 第三方 → 本地

## JavaScript/TypeScript 规范
- 使用 ESLint + Prettier
- 优先使用 TypeScript
- React 组件使用函数式 + Hooks
- API 调用统一使用 fetch wrapper

## API 设计规范
- RESTful 命名，资源用复数
- 统一错误响应格式 { code, message, data }
- 版本号放在 URL 路径中 /api/v1/
- 分页用 cursor-based pagination
```

> 凯神提醒：把这个 Skill 放在项目 `.claude/skills/` 下，Claude Code 写代码时就会自动遵守团队规范。新人入职第一天就能写出符合团队标准的代码。

------

## 5. [CI/CD](https://www.codefather.cn/course/1793910103252721665) 深度集成

### 5.1 GitHub Actions 完整配置

第七章已经介绍了 `anthropics/claude-code-action@v1` 的基础用法，这里给一个更完整的企业级配置：

```yaml
# .github/workflows/claude-ci.yml
name: Claude Code CI

on:
  pull_request:
    branches: [main, develop]
  push:
    branches: [main, develop]

env:
  ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}

jobs:
  # ===== 代码审查 =====
  code-review:
    name: Claude 代码审查
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: 获取变更文件
        id: changed-files
        uses: tj-actions/changed-files@v39

      - name: Claude 代码审查
        if: steps.changed-files.outputs.any_changed == 'true'
        run: |
          DIFF=$(git diff origin/${{ github.base_ref }}...HEAD)
          REVIEW=$(curl -s https://api.anthropic.com/v1/messages \
            -H "x-api-key: $ANTHROPIC_API_KEY" \
            -H "anthropic-version: 2023-06-01" \
            -H "content-type: application/json" \
            -d "{
              \"model\": \"claude-sonnet-4-6\",
              \"max_tokens\": 4096,
              \"messages\": [{
                \"role\": \"user\",
                \"content\": \"请审查以下 PR 的代码变更，按【必须修改】【建议修改】【优点】三部分输出。\\n\\n${DIFF}\"
              }]
            }" | jq -r '.content[0].text')

          echo "## Claude 代码审查结果" >> $GITHUB_STEP_SUMMARY
          echo "$REVIEW" >> $GITHUB_STEP_SUMMARY

  # ===== 代码质量检查 =====
  quality-check:
    name: 代码质量检查
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v4
        with:
          python-version: '3.11'
      - run: pip install black ruff pytest pytest-cov
      - run: black --check .
      - run: ruff check .
      - run: pytest --cov --cov-report=xml

  # ===== 安全扫描 =====
  security-scan:
    name: 安全扫描
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: 扫描硬编码密钥
        run: |
          # 检查是否有 API Key 泄露
          if grep -rE "sk-ant-api[0-9]{2}-[a-zA-Z0-9_-]{20,}" --include="*.py" --include="*.js" --include="*.ts" .; then
            echo "::error::发现硬编码的 API Key！"
            exit 1
          fi

      - name: 依赖漏洞扫描
        run: |
          pip install safety
          safety check --full-report || true
```

------

## 6. 团队监控与跨团队协作

### 6.1 Claude 使用情况监控

跟踪团队成员的 Claude API 调用和成本，避免失控：

```python
#!/usr/bin/env python3
"""Claude 使用情况监控脚本"""

import sqlite3
from datetime import datetime, timedelta

# 模型定价（每 1M tokens）
MODEL_PRICING = {
    "claude-haiku-4-5-20251001":  {"input": 0.80,  "output": 4.00},
    "claude-sonnet-4-6":         {"input": 3.00,  "output": 15.00},
    "claude-opus-4-6":           {"input": 15.00, "output": 75.00},
}

def log_api_call(user, model, prompt_tokens, completion_tokens):
    """记录一次 API 调用"""
    pricing = MODEL_PRICING.get(model, MODEL_PRICING["claude-sonnet-4-6"])
    cost = (prompt_tokens * pricing["input"] + completion_tokens * pricing["output"]) / 1_000_000
    # 存储到 SQLite / 发送到监控平台
    print(f"[{user}] {model} | tokens: {prompt_tokens}+{completion_tokens} | cost: ${cost:.4f}")

def generate_weekly_report():
    """生成周度使用报告"""
    # 统计：总调用次数、总成本、按用户拆分、按模型拆分
    # 输出 Markdown 表格 → 发送到 Slack/飞书
    pass
```

> 凯神建议：用 Haiku 做日常编码辅助（成本最低），Sonnet 做代码审查，Opus 只在复杂架构设计时使用。严格按模型分级能省 60%+ 成本。

### 6.2 多团队共享配置

大公司多团队使用 Claude Code 时，用**配置继承**避免重复：

```nix
company-claude-config/           # 公司级配置（基础）
├── .editorconfig
├── claude/
│   └── skills/
│       └── company-standards/   # 公司编码标准（全员遵守）
│
team-frontend-config/            # 前端团队配置（继承 + 扩展）
├── 继承: company-claude-config
└── claude/
    └── skills/
        └── react-patterns/      # React 专用模式
│
team-backend-config/             # 后端团队配置（继承 + 扩展）
├── 继承: company-claude-config
└── claude/
    └── skills/
        └── api-patterns/        # API 专用模式
```

核心思路：公司级定「红线」（安全规范、代码风格底线），团队级加「特色」（技术栈相关的最佳实践）。

------

## 7. API Key 安全管理

**这是本章最重要的部分，凯神必须拿出来单独重点讲。**

**API Key 全生命周期管理流程**：

![image-20260524123002753](/Users/book/Library/Application Support/typora-user-images/image-20260524123002753.png)

<svg id="bytemd-mermaid-1779586117987-2" width="100%" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="max-width: 463.5px;" viewBox="-8 -8 463.5 1558" role="graphics-document document" aria-roledescription="flowchart-v2"><g><marker id="bytemd-mermaid-1779586117987-2_flowchart-pointEnd" class="marker flowchart" viewBox="0 0 10 10" refX="6" refY="5" markerUnits="userSpaceOnUse" markerWidth="12" markerHeight="12" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker><marker id="bytemd-mermaid-1779586117987-2_flowchart-pointStart" class="marker flowchart" viewBox="0 0 10 10" refX="4.5" refY="5" markerUnits="userSpaceOnUse" markerWidth="12" markerHeight="12" orient="auto"><path d="M 0 5 L 10 10 L 10 0 z" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker><marker id="bytemd-mermaid-1779586117987-2_flowchart-circleEnd" class="marker flowchart" viewBox="0 0 10 10" refX="11" refY="5" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><circle cx="5" cy="5" r="5" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></circle></marker><marker id="bytemd-mermaid-1779586117987-2_flowchart-circleStart" class="marker flowchart" viewBox="0 0 10 10" refX="-1" refY="5" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><circle cx="5" cy="5" r="5" class="arrowMarkerPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></circle></marker><marker id="bytemd-mermaid-1779586117987-2_flowchart-crossEnd" class="marker cross flowchart" viewBox="0 0 11 11" refX="12" refY="5.2" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><path d="M 1,1 l 9,9 M 10,1 l -9,9" class="arrowMarkerPath" style="stroke-width: 2; stroke-dasharray: 1, 0;"></path></marker><marker id="bytemd-mermaid-1779586117987-2_flowchart-crossStart" class="marker cross flowchart" viewBox="0 0 11 11" refX="-1" refY="5.2" markerUnits="userSpaceOnUse" markerWidth="11" markerHeight="11" orient="auto"><path d="M 1,1 l 9,9 M 10,1 l -9,9" class="arrowMarkerPath" style="stroke-width: 2; stroke-dasharray: 1, 0;"></path></marker><g class="root"><g class="clusters"></g><g class="edgePaths"><path d="M168.5,43L168.5,49.5C168.5,56,168.5,69,168.5,81.117C168.5,93.233,168.5,104.467,168.5,110.083L168.5,115.7" id="L-A-B-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-A LE-B" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M168.5,164L168.5,170.5C168.5,177,168.5,190,168.5,202.117C168.5,214.233,168.5,225.467,168.5,231.083L168.5,236.7" id="L-B-C-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-B LE-C" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M116.109,307.757L103.341,315.131C90.573,322.504,65.036,337.252,52.268,350.243C39.5,363.233,39.5,374.467,39.5,380.083L39.5,385.7" id="L-C-D-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-C LE-D" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M181.128,313L183.44,319.5C185.752,326,190.376,339,192.688,351.117C195,363.233,195,374.467,195,380.083L195,385.7" id="L-C-E-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-C LE-E" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M220.891,302.6L238.076,310.834C255.26,319.067,289.63,335.533,306.815,349.383C324,363.233,324,374.467,324,380.083L324,385.7" id="L-C-F-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-C LE-F" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M39.5,462L39.5,468.5C39.5,475,39.5,488,39.5,502.45C39.5,516.9,39.5,532.8,39.5,540.75L39.5,548.7" id="L-D-G-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-D LE-G" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M195,462L195,468.5C195,475,195,488,195,500.117C195,512.233,195,523.467,195,529.083L195,534.7" id="L-E-H-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-E LE-H" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M324,462L324,468.5C324,475,324,488,324,502.45C324,516.9,324,532.8,324,540.75L324,548.7" id="L-F-I-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-F LE-I" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M39.5,597L39.5,605.833C39.5,614.667,39.5,632.333,39.5,649.117C39.5,665.9,39.5,681.8,39.5,689.75L39.5,697.7" id="L-G-J-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-G LE-J" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M182.372,611L180.06,617.5C177.748,624,173.124,637,170.812,651.45C168.5,665.9,168.5,681.8,168.5,689.75L168.5,697.7" id="L-H-K-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-H LE-K" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M316.352,597L313.21,605.833C310.068,614.667,303.784,632.333,300.642,646.783C297.5,661.233,297.5,672.467,297.5,678.083L297.5,683.7" id="L-I-L-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-I LE-L" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M39.5,746L39.5,754.833C39.5,763.667,39.5,781.333,47.034,796.119C54.568,810.905,69.637,822.81,77.171,828.762L84.705,834.714" id="L-J-M-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-J LE-M" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M168.5,746L168.5,754.833C168.5,763.667,168.5,781.333,165.845,795.866C163.19,810.399,157.881,821.797,155.226,827.496L152.571,833.196" id="L-K-M-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-K LE-M" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M297.5,760L297.5,766.5C297.5,773,297.5,786,280.27,800.341C263.04,814.682,228.581,830.365,211.351,838.206L194.121,846.047" id="L-L-M-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-L LE-M" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M133.797,909L133.797,915.5C133.797,922,133.797,935,133.797,947.117C133.797,959.233,133.797,970.467,133.797,976.083L133.797,981.7" id="L-M-N-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-M LE-N" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M133.797,1030L133.797,1036.5C133.797,1043,133.797,1056,133.797,1068.117C133.797,1080.233,133.797,1091.467,133.797,1097.083L133.797,1102.7" id="L-N-O-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-N LE-O" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M133.797,1179L133.797,1185.5C133.797,1192,133.797,1205,144.123,1217.553C154.449,1230.107,175.1,1242.213,185.426,1248.266L195.752,1254.32" id="L-O-P-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-O LE-P" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M237,1300L237,1306.5C237,1313,237,1326,237,1338.117C237,1350.233,237,1361.467,237,1367.083L237,1372.7" id="L-P-Q-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-P LE-Q" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M234.5,589.316L263.417,599.43C292.333,609.544,350.167,629.772,379.083,652.303C408,674.833,408,699.667,408,724.5C408,749.333,408,774.167,408,799C408,823.833,408,848.667,408,873.5C408,898.333,408,923.167,408,941.2C408,959.233,408,970.467,408,976.083L408,981.7" id="L-H-R-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-H LE-R" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M408,1030L408,1036.5C408,1043,408,1056,408,1070.45C408,1084.9,408,1100.8,408,1108.75L408,1116.7" id="L-R-S-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-R LE-S" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M408,1165L408,1173.833C408,1182.667,408,1200.333,388.249,1216.154C368.499,1231.976,328.998,1245.951,309.247,1252.939L289.496,1259.927" id="L-S-P-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-S LE-P" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path><path d="M237,1421L237,1427.5C237,1434,237,1447,237,1459.117C237,1471.233,237,1482.467,237,1488.083L237,1493.7" id="L-Q-T-0" class="edge-thickness-normal edge-pattern-solid flowchart-link LS-Q LE-T" style="fill:none;" marker-end="url(#bytemd-mermaid-1779586117987-2_flowchart-pointEnd)"></path></g><g class="edgeLabels"><g class="edgeLabel" transform="translate(168.5, 82)"><g class="label" transform="translate(-16, -14)"><foreignObject width="32" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">申请</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(168.5, 203)"><g class="label" transform="translate(-16, -14)"><foreignObject width="32" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">创建</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(39.5, 352)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">分配环境</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(195, 352)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">分配环境</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(324, 352)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">分配环境</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(39.5, 501)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">权限级别</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(195, 501)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">权限级别</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(324, 501)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">权限级别</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(39.5, 650)"><g class="label" transform="translate(-24, -14)"><foreignObject width="48" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">有效期</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(168.5, 650)"><g class="label" transform="translate(-24, -14)"><foreignObject width="48" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">有效期</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(297.5, 650)"><g class="label" transform="translate(-24, -14)"><foreignObject width="48" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">有效期</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(39.5, 799)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">自动提醒</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(168.5, 799)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">自动提醒</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(297.5, 799)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">定期审查</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(133.796875, 948)"><g class="label" transform="translate(-16, -14)"><foreignObject width="32" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">轮换</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(133.796875, 1069)"><g class="label" transform="translate(-24, -14)"><foreignObject width="48" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">过渡期</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(133.796875, 1218)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">验证就绪</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(237, 1339)"><g class="label" transform="translate(-16, -14)"><foreignObject width="32" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">记录</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(408, 799)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">泄露风险</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(408, 1069)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">应急响应</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(408, 1218)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">加急轮换</span></div></foreignObject></g></g><g class="edgeLabel" transform="translate(237, 1460)"><g class="label" transform="translate(-32, -14)"><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="edgeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51); background-color: rgb(232, 232, 232); text-align: center;">月度审计</span></div></foreignObject></g></g></g><g class="nodes"><g class="node default default flowchart-label" id="flowchart-A-452" data-node="true" data-id="A" transform="translate(168.5, 21.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-60.390625" y="-21.5" width="120.78125" height="43"></rect><g class="label" style="" transform="translate(-52.890625, -14)"><rect></rect><foreignObject width="105.78125" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">需要新 API Key</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-B-453" data-node="true" data-id="B" transform="translate(168.5, 142.5)"><rect class="basic label-container" style="fill:#3b82f6;" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">审批流程</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-C-455" data-node="true" data-id="C" transform="translate(168.5, 277.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-52.390625" y="-35.5" width="104.78125" height="71"></rect><g class="label" style="" transform="translate(-44.890625, -28)"><rect></rect><foreignObject width="89.78125" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">生成 API Key<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">添加元数据</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-D-457" data-node="true" data-id="D" transform="translate(39.5, 426.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-35.5" width="79" height="71"></rect><g class="label" style="" transform="translate(-32, -28)"><rect></rect><foreignObject width="64" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">开发环境<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">DEV</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-E-459" data-node="true" data-id="E" transform="translate(195, 426.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-35.5" width="79" height="71"></rect><g class="label" style="" transform="translate(-32, -28)"><rect></rect><foreignObject width="64" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">生产环境<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">PROD</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-F-461" data-node="true" data-id="F" transform="translate(324, 426.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-35.5" width="79" height="71"></rect><g class="label" style="" transform="translate(-32, -28)"><rect></rect><foreignObject width="64" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">审计环境<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">AUDIT</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-G-463" data-node="true" data-id="G" transform="translate(39.5, 575.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">仅读权限</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-H-465" data-node="true" data-id="H" transform="translate(195, 575.5)"><rect class="basic label-container" style="fill:#f59e0b;" rx="0" ry="0" x="-39.5" y="-35.5" width="79" height="71"></rect><g class="label" style="" transform="translate(-32, -28)"><rect></rect><foreignObject width="64" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">读写权限<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">受限制</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-I-467" data-node="true" data-id="I" transform="translate(324, 575.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">只读权限</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-J-469" data-node="true" data-id="J" transform="translate(39.5, 724.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-26.30078125" y="-21.5" width="52.6015625" height="43"></rect><g class="label" style="" transform="translate(-18.80078125, -14)"><rect></rect><foreignObject width="37.6015625" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">90 天</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-K-471" data-node="true" data-id="K" transform="translate(168.5, 724.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-26.30078125" y="-21.5" width="52.6015625" height="43"></rect><g class="label" style="" transform="translate(-18.80078125, -14)"><rect></rect><foreignObject width="37.6015625" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">30 天</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-L-473" data-node="true" data-id="L" transform="translate(297.5, 724.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-46.10546875" y="-35.5" width="92.2109375" height="71"></rect><g class="label" style="" transform="translate(-38.60546875, -28)"><rect></rect><foreignObject width="77.2109375" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">永久<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">+ 访问日志</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-M-475" data-node="true" data-id="M" transform="translate(133.796875, 873.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-55.5" y="-35.5" width="111" height="71"></rect><g class="label" style="" transform="translate(-48, -28)"><rect></rect><foreignObject width="96" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">30天前通知<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">密钥即将过期</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-N-481" data-node="true" data-id="N" transform="translate(133.796875, 1008.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-47.5" y="-21.5" width="95" height="43"></rect><g class="label" style="" transform="translate(-40, -14)"><rect></rect><foreignObject width="80" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">生成新密钥</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-O-483" data-node="true" data-id="O" transform="translate(133.796875, 1143.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-35.5" width="79" height="71"></rect><g class="label" style="" transform="translate(-32, -28)"><rect></rect><foreignObject width="64" height="56"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">新旧密钥<br style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px;">并行使用</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-P-485" data-node="true" data-id="P" transform="translate(237, 1278.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-47.5" y="-21.5" width="95" height="43"></rect><g class="label" style="" transform="translate(-40, -14)"><rect></rect><foreignObject width="80" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">撤销旧密钥</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-Q-487" data-node="true" data-id="Q" transform="translate(237, 1399.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">审计日志</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-R-489" data-node="true" data-id="R" transform="translate(408, 1008.5)"><rect class="basic label-container" style="fill:#ef4444;" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">立即撤销</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-S-491" data-node="true" data-id="S" transform="translate(408, 1143.5)"><rect class="basic label-container" style="" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">发送告警</span></div></foreignObject></g></g><g class="node default default flowchart-label" id="flowchart-T-495" data-node="true" data-id="T" transform="translate(237, 1520.5)"><rect class="basic label-container" style="fill:#10b981;" rx="0" ry="0" x="-39.5" y="-21.5" width="79" height="43"></rect><g class="label" style="" transform="translate(-32, -14)"><rect></rect><foreignObject width="64" height="28"><div xmlns="http://www.w3.org/1999/xhtml" bis_skin_checked="1" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; display: inline-block; white-space: nowrap;"><span class="nodeLabel" style="--tw-border-spacing-x: 0; --tw-border-spacing-y: 0; --tw-translate-x: 0; --tw-translate-y: 0; --tw-rotate: 0; --tw-skew-x: 0; --tw-skew-y: 0; --tw-scale-x: 1; --tw-scale-y: 1; --tw-pan-x: ; --tw-pan-y: ; --tw-pinch-zoom: ; --tw-scroll-snap-strictness: proximity; --tw-gradient-from-position: ; --tw-gradient-via-position: ; --tw-gradient-to-position: ; --tw-ordinal: ; --tw-slashed-zero: ; --tw-numeric-figure: ; --tw-numeric-spacing: ; --tw-numeric-fraction: ; --tw-ring-inset: ; --tw-ring-offset-width: 0px; --tw-ring-offset-color: #fff; --tw-ring-color: rgba(59,130,246,.5); --tw-ring-offset-shadow: 0 0 #0000; --tw-ring-shadow: 0 0 #0000; --tw-shadow: 0 0 #0000; --tw-shadow-colored: 0 0 #0000; --tw-blur: ; --tw-brightness: ; --tw-contrast: ; --tw-grayscale: ; --tw-hue-rotate: ; --tw-invert: ; --tw-saturate: ; --tw-sepia: ; --tw-drop-shadow: ; --tw-backdrop-blur: ; --tw-backdrop-brightness: ; --tw-backdrop-contrast: ; --tw-backdrop-grayscale: ; --tw-backdrop-hue-rotate: ; --tw-backdrop-invert: ; --tw-backdrop-opacity: ; --tw-backdrop-saturate: ; --tw-backdrop-sepia: ; --tw-contain-size: ; --tw-contain-layout: ; --tw-contain-paint: ; --tw-contain-style: ; box-sizing: border-box; border: 0px solid rgb(240, 241, 242); scrollbar-color: auto; scrollbar-width: auto; outline: transparent solid 2px; outline-offset: 2px; line-height: 1.75; fill: rgb(51, 51, 51); color: rgb(51, 51, 51);">合规报告</span></div></foreignObject></g></g></g></g></g></svg>

### 7.1 泄露的灾难后果

真实安全事故，每一个都是血的教训：

| 事故                           | 后果                        | 损失         |
| ------------------------------ | --------------------------- | ------------ |
| API Key 提交到 GitHub 公开仓库 | 被扫描器 5 分钟内发现并盗刷 | **$15,000**  |
| 硬编码在前端代码里             | 暴露给所有用户              | 无限额度滥用 |
| 明文存储在配置文件             | 服务器被入侵后泄露          | **$8,000**   |
| 共享给离职员工未回收           | 前员工恶意使用              | 法律诉讼     |
| 未设置使用限制                 | 被 DDoS 攻击刷量            | **$25,000**  |

> 凯神说句掏心窝的话：以上每一条都是真实发生过的。一次泄露可能让你公司赔到肉疼。

### 7.2 密钥分级管理

企业必须按环境分级管理密钥：

```gauss
Production Keys (生产环境)
├── Master Key (主密钥)          # 最高权限，仅 CEO/CTO 持有
│   ├── 用途：密钥轮换、紧急恢复
│   └── 访问：2FA + 硬件密钥
├── Service Keys (服务密钥)      # 各服务独立密钥
│   ├── API Gateway Key          # 限制：10,000 RPM
│   ├── Backend Service Key      # 限制：5,000 RPM
│   └── Batch Job Key            # 限制：100 RPM
└── Developer Keys (开发密钥)    # 开发/测试环境
    ├── Dev Environment          # 限制：100 RPM
    └── Test Environment         # 限制：50 RPM

Staging Keys (预发布环境)
└── 独立密钥，与生产完全隔离

Development Keys (开发环境)
└── 团队共享，每周轮换
```

### 7.3 密钥存储方案对比

**绝对禁止的做法（凯神看到就想打人）：**

```python
# ❌ 硬编码（等着被扫描器抓）
ANTHROPIC_API_KEY = "sk-ant-api03-XXXXXXXX"

# ❌ 提交到 Git（.env 未加入 .gitignore）
# ❌ 明文配置文件
api_key: "sk-ant-api03-XXXXXXXX"

# ❌ 写在前端代码里（暴露给全世界）
const API_KEY = "sk-ant-api03-XXXXXXXX";
```

**正确的企业级做法：**

```python
# ✅ 方案 1：AWS Secrets Manager
import boto3

def get_api_key() -> str:
    """从 AWS Secrets Manager 获取 API Key"""
    client = boto3.client('secretsmanager', region_name='us-east-1')
    response = client.get_secret_value(SecretId='prod/anthropic/api-key')
    return response['SecretString']

# ✅ 方案 2：HashiCorp Vault
import hvac, os

def get_api_key_from_vault() -> str:
    """从 Vault 获取 API Key"""
    client = hvac.Client(url='https://vault.example.com:8200')
    client.auth.approle.login(
        role_id=os.getenv("VAULT_ROLE_ID"),
        secret_id=os.getenv("VAULT_SECRET_ID")
    )
    secret = client.secrets.kv.v2.read_secret_version(
        path='anthropic/api-key',
        mount_point='secret'
    )
    return secret['data']['data']['key']
```

三大方案对比：

| 方案                | 优点                | 缺点             | 适用场景   |
| ------------------- | ------------------- | ---------------- | ---------- |
| AWS Secrets Manager | 与 AWS 生态深度集成 | 仅限 AWS         | AWS 用户   |
| HashiCorp Vault     | 跨平台、功能强大    | 需要额外部署维护 | 多云环境   |
| Azure Key Vault     | 与 Azure 集成良好   | 仅限 Azure       | Azure 用户 |

> 凯神建议：中小团队用环境变量 + `.env`（确保加入 `.gitignore`）就够了；中大型企业必须上 Secrets Manager 或 Vault。

### 7.4 密钥轮换自动化

密钥不是配一次就完事了，必须定期轮换：

```markdown
检查密钥过期（90 天周期）
         ↓
  生成新密钥
         ↓
  存储到 Vault（备份旧密钥）
         ↓
  更新所有服务（滚动更新）
         ↓
  等待 5 分钟观察
         ↓
     验证新密钥
    ↙         ↘
成功             失败
 ↓                ↓
撤销旧密钥      回滚到旧密钥
通知成功        告警通知
```

| 项目     | 建议值                               |
| -------- | ------------------------------------ |
| 轮换周期 | 生产密钥 90 天，开发密钥 30 天       |
| 回滚窗口 | 旧密钥保留 24 小时后撤销             |
| 通知渠道 | Slack/飞书 + 邮件                    |
| 审计日志 | 记录每次轮换操作的时间、操作人、结果 |

------

## 8. 敏感数据保护

### 8.1 Git Secrets 扫描

在 `pre-commit` 里加上敏感信息正则扫描，防止密钥意外提交：

```bash
#!/bin/bash
# 敏感信息扫描 - 集成到 pre-commit hook

# 定义敏感信息正则表达式
declare -A PATTERNS=(
    ["anthropic_api_key"]='sk-ant-api[0-9]{2}-[a-zA-Z0-9_-]{20,}'
    ["aws_access_key"]='AKIA[0-9A-Z]{16}'
    ["aws_secret_key"]='[0-9a-zA-Z/+=]{40}'
    ["openai_api_key"]='sk-[a-zA-Z0-9]{48}'
    ["github_token"]='ghp_[a-zA-Z0-9]{36}'
    ["private_key"]='-----BEGIN (RSA |EC |OPENSSH )?PRIVATE KEY-----'
    ["password_assignment"]='password\s*[=:]\s*['"'"'"][^'"'"'"]{8,}['"'"'"]'
)

STAGED_FILES=$(git diff --cached --name-only)
FOUND_SECRETS=0

for file in $STAGED_FILES; do
    for pattern_name in "${!PATTERNS[@]}"; do
        if grep -qE "${PATTERNS[$pattern_name]}" "$file" 2>/dev/null; then
            echo "[ERROR] 在 $file 中发现疑似 $pattern_name"
            FOUND_SECRETS=1
        fi
    done
done

if [[ $FOUND_SECRETS -eq 1 ]]; then
    echo "[ERROR] 发现敏感信息！提交被拒绝。"
    echo "[ERROR] 请将敏感信息移至环境变量或 Secrets Manager。"
    exit 1
fi
```

### 8.2 日志脱敏

生产环境日志必须自动脱敏，防止敏感信息泄露到日志系统：

```python
import re
import logging

class SensitiveDataFilter(logging.Filter):
    """日志脱敏过滤器"""

    PATTERNS = {
        "api_key":     (r'sk-ant-api\d{2}-\S{10,}', 'sk-ant-api**-*****'),
        "email":       (r'[\w.-]+@[\w.-]+\.\w+', '***@***.***'),
        "phone":       (r'\d{3}-\d{3,4}-\d{4}', '***-****-****'),
        "credit_card": (r'\d{4}[\s-]?\d{4}[\s-]?\d{4}[\s-]?\d{4}', '**** **** **** ****'),
    }

    def filter(self, record):
        msg = str(record.msg)
        for name, (pattern, replacement) in self.PATTERNS.items():
            msg = re.sub(pattern, replacement, msg)
        record.msg = msg
        return True

# 使用方式
logger = logging.getLogger()
logger.addFilter(SensitiveDataFilter())
```

------

## 9. 企业合规要求

### 9.1 GDPR 合规

如果你的业务涉及欧盟用户，必须满足 GDPR：

| 要求         | 说明                 | Claude Code 实现       |
| ------------ | -------------------- | ---------------------- |
| 数据最小化   | 仅收集必要数据       | 限制日志记录的个人信息 |
| 访问权       | 用户可请求访问其数据 | 提供数据导出 API       |
| 删除权       | 用户可请求删除数据   | 实现数据删除流程       |
| 数据可移植性 | 数据可导出           | 支持 JSON/CSV 格式导出 |
| 违规通知     | 72 小时内通知        | 自动化事故响应流程     |
| 数据保护官   | 指定 DPO             | 安全团队负责人         |

### 9.2 SOC 2 合规

SOC 2 审计关注五大信任原则：

| 原则                               | 含义           | 关键措施                     |
| ---------------------------------- | -------------- | ---------------------------- |
| 安全性（Security）                 | 防止未授权访问 | API Key 分级、2FA、最小权限  |
| 可用性（Availability）             | 系统正常运行   | 监控告警、故障切换、SLA      |
| 处理完整性（Processing Integrity） | 数据处理正确   | 审计日志、数据校验           |
| 机密性（Confidentiality）          | 敏感信息保密   | 加密传输、日志脱敏、密钥管理 |
| 隐私性（Privacy）                  | 个人信息保护   | GDPR 合规、数据生命周期管理  |

------

## 10. 安全审计与事故响应

### 10.1 综合安全扫描清单

定期执行以下安全扫描：

| #    | 扫描项           | 工具                                | 频率     |
| ---- | ---------------- | ----------------------------------- | -------- |
| 1    | Git Secrets 扫描 | git-secrets / pre-commit hook       | 每次提交 |
| 2    | 依赖漏洞扫描     | Safety（Python）/ npm audit（Node） | 每次 CI  |
| 3    | 代码安全扫描     | Bandit（Python）/ ESLint security   | 每次 CI  |
| 4    | 容器镜像扫描     | Trivy                               | 每次构建 |
| 5    | 配置文件安全检查 | 自定义脚本（检查 .env 权限等）      | 每日     |
| 6    | SSL/TLS 检查     | testssl.sh                          | 每周     |
| 7    | 密钥轮换检查     | 自动化脚本                          | 每月     |

### 10.2 API 泄露应急预案

**发现 API Key 泄露后的分钟级响应流程：**

```nix
API Key 泄露检测
         ↓
  [自动告警] → Slack / 飞书 / 邮件 / 短信
         ↓
  ┌─── 立即响应（5 分钟内）───┐
  │ 1. 撤销泄露的密钥          │
  │ 2. 生成新密钥              │
  │ 3. 更新所有受影响服务      │
  │ 4. 通知相关人员            │
  └────────────────────────────┘
         ↓
  ┌─── 调查分析（1 小时内）───┐
  │ 5. 分析泄露原因            │
  │ 6. 评估影响范围            │
  │ 7. 检查异常 API 使用       │
  │ 8. 记录审计日志            │
  └────────────────────────────┘
         ↓
  ┌─── 修复加固（24 小时内）──┐
  │ 9. 修复泄露源             │
  │ 10. 加强访问控制          │
  │ 11. 更新安全策略          │
  │ 12. 培训相关人员          │
  └───────────────────────────┘
         ↓
  ┌─── 复盘总结（72 小时内）──┐
  │ 13. 编写事故报告           │
  │ 14. 改进响应流程           │
  │ 15. 预防类似事故           │
  └────────────────────────────┘
```

> 凯神提醒：Anthropic Console 后台可以即时撤销密钥。发现泄露的第一秒就去撤销，不要犹豫。

------

## 11. 20 条安全黄金规则

凯神把企业安全浓缩成 20 条规则，按优先级排列，P0 是必须立即执行的：

| #    | 规则                           | 检查方法           | 优先级 |
| ---- | ------------------------------ | ------------------ | ------ |
| 1    | API Key **永远不硬编码**       | Git Secrets 扫描   | **P0** |
| 2    | 使用环境变量或 Secrets Manager | 代码审查           | **P0** |
| 3    | 每 90 天轮换一次密钥           | 自动化脚本         | **P0** |
| 4    | 限制 API 速率                  | 配置检查           | **P0** |
| 5    | 记录所有 API 访问              | 审计日志           | **P0** |
| 6    | 异常访问立即告警               | 监控系统           | **P0** |
| 7    | 敏感数据必须加密               | 数据审计           | P1     |
| 8    | 日志自动脱敏                   | 日志检查           | P1     |
| 9    | 定期安全扫描                   | CI/CD 集成         | P1     |
| 10   | 依赖漏洞检查                   | Safety / npm audit | P1     |
| 11   | 最小权限原则                   | 权限审计           | P1     |
| 12   | 多因素认证（2FA）              | 用户账户检查       | P1     |
| 13   | 网络隔离                       | 网络配置           | P2     |
| 14   | SSL/TLS 加密                   | SSL 检查           | P2     |
| 15   | 防火墙配置                     | 网络安全审计       | P2     |
| 16   | 备份与恢复                     | 备份测试           | P2     |
| 17   | 安全培训                       | 团队培训记录       | P2     |
| 18   | 事故响应预案                   | 演练测试           | P2     |
| 19   | 合规性审计                     | 定期审计           | P3     |
| 20   | 安全文档更新                   | 文档检查           | P3     |

> 凯神建议：先把 P0 的 6 条全部落地，再逐步推进 P1 和 P2。P0 没做好就上生产，等于裸奔。

------

## 12. 故障排查

| 问题                     | 可能原因                   | 解决方案                                     |
| ------------------------ | -------------------------- | -------------------------------------------- |
| 团队成员配置不一致       | 没用统一配置仓库，手动配置 | 建立配置仓库 + `install.sh` 一键安装         |
| `pre-commit` hook 没生效 | hook 文件没有执行权限      | `chmod +x .git/hooks/pre-commit`             |
| Claude 代码审查调用失败  | API Key 未设置或过期       | 检查 `ANTHROPIC_API_KEY` 环境变量            |
| CI 安全扫描误报          | 正则匹配到测试数据         | 在扫描脚本中排除 `tests/` 目录               |
| 密钥轮换后服务中断       | 新密钥未正确分发到所有服务 | 使用滚动更新 + 健康检查验证                  |
| 审计日志丢失             | 日志存储空间不足           | 配置日志轮转 + 归档到对象存储                |
| Secrets Manager 连接失败 | IAM 权限不足或网络不通     | 检查 IAM Policy 和 VPC 网络配置              |
| Git Secrets 扫描太慢     | 仓库文件太多               | 只扫描暂存文件（`--cached`），排除二进制文件 |

------

## 13. 总结

本章凯神带你走了一遍企业落地 Claude Code 的「深水区」：

**团队协作侧：**

| 主题               | 核心要点                                                |
| ------------------ | ------------------------------------------------------- |
| 团队配置统一化     | 配置仓库 + 一键安装 + 自动验证 + 版本回滚               |
| Git Hooks 深度集成 | pre-commit 自动格式化 + Claude 审查 + commit-msg 规范化 |
| 团队知识库         | Skills 沉淀编码标准 + ADR 记录技术决策                  |
| CI/CD 深度集成     | GitHub Actions + Claude API 自动审查 + 安全扫描         |
| 监控与跨团队协作   | 使用量追踪 + 成本控制 + 配置继承                        |

**安全合规侧：**

| 主题         | 核心要点                                     |
| ------------ | -------------------------------------------- |
| API Key 安全 | 分级管理 + Secrets Manager/Vault + 90 天轮换 |
| 敏感数据保护 | Git Secrets 扫描 + 日志脱敏                  |
| 企业合规     | GDPR 六大要求 + SOC 2 五大原则               |
| 安全审计     | 7 项定期扫描 + API 泄露应急预案              |
| 安全规则     | 20 条黄金规则，P0 必须立即执行               |

**记住凯神这三条铁律：**

1. **Never trust, always verify** —— 零信任原则
2. **Defense in depth** —— 纵深防御
3. **Fail securely** —— 安全失败

