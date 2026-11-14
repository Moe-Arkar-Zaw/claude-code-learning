# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A personal learning journal for Claude Code. It holds Markdown notes and screenshots only; there's no code, build, lint or tests. Commits are made directly to `main`.

## Files

- `Learning_Note.md`: the main notes, split into numbered sessions (`## 1.`, `## 2.`, ...). Each session is a bullet list of `- **Topic**: short explanation`. A session that hasn't been written yet is just a list of topic names (for example, the current `## 3.` lists topics to study: agent view, subagents, agent teams, skills, plugins, MCP). Sessions are separated by a `---` line.
- `Troubleshooting.md`: numbered problems the author has solved, each using the same headings: Environment, Error, Problem, Cause, Solution, Note.
- `README.md`: overview of the folder. When a session or a tool in `.claude/` is added, update its "Topics covered" and "Tools" tables.
- `Whats_New.md`: a log of Claude Code updates, written by the `whats-new` skill. Newest entry at the top; each entry's heading records the version checked up to.
- `.claude/`: the project's own skills (`research-topic`, `whats-new`, both using the exa plugin), the `note-writer` subagent and its memory.
- `screenshots/`: images numbered to match the sessions (`1.png`, `2.png`, ...).
- `*.png` in the root: reference diagrams (how Claude Code works, subagents vs. agent teams).

## Conventions when editing notes

- Keep the existing style: numbered sections, bold topic labels, one or two plain-language sentences per bullet.
- Under every note, add one `  - Syntax:` sub-bullet with the commands, shortcuts or file paths for it, each in backticks with a short meaning in brackets, separated by ` · `. Check the official docs (code.claude.com/docs) so the syntax is correct.
- When filling in a session that only has a topic list, turn each topic name into a `- **Topic**: explanation` bullet. Don't start a new section for it.
- Environment: Windows 11 with PowerShell. Use PowerShell commands in examples (for example `curl.exe`, not `curl`).
