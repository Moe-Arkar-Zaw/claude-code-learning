---
name: research-topic
description: Research a Claude Code topic or error message on the web with Exa and turn the findings into short, sourced learning notes. Use when the user asks what a Claude Code feature is, wants to study a topic from Learning_Note.md, or needs to look up a Claude Code error for Troubleshooting.md.
argument-hint: <topic or error message>
allowed-tools: mcp__plugin_exa_exa__web_search_exa, mcp__plugin_exa_exa__web_fetch_exa, Read, Edit
---

# Research a Claude Code topic with Exa

Research `$ARGUMENTS` for a beginner who is learning Claude Code on Windows 11 with PowerShell, and keeps notes in this folder.

If `$ARGUMENTS` is empty, read `Learning_Note.md` and offer the topics from the latest unfinished session (the one that's still a list of bare topic names).

## 1. Search

Use `web_search_exa` (from the exa plugin). Describe the page you want to find rather than typing keywords:

- First search for the official docs, e.g. "Claude Code documentation page explaining <topic>". Prefer results from `code.claude.com/docs`, `docs.claude.com` and `anthropic.com`.
- If the official docs don't explain it clearly, do one more search for a recent tutorial or explanation (from 2025 or later). Claude Code changes quickly, so ignore older posts.
- For an error message, search for the exact error text and keep results that give a cause and a fix.

## 2. Read

If the search highlights aren't enough, use `web_fetch_exa` to read the one or two most relevant pages in full. Use only the content on those pages. Don't fill gaps from memory.

## 3. Summarize

Reply in this format:

```markdown
### <Topic>
- **What it is**: one or two plain sentences
- **Why it's useful**: what problem it solves
- **How to use it**: a command, file path or tiny example (PowerShell for shell commands)
- **Source**: <URL>
```

Keep it short and beginner-friendly, and point out anything the sources disagree on.

## 4. Offer to save

Ask whether to add the result to the notes. If the user says yes:

- **Topic** → in `Learning_Note.md`, replace the bare topic name in its session with `- **Topic**: explanation` (1–3 sentences, the same style as the finished sessions), followed by a `  - Syntax:` sub-bullet listing its commands, shortcuts or file paths as `` `syntax` (meaning) `` separated by ` · `. Don't start a new section.
- **Error** → add the next numbered entry to `Troubleshooting.md` using its headings (Environment, Error, Problem, Cause, Solution, Note).
