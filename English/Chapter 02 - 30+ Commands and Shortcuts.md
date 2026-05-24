# Chapter 2: 30+ Commands and Shortcuts to Double Your Coding Efficiency

## 1. Glossary (read this first if you're new)

| Term              | Full name              | Plain meaning                                            | Everyday analogy                            |
| ----------------- | ---------------------- | -------------------------------------------------------- | ------------------------------------------- |
| CLI               | Command Line Interface | Operating the computer by typing                         | Texting someone instructions                |
| Interactive Mode  | Interactive Mode       | Continuous conversation with memory of context           | A phone call with several rounds of back-and-forth |
| REPL              | Read-Eval-Print-Loop   | Read input, evaluate, print result, repeat               | You speak, AI replies, repeat               |
| Print Mode        | Print Mode             | Outputs only the result, no extra formatting             | Just the answer, no chit-chat               |
| Slash Command     | Slash Commands         | Special commands starting with `/`                       | A shortcut trigger                          |
| Token             | -                      | The unit by which the AI bills text processing           | A taxi meter charges by distance; the AI charges by token |
| Checkpoint        | -                      | A saved state of code + conversation                     | A save file in a video game                 |
| Rewind            | -                      | Roll back to a previous checkpoint                       | Loading a save                              |
| Compact           | -                      | Compress conversation history to save tokens             | Tidying a room — toss the unimportant stuff |
| Extended Thinking | -                      | Extended-thinking mode for deeper analysis               | Showing your work, not just the answer      |
| MCP               | Model Context Protocol | Plugin system for connecting Claude to external tools    | Installing apps on a phone to add features  |

---

## 2. Your First Claude Code Session

> Prerequisite: complete the environment setup and installation in Chapter 1.

### 2.1 Launching and your first message

Open a terminal (Windows: `Win+R` → `powershell`; macOS: `Cmd+Space` → `Terminal`; Linux: `Ctrl+Alt+T`), then enter the project directory and launch:

```bash
cd ~/your/project/path    # No project yet? Try: mkdir test-claude && cd test-claude
claude
```

When you see the `You: █` cursor blinking, launch was successful. Try your first prompt:

```
You: Hello, please introduce yourself
```

Claude will reply with an introduction and a list of things it can do (write code, fix bugs, search files, and so on). Receiving a normal response means everything is working.

### 2.2 Verifying and exiting

**Quick verification** — have Claude create a file to confirm it can read and write:

```
You: Create a hello.py file that prints "Hello Claude Code"
```

Claude will ask for confirmation → press Enter → the file is created. Verify with `cat hello.py`.

**To exit:** type `/exit`, or press `Ctrl+D` (macOS/Linux) / `Ctrl+Z` then Enter (Windows).

### 2.3 Initializing a Project (highly recommended)

> ⚠️ **Important:** new projects must be initialized. Even more important: **rerun `/init` whenever the project changes significantly to refresh Claude's context.**

#### Why initialize?

Let Claude automatically learn the project structure, tech stack, coding conventions, and goals. From then on, every conversation benefits from that context.

#### Standard initialization

```bash
You: /init
```

This scans the project automatically, generates or updates `CLAUDE.md`, and feeds that context into every later conversation.

#### Reinitialize as the project evolves

Don't treat `/init` as a one-shot. Rerun it whenever the project changes:

| Scenario                                | Recommendation        |
| --------------------------------------- | --------------------- |
| 🆕 First time on a new project          | **Must** run `/init`  |
| 🔄 Adjusted the project layout          | Rerun `/init`         |
| 🏗️ Added a major new module             | Rerun `/init`         |
| 📝 Updated coding conventions           | Rerun `/init`         |
| 🛠️ Switched framework/tech stack        | Rerun `/init`         |
| 💻 Only changed code logic              | No `/init` needed     |

#### A typical workflow

```bash
# Day 1: initialize
You: /init  # First full scan

# Iterate, build the auth module
You: Implement user login

# Day 2: project update
You: /init  # Rescan, refresh context (added a new API service layer)

# Claude now knows the new API-layer conventions
You: Add data caching in the new API layer

# Day 3: conventions updated
You: /init  # Re-sync with the latest conventions

# AI generates code matching the new conventions
You: Refactor the auth module
```

#### Verifying initialization

```bash
You: /memory
# Inspect the generated CLAUDE.md to confirm project info loaded correctly
```

---

#### Screenshots

![Initialization screenshot 1](../images/8y3WWT7kxZ05rwLA.png)

![Initialization screenshot 2](../images/YQN5n0un2CnZtIhw.png)

![Initialization screenshot 3](../images/VDGeT31ElXoJ953W.png)

## 3. Interactive Mode and Launch Options

Interactive mode (REPL) is Claude Code's core flow: you speak, the AI replies, context is always kept, and the loop continues.

You can attach flags at launch to control behavior:

```bash
claude                                  # Default launch
claude --project /path/to/project       # Specify a project directory without cd-ing
```

| Option           | Short | Effect                       | Use case                          |
| ---------------- | ----- | ---------------------------- | --------------------------------- |
| `--verbose`      | —     | Show detailed logs           | Debugging                         |
| `--model <name>` | `-m`  | Specify the AI model         | Switch to a specific model        |
| `--continue`     | `-c`  | Resume the most recent session | Continue yesterday's work       |
| `--resume <id>`  | `-r`  | Resume a specific session    | Pick up a particular conversation |

> See Chapter 1 §2.3.1 for the other startup flags (`--dangerously-skip-permissions`, `-p`, `--headless`).

### 3.1 Three Operating Modes

Claude Code has three modes. **Cycle through them with `Shift + Tab`.** The current mode is displayed in the top-right status bar.

| Mode               | Status bar  | Behavior                                                                 | Best for                                                  |
| ------------------ | ----------- | ------------------------------------------------------------------------ | --------------------------------------------------------- |
| Default            | (no marker) | Each file edit and command run pauses for confirmation                   | Beginners, unfamiliar projects, sensitive operations      |
| Auto-edit          | `Auto-edit` | File reads/writes auto-confirmed; Bash commands still need confirmation  | Familiar projects, large refactors                        |
| Plan mode          | `Plan mode` | Claude only analyzes and plans, never executes — explains "what I'd do"  | Breaking down complex tasks; assess risk before executing |

**How to switch:**

- Keyboard: `Shift + Tab` (Default → Auto-edit → Plan mode → Default)
- Mouse: click the mode label at the bottom-left of the input box

> **Beginner advice:** stay in default mode at first and inspect each action before confirming. Once you're comfortable, switch to Auto-edit for speed. For complex tasks, start in Plan mode to clarify your approach before executing.

---

## 4. Input Tips

### 4.1 Shortcut Input Prefixes

| Prefix | Effect                                            | Example                       |
| ------ | ------------------------------------------------- | ----------------------------- |
| `#`    | Append content to the memory file (`CLAUDE.md`)   | `# This project uses TypeScript` |
| `@`    | File-path autocomplete; focuses the AI on a file  | `@src/app.js`                 |
| `!`    | Execute a Bash command directly                   | `!npm test`                   |

### 4.2 Multi-line Input

| Method                  | Shortcut          | Notes                          |
| ----------------------- | ----------------- | ------------------------------ |
| Backslash + Enter       | `\` + Enter       | Works in every terminal        |
| macOS default           | `Option + Enter`  | macOS Terminal                 |
| After terminal setup    | `Shift + Enter`   | Run `/terminal-setup` to enable |
| Control sequence        | `Ctrl + J`        | Newline character              |
| Direct paste            | Paste a code block | Multi-line is auto-detected   |

---

## 5. Conversation Management

| Command    | Effect          | What is kept            | Token savings | Best for                                              |
| ---------- | --------------- | ----------------------- | ------------- | ----------------------------------------------------- |
| `/clear`   | Wipe entirely   | Only `CLAUDE.md` config | 100%          | Switching to a completely new task                    |
| `/compact` | Compress history | A summary of key info   | 40–60%        | Same task, but responses are slowing; near token cap  |

> **Rule of thumb:** new task → `/clear`; feels slow → `/compact`.

---

## 6. Slash Command Reference

> Slash commands only work in interactive mode (after entering `claude`).

### 6.1 Command Cheat Sheet

**Basic control**

| Command    | Effect                          | Notes                                    |
| ---------- | ------------------------------- | ---------------------------------------- |
| `/help`    | Show all available commands     | Look up anything you've forgotten        |
| `/exit`    | Exit Claude Code                | `Ctrl+D` also works                      |
| `/clear`   | Clear conversation history      | `CLAUDE.md` config is preserved          |
| `/compact` | Compress conversation history   | Accepts hints: `/compact keep the DB discussion` |

**Context and cost**

| Command    | Effect                                          |
| ---------- | ----------------------------------------------- |
| `/context` | Visualize token usage (color progress bar)      |
| `/cost`    | Show current session token usage and price      |
| `/usage`   | Show overall account usage and limits (subscribers) |

**Models and sessions**

| Command   | Effect              | Notes                                         |
| --------- | ------------------- | --------------------------------------------- |
| `/model`  | Switch AI model     | Or direct: `/model claude-opus-4-5-20251101`  |
| `/resume` | Resume a session    | Lists recent sessions to pick from            |
| `/export` | Export the transcript | Supports Markdown / JSON / HTML             |
| `/rename` | Rename current session | Easier to find later                       |

**Project configuration**

| Command        | Effect                                       |
| -------------- | -------------------------------------------- |
| `/init`        | Analyze the project and create `CLAUDE.md`   |
| `/memory`      | Open an editor to modify `CLAUDE.md`         |
| `/permissions` | View and modify Claude's permission settings |

**Development helpers**

| Command   | Effect                                |
| --------- | ------------------------------------- |
| `/review` | Review uncommitted code changes       |
| `/todos`  | List TODO items tracked in the chat   |
| `/agents` | Show the status of active sub-agents  |

**Diagnostics and status**

| Command   | Effect                                                   |
| --------- | -------------------------------------------------------- |
| `/doctor` | System health check (Node.js, API connection, MCP, etc.) |
| `/status` | Show version, model, account, and full status            |

**MCP and plugins**

| Command   | Effect                                  |
| --------- | --------------------------------------- |
| `/mcp`    | View and manage MCP server connections  |
| `/plugin` | Install, enable, or disable plugins     |
| `/hooks`  | Configure event-triggered automation    |

**Other**

| Command           | Effect                                          |
| ----------------- | ----------------------------------------------- |
| `/stats`          | Usage statistics (sessions, messages, costs)    |
| `/vim`            | Enable Vim-style editing in the input box       |
| `/release-notes`  | View the latest release notes                   |
| `/bug`            | File a bug report to Anthropic                  |
| `/terminal-setup` | Configure the terminal to support Shift+Enter   |

---

### 6.2 Context and Cost Management

`/context` displays a color progress bar showing token usage, so you know when it's time to `/compact`:

```
████████████░░░░░░░░  60% (120K / 200K tokens)
```

`/cost` shows the real cost of the current session — useful for pay-as-you-go users tracking spend.

### 6.3 Switching Models

```bash
/model                              # Interactive selection
/model claude-opus-4-5-20251101     # Pick one directly
```

Shortcut: `Option+P` on macOS / `Alt+P` on Windows.

| Model  | Speed   | Capability | Cost   | Best for                            |
| ------ | ------- | ---------- | ------ | ----------------------------------- |
| Haiku  | Fastest | Basic      | Lowest | Simple tasks, quick lookups         |
| Sonnet | Medium  | Strong     | Medium | Daily development (recommended)     |
| Opus   | Slowest | Strongest  | Highest | Complex tasks, critical decisions  |

### 6.4 Checkpoint and Rewind

Checkpoint = a game save. Rewind = loading the save. Claude Code creates a checkpoint automatically on every file modification, so you can experiment fearlessly.

**How to trigger:**

- Press `Esc` twice quickly (fastest)
- Type `/rewind`

**Three recovery options:**

| Option            | Effect                                                        | Use case                                                  |
| ----------------- | ------------------------------------------------------------- | --------------------------------------------------------- |
| Conversation only | Keep code changes, reset AI context                           | AI misunderstood, but the code came out right             |
| Code only         | Keep conversation, revert file changes                        | Code went wrong, but the discussion is still valuable     |
| Both              | Roll back both code and conversation to the earlier state     | Headed completely in the wrong direction — start fresh    |

> **Important limit:** checkpoints track only Claude's file-editing tools (Write, Edit) — they **do not** track Bash-driven changes like `!mv` or `!rm`. For important changes, have Claude use file tools, and pair it with Git.

### 6.5 Session Management

```bash
# Fast resume from the CLI
claude -c                    # Resume most recent session
claude -r ses_abc123         # Resume a specific session

# From inside interactive mode
/resume                      # List recent sessions to pick from
```

Export the conversation:

```
/export                      # Default Markdown
/export --clipboard          # Send to clipboard
/export --format json        # JSON format
```

Name a session for easier lookup later:

```
/rename auth-module-implementation
```

### 6.6 Project Configuration

- `/init` — auto-analyze the project structure and generate `CLAUDE.md` (see Chapter 1).
- `/memory` — open an editor to modify `CLAUDE.md`; you can also add memory with the `#` prefix.
- `/permissions` — view current permissions (file I/O, Bash commands, etc.) and adjust as needed.

### 6.7 Development Helpers

- `/review` — review uncommitted changes; Claude analyzes security issues, performance risks, and code style.
- `/todos` — list TODOs tracked in the conversation, with status.
- `/agents` — see active sub-agents (used during complex task decomposition).

### 6.8 Diagnostics and Status

Reach for these two when something goes wrong:

- `/doctor` — full health check (Node.js version, API connection, MCP status, etc.) — like a checkup.
- `/status` — current version, model, account, MCP connections, and other status info.

### 6.9 MCP and Plugins

- `/mcp` — view connected MCP servers and the tools they expose.
- `/plugin` — manage installed plugins (enable/disable).
- `/hooks` — view configured event hooks (e.g., auto-lint before write, notify on commit).

> MCP, Plugins, and Hooks are covered in detail in Chapters 4 and 6.

### 6.10 Other Commands

- `/stats` — usage habits (sessions, messages, cost trends).
- `/vim` — Vim-style editing in the input box (`h/j/k/l` to move, `i` to insert, `Esc` for normal mode).
- `/release-notes` — recent release notes.
- `/bug` — submit a bug report to Anthropic with a guided description.
- `/terminal-setup` — configure the terminal so Shift+Enter inserts a newline.

---

## 7. Shortcut Cheat Sheet

### 7.1 General Controls

| Shortcut                 | Effect                                  | Notes                                            |
| ------------------------ | --------------------------------------- | ------------------------------------------------ |
| `Ctrl + C`               | Cancel current input or stop generation | Standard interrupt signal                        |
| `Ctrl + D`               | Exit Claude Code                        | EOF signal                                       |
| `Ctrl + L`               | Clear the terminal screen               | Conversation history is unaffected               |
| `Ctrl + O`               | Toggle verbose output                   | Show/hide tool-call details                      |
| `Ctrl + R`               | Reverse history search                  | See §7.2                                         |
| `Esc + Esc`              | Open the Rewind menu                    | Roll back code/conversation (§6.4)               |
| `Tab`                    | Toggle Extended Thinking                | Turn extended thinking on/off                    |
| `Shift + Tab`            | Switch operating mode                   | Default / Auto-edit / Plan                       |
| `↑` / `↓`                | Browse input history                    | Quickly reuse previous prompts                   |
| `Option + P` / `Alt + P` | Switch model                            | Option on macOS, Alt on Windows/Linux            |
| `Ctrl + V` / `Alt + V`   | Paste an image                          | `Ctrl+V` on macOS/Linux, `Alt+V` on Windows      |

> Multi-line input shortcuts are listed in §4.2.

### 7.2 History Search (Ctrl+R)

1. Press `Ctrl + R` to enter search mode.
2. Type a keyword to match history entries.
3. Press `Ctrl + R` again to browse earlier matches.
4. `Tab` or `Esc` accepts the current match; `Enter` runs it; `Ctrl + C` cancels.

### 7.3 Background Execution

| Action                             | How                                |
| ---------------------------------- | ---------------------------------- |
| Ask Claude to run in the background | Say "run in the background" in your prompt |
| Manually move to background        | `Ctrl + B`                         |
| tmux users                         | Press `Ctrl + B` twice             |

Good background candidates: build tools (Webpack, Vite), test runners (jest, pytest), dev servers.

### 7.4 Vim Mode

After `/vim`, the input box supports Vim-style editing:

| Action              | Keys              | Notes                                  |
| ------------------- | ----------------- | -------------------------------------- |
| Enter normal mode   | `Esc`             | Leave insert mode                      |
| Insert              | `i` / `a` / `o`   | Before cursor / after cursor / new line below |
| Move                | `h` `j` `k` `l`   | Left / down / up / right               |
| Move by word        | `w` / `b`         | Next word / previous word              |
| Start/end of line   | `0` / `$`         |                                        |
| Delete              | `x` / `dd` / `dw` | Char / whole line / word               |
| Replace whole line  | `cc`              | Clear current line and insert mode     |
| Repeat last action  | `.`               |                                        |

---

## 8. Best Practices

### 8.1 Daily Workflow

Recommended daily flow:

```bash
$ claude -c                          # 1. Resume yesterday's session
You: /status                         # 2. Check status
You: I want to finish the auth module today    # 3. Start working
You: /context                        # 4. Check token usage periodically
You: /compact                        # 5. Compact when usage exceeds 60%
You: /export ~/docs/auth.md          # 6. Export after completing a major feature
You: /rename auth-module-day2        # 7. Rename session before ending the day
```

### 8.2 Saving on Tokens

**Token optimization:**

| Tip                                                    | Savings |
| ------------------------------------------------------ | ------- |
| Turn off Extended Thinking for simple questions (`Tab`) | ~70%    |
| Use `/compact` regularly                               | 40–60%  |
| `/clear` once a task is done                           | 100%    |
| Use Sonnet instead of Opus                             | ~80%    |
| Describe requirements concisely; avoid redundancy      | ~30%    |

**Model selection strategy:**

```
Simple queries (function explanation, format conversion) → Haiku (cheapest)
Daily development (coding, refactoring, debugging)       → Sonnet (best value)
Critical decisions (architecture, deep analysis)         → Opus (strongest)
```

### 8.3 Configuring Aliases

**macOS / Linux** (add to `~/.bashrc` or `~/.zshrc`):

```bash
alias cc="claude --dangerously-skip-permissions"    # Fast launch
alias cr="claude -c"                                # Resume session
alias ccv="claude --verbose"                        # Debug mode
alias cco="claude --model claude-opus-4-5-20251101" # Use Opus
```

**Windows PowerShell** (add to `$PROFILE`):

```powershell
function cc { claude --dangerously-skip-permissions }
function cr { claude -c }
function ccv { claude --verbose }
```

### 8.4 Experiment Freely with Checkpoints

Checkpoints let you try aggressive approaches without fear:

```
You: Refactor this module with a new architecture    # Attempt A (auto-checkpoint)
[Esc + Esc → rewind]                                  # Not happy? Rewind.
You: Try a factory pattern                            # Attempt B
[Esc + Esc → rewind]                                  # Still not happy? Rewind.
You: Try strategy pattern                             # Attempt C, iterate until satisfied
```

### 8.5 Team Collaboration

**Share a conversation:**

```
/export --format html shared/auth-discussion.html
```

**Create reusable team commands:**

```bash
mkdir -p .claude/commands
echo "Review this code for security and performance issues:" > .claude/commands/security-review.md
```

After committing to Git, every teammate can trigger the same review with `/security-review`.

---

## Appendix: Full Cheat Sheet

**CLI launch options**

| Option                           | Short | Effect                       |
| -------------------------------- | ----- | ---------------------------- |
| `--version`                      | `-v`  | Show version                 |
| `--help`                         | `-h`  | Show help                    |
| `--print`                        | `-p`  | Print mode (answer then exit)|
| `--model <name>`                 | `-m`  | Specify model                |
| `--continue`                     | `-c`  | Resume most recent session   |
| `--resume <id>`                  | `-r`  | Resume specific session      |
| `--project <path>`               | —     | Specify project directory    |
| `--verbose`                      | —     | Verbose output               |
| `--dangerously-skip-permissions` | —     | Skip permission confirmations |

**Slash commands**

| Command    | Effect           |      | Command          | Effect            |
| ---------- | ---------------- | ---- | ---------------- | ----------------- |
| `/help`    | Show help        |      | `/init`          | Initialize project |
| `/exit`    | Exit             |      | `/memory`        | Edit memory       |
| `/clear`   | Clear chat       |      | `/permissions`   | Manage permissions |
| `/compact` | Compress chat    |      | `/review`        | Code review       |
| `/context` | View token usage |      | `/todos`         | View TODOs        |
| `/cost`    | View cost        |      | `/rewind`        | Rewind            |
| `/model`   | Switch model     |      | `/mcp`           | Manage MCP        |
| `/status`  | View status      |      | `/plugin`        | Manage plugins    |
| `/doctor`  | System diagnostics |    | `/hooks`         | Manage hooks      |
| `/resume`  | Resume session   |      | `/vim`           | Vim mode          |
| `/export`  | Export chat      |      | `/stats`         | Usage stats       |
| `/rename`  | Rename session   |      | `/usage`         | Usage             |
|            |                  |      | `/release-notes` | Release notes     |
|            |                  |      | `/bug`           | Report bug        |

**Shortcuts**

| Shortcut | Effect           |      | Shortcut       | Effect                       |
| -------- | ---------------- | ---- | -------------- | ---------------------------- |
| `Ctrl+C` | Cancel / interrupt |    | `Esc+Esc`      | Rewind menu                  |
| `Ctrl+D` | Exit             |      | `Tab`          | Toggle Extended Thinking     |
| `Ctrl+L` | Clear screen     |      | `Shift+Tab`    | Switch mode                  |
| `Ctrl+O` | Toggle verbose   |      | `Option/Alt+P` | Switch model                 |
| `Ctrl+R` | Search history   |      | `Ctrl/Alt+V`   | Paste image                  |
| `Ctrl+B` | Move to background |    | `↑` / `↓`      | Browse history               |

---

## Summary

This chapter covered:

1. **Interactive mode** — the REPL workflow at the heart of Claude Code.
2. **30+ slash commands** — from basic control to MCP management.
3. **Checkpoint/Rewind** — experiment freely, roll back at will.
4. **Shortcuts** — efficient control, background runs, Vim mode.
5. **Best practices** — token savings, alias configuration, team collaboration.
