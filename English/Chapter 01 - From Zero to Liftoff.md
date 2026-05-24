# Chapter 1: From Zero to Liftoff — Get AI Writing Code for You in 10 Minutes

## 1. Preface

Claude Code is Anthropic's revolutionary AI coding assistant. It is not a simple autocomplete tool — it is a "coding partner" that understands your intent, thinks proactively, and takes action.

Unlike traditional AI tools, **Claude Code runs directly in the terminal**. It can read and write files, run commands, and analyze code — putting plain-language requests into real results.

This chapter walks through practical scenarios so you can master the core usage of Claude Code quickly.

**Who this is for:** frontend/backend developers, technical writers, code reviewers, and anyone who wants to ship faster with AI assistance.

## 2. Quick Start: Using Claude Code for the First Time

### 2.1 Environment Setup (do this first)

Before installing Claude Code, make sure your system meets the following prerequisites.

#### 2.1.1 Install Git (required)

Download: [git-scm.com](https://git-scm.com/downloads). Use the default installation steps.

**Important configuration:** set the environment variable `CLAUDE_CODE_GIT_BASH_PATH`.

```bash
D:\Program Files\Git\bin\bash.exe
```

(Adjust the path to match your Git installation.)

**Verify installation:**

```bash
git --version
```

#### 2.1.2 Install Node.js (required)

Download: [nodejs.org](https://nodejs.org/). Install Node.js 18 or higher (24.14.0 recommended).

**Verify installation:**

```bash
node -v
npm -v
```

![Node version check](../images/sbF8uf1Y6aaRQ5tG.webp)

![npm version check](../images/3g5gKTh737r3gxFS.png)

#### 2.1.3 Get an API Key

Claude Code requires either an official account login or an API key. You have two options.

An API key is a string starting with `sk-ant-`, for example:

```
sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Official channel:**

1. Visit [Anthropic Console](https://console.anthropic.com/settings/keys).
2. Register an account using one of:
   - Google sign-in (recommended, fastest)
   - Email + password
   - GitHub sign-in
3. Create a new key on the **API Keys** page.
4. Copy and store it somewhere safe — it is only shown once.

### 2.2 Install Claude Code

#### 2.2.1 Option A: Official Install (recommended)

**Step 1: Install Claude Code.** Reference the official quickstart: [Quickstart — Claude Code Docs](https://code.claude.com/docs/en/quickstart#native-install-recommended).

Pick the install script for your system:

| System              | Install command                                                              |
| ------------------- | ---------------------------------------------------------------------------- |
| macOS / Linux / WSL | `curl -fsSL https://claude.ai/install.sh \| bash`                            |
| Windows PowerShell  | `irm https://claude.ai/install.ps1 \| iex`                                   |
| Windows CMD         | `curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd` |

The official installer updates automatically, keeping you on the latest version.

**Step 2: Sign in.**

Launch Claude Code and log in:

```bash
claude
# First run will prompt for login
/login
# Follow the prompts to complete sign-in
```

**Supported account types:**

- Claude Pro, Max, Teams, Enterprise (recommended)
- Claude Console (API access; requires prepaid credits)
- Amazon Bedrock, Google Vertex AI, Microsoft Foundry (enterprise cloud services)

Credentials are saved automatically after sign-in. Use `/login` again to switch accounts.

#### 2.2.2 Option B: IDE Extensions (VS Code / Cursor / IntelliJ IDEA)

In addition to the terminal CLI, you can use Claude Code inside your editor via extensions for a visual, deeply integrated experience.

**VS Code (official extension)**

1. Press `Ctrl/Cmd + Shift + X` to open the Extensions marketplace.
2. Search `Claude Code`, find the Anthropic-published extension, and click Install.
3. After installation, a spark icon appears in the activity bar — click it to open the Claude Code panel.

What the extension adds over the terminal CLI:

| Feature              | Description                                          |
| -------------------- | ---------------------------------------------------- |
| Sidebar panel        | Code and conversation are separated, no interference |
| Inline diff view     | Edits are highlighted in real time                   |
| Checkpoint rollback  | Press Esc twice to revert to the previous checkpoint |
| @mentions            | Smart references to files and functions              |

Reference: https://code.claude.com/docs/en/vs-code

**Cursor (manual VSIX install)**

Cursor is based on VS Code, but the Claude Code extension cannot auto-detect Cursor — you need to install it manually:

1. Download the VSIX of the Claude Code extension from the VS Code Marketplace.

2. Install it in Cursor:

   ```bash
   cursor --install-extension /path/to/claude-code.vsix
   ```

   Or drag the VSIX file directly onto Cursor's Extensions panel.

3. Restart Cursor. The Claude Code icon appears in the left sidebar on success.

Reference: https://www.cursor-ide.com/blog/claude-code-cursor-extension-guide

**IntelliJ IDEA (Claude Code GUI plugin)**

[Claude Code GUI](https://plugins.jetbrains.com/plugin/26200-claude-code-gui) is a 4.8-rated visual plugin on the JetBrains Marketplace that integrates both Claude Code and OpenAI Codex directly into IntelliJ IDEA.

1. Press `Ctrl/Cmd + ,` to open Settings → Plugins → Marketplace.
2. Search `Claude Code GUI` and click Install.
3. Restart IDEA. The Claude Code panel appears in the tool window on success.

![Claude Code GUI plugin in IntelliJ IDEA](../images/D3SHh5VkdJkq1bGA.png)

### 2.3 First Launch and Configuration

```bash
# Enter your project directory
cd ~/my-project

# Launch Claude Code
claude
```

Configure environment variables — one-time for the session, or system-wide:

| Environment        | Command to set a temporary env var | Scope                       |
| ------------------ | ---------------------------------- | --------------------------- |
| Linux/macOS shell  | `export NAME=value`                | Current terminal session    |
| Windows CMD        | `set "NAME=value"`                 | Current CMD window          |
| Windows PowerShell | `$env:NAME="value"`                | Current PowerShell session  |

```text
export ANTHROPIC_BASE_URL=http://xxx.xx
export ANTHROPIC_AUTH_TOKEN=API_Key
```

#### 2.3.1 Launch Options Quick Reference

Beyond running plain `claude`, you can control startup behavior with flags:

| Flag                                    | Effect                                       | Use case                                  |
| --------------------------------------- | -------------------------------------------- | ----------------------------------------- |
| `claude`                                | Default launch (asks for permission)         | Day-to-day use                            |
| `claude --dangerously-skip-permissions` | Skip all permission prompts                  | Trusted personal projects, fast iteration |
| `claude -p "your question"`             | Ask once and exit                            | Quick lookups, no conversation needed     |
| `claude --headless`                     | Non-interactive mode                         | Script automation                         |

**About `--dangerously-skip-permissions`**

This flag makes Claude Code skip every permission prompt and execute file edits, command runs, and other operations directly. Anthropic officially calls this **"Safe YOLO mode."**

The "dangerously" prefix is there because the AI might modify code incorrectly, delete files, or run unintended commands — and skipping confirmation means you have no chance to stop it.

| Scenario                                                | Recommended? |
| ------------------------------------------------------- | ------------ |
| Personal/learning projects with code already in Git     | Yes          |
| Read-only operations (queries, analysis)                | Yes          |
| Company projects, open-source projects                  | No           |
| First time using Claude Code                            | No           |
| Projects containing sensitive data                      | No           |

> **Beginner tip:** Don't add this flag for your first month. Letting the AI ask for permission on each action teaches you what it is doing and prevents accidental damage. Once you understand Claude Code's behavior patterns, you can consider using it in personal projects — but commit your code to Git first so you can always roll back.

#### 2.3.2 Configuration File Layout

Claude Code's configuration has two levels — **global** and **project** — and understanding the layout matters for later chapters (CLAUDE.md, Commands, Hooks, etc.):

```
~/.claude/                      ← Global config directory (shared by all projects)
├── config.json                 ← Global config file
├── auth-token.json             ← Auth token
├── trusted-directories.json    ← List of trusted directories
├── cache/                      ← Cache
└── logs/                       ← Logs

<project>/.claude/              ← Project-level config (applies only to this project)
├── config.json                 ← Project config (overrides global settings of the same name)
├── commands/                   ← Custom commands (covered in Chapter 3)
├── skills/                     ← Custom skills (covered in Chapter 5)
└── hooks/                      ← Custom hooks (covered in Chapter 4)
```

## 3. Core Command Cheat Sheet

### 3.1 High-Frequency Commands (worth memorizing)

| Command   | Function                       | Use case                                                  |
| --------- | ------------------------------ | --------------------------------------------------------- |
| /init     | Initialize project docs        | First time in a project — let the AI learn the structure  |
| /clear    | Clear conversation history     | Switching tasks; free up context and save tokens          |
| /compact  | Compact conversation history   | Long sessions — keep a summary and continue chatting      |
| /add-dir  | Add a working directory        | When you need to operate on multiple projects             |
| /export   | Export conversation transcript | Save important conversations                              |
| /model    | Switch AI model                | Switch to Opus or another model                           |
| /memory   | Edit memory file               | Customize the AI's long-term memory                       |
| /resume   | Resume last conversation       | Continue where you left off                               |

### 3.2 Shortcuts

| Action            | Key/Syntax                              | Description                              |
| ----------------- | --------------------------------------- | ---------------------------------------- |
| Reference a file  | `@filename`                             | Have the AI focus on a specific file     |
| Paste an image    | `Ctrl + V` / `Alt + V` (varies by term) | Send a screenshot for analysis           |
| Newline in input  | `Shift + Alt + Enter`                   | Multi-line input                         |
| Run a bash command | `!ls -l`                               | Execute a shell command directly         |
| History           | `↑` / `↓`                               | Cycle through previous inputs            |
| Interrupt         | `Esc`                                   | Stop the current operation               |

## 4. Summary

Claude Code's core strengths:

1. **Natural-language interaction** — no complex commands to memorize; speak plainly.
2. **Active execution** — not just suggestions, but real edits, real files, real commands.
3. **Context awareness** — understands your project structure and follows its conventions.
4. **Multi-modal** — handles images, analyzes screenshots.

**Remember:** Claude Code's biggest advantage is understanding natural language. State your need clearly, act as the commander, and let it do the work.
