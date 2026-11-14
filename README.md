# Claude Code Learning

My personal notes from learning [Claude Code](https://code.claude.com/docs), Anthropic's AI coding assistant for the terminal, Desktop app and IDEs. I use it on Windows 11 with PowerShell.

## What's in this folder

| File | What it holds |
|---|---|
| [`Learning_Note.md`](Learning_Note.md) | The main notes, one numbered section per study session |
| [`Troubleshooting.md`](Troubleshooting.md) | Problems I hit and how I fixed them |
| `Whats_New.md` | A log of Claude Code updates (created by the `/whats-new` skill) |
| [`CLAUDE.md`](CLAUDE.md) | Instructions Claude Code reads automatically when working in this folder |
| `screenshots/` | Screenshots from each session (`1.png`, `2.png`, ...) |
| `claude_code_functioning.png`, `subagents_and_agent_teams.png` | Reference diagrams |
| `.claude/` | The skills, agent and agent memory built for this folder (see below) |

## Topics covered so far

| Session | Topics |
|---|---|
| 1 | Installation, Desktop app tabs (Code and Cowork), working with folders, terminal usage |
| 2 | Connecting to Anthropic, prompting, `.md` files and CLAUDE.md, subagents, plan mode, building an agent |
| 3 | Agent view, subagents, agent teams, skills, plugins, MCP |

Each note has a one- to three-sentence explanation plus a **Syntax** line listing its commands and shortcuts, so it doubles as a cheat sheet:

```markdown
- **Plan mode**: A mode where Claude only reads and researches ...
  - Syntax: `Shift+Tab` (switch permission modes until "plan mode" shows) · `claude --permission-mode plan` (start in plan mode)
```

## Tools built for this folder

While learning, I built these Claude Code extensions here. They're working examples of the session 3 topics.

| Tool | Type | What it does | How to use it |
|---|---|---|---|
| `research-topic` | Skill (uses the exa plugin) | Searches the web for a Claude Code topic or error and writes a short note with sources | `/research-topic agent teams` |
| `whats-new` | Skill (uses the exa plugin) | Reads the official changelog and logs what's new since the last check | `/whats-new` |
| `note-writer` | Subagent with memory | Fills in unfinished sessions and adds troubleshooting entries in the notes' style | "use the note-writer agent to fill in session 4" |

They live in:

```
.claude/
├── skills/research-topic/SKILL.md
├── skills/whats-new/SKILL.md
├── agents/note-writer.md
└── agent-memory/note-writer/MEMORY.md
```

The skills need the **exa** plugin installed (`/plugin` to check).

## How I add a new session

1. Add `## 4.` (and so on) to `Learning_Note.md` with a list of topic names to study.
2. Run `/research-topic <topic>` to learn each one, or ask the `note-writer` agent to fill in the whole session.
3. Run `/whats-new` now and then to catch new features and changed syntax.
4. Commit the changes.

## Sources

- Claude Code docs: https://code.claude.com/docs
- Changelog: https://code.claude.com/docs/en/changelog

## Credits

Thanks to **Krish Naik**, whose teaching material I learned Claude Code from. These notes are my own summaries, written in my own words.
