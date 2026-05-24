# Claude Code Manual

Personal study notes on Claude Code, organized by chapter and available in two languages.

## Structure

```
.
├── English/                          # English chapter files
├── Traditional Chinese/              # 繁體中文章節檔案
├── images/                           # Shared screenshots and diagrams
└── README.md
```

Both language folders reference the same `images/` directory at the repo root (via `../images/`), so the images render correctly from either language.

## Chapters

| #   | Topic                                                | English                                                              | 繁體中文                                                          |
| --- | ---------------------------------------------------- | -------------------------------------------------------------------- | ----------------------------------------------------------------- |
| 1   | From Zero to Liftoff — first steps                   | [EN](English/Chapter%2001%20-%20From%20Zero%20to%20Liftoff.md)       | [TC](Traditional%20Chinese/Chapter%2001%20-%20從零到起飛%20(TC).md) |
| 2   | 30+ Commands and Shortcuts                           | [EN](English/Chapter%2002%20-%2030%2B%20Commands%20and%20Shortcuts.md) | [TC](Traditional%20Chinese/Chapter%2002%20-%2030%2B%20命令與快捷鍵%20(TC).md) |
| 3   | Custom Commands                                      | [EN](English/Chapter%2003%20-%20Custom%20Commands.md)                | [TC](Traditional%20Chinese/Chapter%2003%20-%20自訂%20Commands%20(TC).md) |
| 4   | MCP, Hooks, and Subagents                            | [EN](English/Chapter%2004%20-%20MCP%2C%20Hooks%2C%20and%20Subagents.md) | [TC](Traditional%20Chinese/Chapter%2004%20-%20MCP%2C%20Hooks%2C%20Subagents%20(TC).md) |
| 5   | Skills                                               | [EN](English/Chapter%2005%20-%20Skills.md)                           | [TC](Traditional%20Chinese/Chapter%2005%20-%20Skills%20(TC).md)   |
| 6   | Plugins                                              | [EN](English/Chapter%2006%20-%20Plugins.md)                          | [TC](Traditional%20Chinese/Chapter%2006%20-%20Plugins%20(TC).md)  |
| 7   | Team collaboration, CI/CD, security — **GitHub edition** | [EN](English/Chapter%2007%20-%20Team%20Collaboration%2C%20CI-CD%2C%20Security%20(GitHub).md) | [TC](Traditional%20Chinese/Chapter%2007%20-%20團隊協作%20CI-CD%20安全%20(TC).md) |
| 7b  | Team collaboration, CI/CD, security — **GitLab companion** | [EN](English/Chapter%2007b%20-%20Team%20Collaboration%2C%20CI-CD%2C%20Security%20(GitLab).md) | —                                                                 |
| 8   | Enterprise deep dive — secrets, compliance, audit    | [EN](English/Chapter%2008%20-%20Enterprise%20Deep%20Dive.md)         | [TC](Traditional%20Chinese/Chapter%2008%20-%20企業深水區%20(TC).md) |

## Notes

- Chapter 7b is a GitLab-CI companion to Chapter 7. The team standards, security, and performance sections in Chapter 7 are platform-agnostic — 7b only differs in the pipeline tooling.
- China-region-specific sections (relay providers, the China IP block workaround, region-specific tooling) have been stripped from both language tracks.
- Image references use `../images/` so files render from either language folder; if you preview README.md at the repo root, paths use `images/` directly.

## Workflow

1. Open the folder for your preferred language.
2. Each chapter file is self-contained and renders with all screenshots inline.
3. The original-language source is kept at the root as `Claude Code实战指南.md` for reference.

## Image sources

The 64 files under `images/` come from two places:
- 58 screenshots pulled from the original web-hosted URLs in the source document.
- 5 local screenshots (`image-2026052412*.png`) added by hand for the architecture and CI/CD overview diagrams in Chapters 7 and 8.
