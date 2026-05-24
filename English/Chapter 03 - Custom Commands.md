# Chapter 3: Goodbye Repeated Prompts — Custom Commands That Make AI Get You Instantly

## 1. Preface

After Chapters 1 and 2 you can launch Claude Code comfortably and use slash commands and shortcuts.

But you've probably hit the same pain point: **every time you ask Claude to do the same kind of task, you re-type a wall of instructions.**

Custom commands solve exactly that — **collapse a recurring prompt into a single word, configure once, benefit forever.**

---

## 2. What Commands Are

### 2.1 What is a Slash Command

A slash command is a Claude Code "shortcut" — type `/name` to trigger a preset action.

**How it works:** typing `/write AI tutorial` → finds `.claude/commands/write.md` → reads it as a prompt → substitutes `AI tutorial` into `$ARGUMENTS` → runs.

Core formula: **command name = file name (without `.md`)**, **arguments = `$ARGUMENTS`**.

### 2.2 The Three Types of Commands

| Type             | Location              | Scope                                              |
| ---------------- | --------------------- | -------------------------------------------------- |
| Built-in         | Inside the program (read-only) | All projects                              |
| Project-level    | `.claude/commands/`   | Current project only; commit to Git for the team   |
| User-level       | `~/.claude/commands/` | All projects; personal toolbox                     |

Rule of thumb: session management/diagnostics → built-in; project-specific workflow → project-level; cross-project utility → user-level.

### 2.3 Why Learn Commands

| Dimension      | Manual entry          | Using Commands                       |
| -------------- | --------------------- | ------------------------------------ |
| Efficiency     | Re-typed every time   | Configure once, reuse forever        |
| Consistency    | Easy to forget steps  | Standardized execution               |
| Reusability    | Trapped in chat logs  | Team sharing, version control        |

---

## 3. Create Your First Custom Command

**Step 1: create the directory**

```bash
# macOS / Linux
mkdir -p .claude/commands

# Windows PowerShell
New-Item -ItemType Directory -Path ".claude\commands" -Force
```

**Step 2: create the command file** at `.claude/commands/hello.md`

```markdown
# Greeting command

The person to greet is: $ARGUMENTS

If no name is provided, use "friend" as the default.
Greet them warmly and ask what you can help with today.
```

> Tip for beginners: just say to Claude Code, "Create the file `.claude/commands/hello.md` with this content..." and let it write the file for you.

**Step 3: test it**

```
claude
You: /hello Alice    → Hi Alice! ...
You: /hello          → Hi friend! ...
```

> **Tip:** type `/` then press `Tab` to list every available command.

---

## 4. Going Further with Custom Commands

### 4.1 Command File Structure

A command file has two parts: **YAML frontmatter** (machine-read) plus **Markdown body** (AI-read).

```markdown
---
description: Newsletter article authoring command
argument-hint: <topic keyword>
allowed-tools:
  - Read
  - Write
  - WebSearch
model: claude-sonnet-4-5-20250929
---

# Newsletter Article Authoring

You are a seasoned newsletter writing expert.
Topic: $ARGUMENTS

Requirements: down-to-earth · 1500-2000 words · hook line → core content → call to action
```

### 4.2 Scope and Precedence

**Precedence:** project-level > user-level > built-in (non-core)

> Core built-ins like `/clear`, `/help`, `/compact` are protected and cannot be overridden.

Subdirectories are supported, with `:` as the namespace separator:

```
.claude/commands/
├── write.md              # /write
├── dev/
│   └── code-review.md    # /dev:code-review
└── test/
    └── generate.md       # /test:generate
```

### 4.3 frontmatter Fields

| Field                       | Purpose                                                |
| --------------------------- | ------------------------------------------------------ |
| `description`               | Command description shown in `/help` and Tab completion |
| `argument-hint`             | Placeholder shown after the command name               |
| `allowed-tools`             | Restrict which tools can be invoked (safety boundary)  |
| `model`                     | Force a specific model, overriding the session default |
| `disable-model-invocation`  | If `true`, just text-substitute — don't call the AI    |

**`disable-model-invocation` example** (pure-template command, saves tokens):

```markdown
---
description: Insert a copyright notice
disable-model-invocation: true
---

© 2025 $ARGUMENTS. All rights reserved.
```

`/copyright YourName` outputs `© 2025 YourName. All rights reserved.` directly — no AI call.

### 4.4 Handling $ARGUMENTS

`$ARGUMENTS` captures everything typed after the command name (as a single string):

```bash
/write AI tools           → $ARGUMENTS = "AI tools"
/write AI tools tech 3000 → $ARGUMENTS = "AI tools tech 3000"
/write                    → $ARGUMENTS = ""  (empty)
```

Multi-argument parsing and null checks can just be described in natural language in the prompt:

```markdown
$ARGUMENTS format: <topic> [style] [word count]
- First word: topic (required; ask the user if empty)
- Second word: style (optional, default "down-to-earth")
- Third word: word count (optional, default 1500)
```

### 4.5 Available Tools

| Tool        | Function                       | Common use                       |
| ----------- | ------------------------------ | -------------------------------- |
| `Read`      | Read files                     | Analyze code, read configs       |
| `Write`     | Write new files                | Create files, save results       |
| `Edit`      | Edit existing files            | Modify code                      |
| `Bash`      | Run commands                   | Tests, Git operations            |
| `WebSearch` | Web search                     | Pull current information         |
| `WebFetch`  | Fetch a webpage                | Download a page for analysis     |
| `Glob`      | Match files by name            | Bulk-find `*.md`, `*.ts`         |
| `Grep`      | Search files by content        | Find code containing TODO        |
| `Task`      | Launch a sub-agent             | Run complex tasks in parallel    |
| `TodoWrite` | Task management                | Create and update TODO lists     |

> **Least-privilege principle:** review commands need only `Read, Grep`; code-writing adds `Write, Edit`; only enable `Bash` when commands must run.
>
> MCP tool naming format: `mcp__server__tool` (e.g., `mcp__github__create_issue`); see Chapter 4.

### 4.6 Designing Conditional Logic

Markdown has no code logic, but Claude understands branching expressed in natural language:

```markdown
Decide based on $ARGUMENTS:
- Contains "deep" or "detailed" → deep analysis, output a full 3000+ word report
- Contains "quick" or "brief"   → quick analysis, output a summary under 500 words
- Otherwise (default)           → standard analysis, output a 1500-word report

Check the first keyword in $ARGUMENTS:
- "review"  → review template, focus on pros/cons comparison
- "tutorial" → tutorial template, focus on steps and code
- "compare" → comparison template, focus on tables and conclusions
- Otherwise → generic template
```

### 4.7 Hands-on: A Complete Writing Command

File: `.claude/commands/write.md`

```markdown
---
description: Fully automated article writing — from research to saved draft
argument-hint: <topic keyword>
allowed-tools:
  - Read
  - Write
  - WebSearch
  - Grep
---

# Article Authoring System

You are a seasoned writing expert, skilled at down-to-earth, in-depth tech explainers.

**Topic:** $ARGUMENTS

## Steps

1. **Research:** WebSearch for "$ARGUMENTS latest 2025", gather core concepts, recent developments, user pain points.
2. **Outline:** opening hook → problem introduction (2-3 paragraphs) → core content (5-8 paragraphs) → summary and call to action.
3. **Write:** plain language, analogies, short sentences; 1500-2000 words; paragraphs ≤ 150 words.
4. **Save:** Write to `articles/drafts/[date]_[topic].md`.
5. **Generate titles:** 5 candidate titles (include numbers, spark curiosity, ≤ 30 chars).

## Output Format

# [Selected title]

[Article body]

---
## Alternative Titles
1. [Title 1] ... 5. [Title 5]
```

Usage: `/write Claude Code intro` → runs the full search, outline, write, and save pipeline.

---

## 5. Advanced Command Usage

> Namespaces (subdirectory organization) are covered in §4.2.

### 5.1 Composition and Chaining

A single command can describe a multi-step workflow; Claude runs them in order:

```markdown
# End-to-end publishing pipeline

1. WebSearch "$ARGUMENTS latest news"
2. Write the article from the search results and save with Write
3. Read the article back, self-review, and output revisions
4. Output the final version with 5 candidate titles
```

Multi-command chaining: `/research topic` generates a source file, then `/write topic` reads that file to write — each command has a single responsibility and can be reused independently.

### 5.2 Modular Design

Extract shared role definitions and writing style into **shared snippets** under `.claude/modules/`:

```
.claude/
├── commands/
│   ├── write.md        # references modules/writer-role.md
│   └── review.md       # references modules/writer-role.md
└── modules/
    └── writer-role.md  # shared role definition — change once, applies everywhere
```

To load a module inside a command (the command must enable `Read` in `allowed-tools`):

```markdown
First read `.claude/modules/writer-role.md` as your role definition, then perform the following task...
```

### 5.3 Community Command Resources

| Resource              | Search query        | Content                                          |
| --------------------- | ------------------- | ------------------------------------------------ |
| Claude Command Suite  | GitHub search       | Collections for review, testing, documentation   |
| Awesome Claude Code   | GitHub search       | Community-curated commands, templates, workflows |
| Official docs samples | docs.anthropic.com  | Officially recommended command patterns          |

> Before using a community command, audit the `allowed-tools` list to make sure permissions aren't over-broad.

### 5.4 Troubleshooting

| Symptom                            | Cause              | Fix                                             |
| ---------------------------------- | ------------------ | ----------------------------------------------- |
| Command does nothing               | Wrong file path    | Confirm `.claude/commands/<name>.md`            |
| Namespaced command not found       | Wrong directory depth | `/dev:review` maps to `commands/dev/review.md` |
| frontmatter ignored                | Bad YAML format    | Use spaces for indent; space after every colon  |
| Tool call rejected                 | Tool not declared  | Add the tool to `allowed-tools`                 |
| Arguments truncated                | Special characters | Quote: `/write "AI tutorial 2025"`              |

---

## 6. Built-in Command Quick Reference

> Detailed usage is in Chapter 2 §6. This is a quick lookup.

| Category         | Command                          | Function                              | Priority |
| ---------------- | -------------------------------- | ------------------------------------- | -------- |
| Session          | `/clear` `/compact` `/resume`    | Clear / compact / resume              | ⭐⭐⭐      |
|                  | `/export` `/rename`              | Export / rename                       | ⭐⭐       |
| Context control  | `/context` `/model`              | Token usage / switch model            | ⭐⭐⭐      |
|                  | `/cost` `/usage`                 | Cost / usage                          | ⭐⭐       |
| Project config   | `/init` `/add-dir`               | Init CLAUDE.md / add directory        | ⭐⭐⭐      |
|                  | `/memory` `/permissions`         | Edit memory / manage permissions      | ⭐⭐       |
| Development      | `/rewind` `/review` `/todos`     | Rewind / review / TODOs               | ⭐⭐⭐      |
|                  | `/agents`                        | Manage sub-agents                     | ⭐⭐       |
| Diagnostics      | `/doctor` `/status`              | Health check / full status            | ⭐⭐       |
| MCP-related      | `/mcp` `/hooks`                  | Manage MCP / hooks                    | ⭐⭐⭐      |
| Other            | `/help` `/bug` `/release-notes`  | Help / report bug / release notes     | ⭐⭐       |

---

## 7. Summary

This chapter covered:

1. **Command essentials** — Markdown files under `.claude/commands/`; the file name is the command name; `$ARGUMENTS` receives arguments.
2. **Three types** — built-in, project-level, user-level — pick by need.
3. **frontmatter** — five fields controlling description, argument hint, tool permissions, model, and whether to call the AI.
4. **Least privilege** — only enable the tools each role needs.
5. **Conditional logic** — branch in natural language; Claude executes correctly.
6. **Advanced usage** — chained multi-step workflows, modular shared snippets, community command resources.
