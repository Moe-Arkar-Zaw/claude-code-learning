---
name: whats-new
description: Check what's new in Claude Code since the last check, using Exa to read the official changelog, and log the beginner-relevant changes in Whats_New.md. Use when the user asks about the latest Claude Code features, updates, releases or versions, or whether their installed Claude Code is out of date.
argument-hint: "[version to start from, e.g. 2.1.320]"
allowed-tools: mcp__plugin_exa_exa__web_search_exa, mcp__plugin_exa_exa__web_fetch_exa, Read, Edit, Write, PowerShell(claude --version)
---

# What's new in Claude Code

Find the Claude Code changes since the last check and explain the ones that matter to a beginner. The user is learning Claude Code on Windows 11 with PowerShell.

## 1. Find the starting point

- Run `claude --version` to get the installed version.
- Read `Whats_New.md` in the project root, if it exists. Its newest entry says which version was checked last.
- Start from `$ARGUMENTS` if a version was given; otherwise from the last checked version; otherwise (first run) cover only the last 7 days.

## 2. Read the changelog with Exa

- Use `web_fetch_exa` to read https://code.claude.com/docs/en/changelog (set `maxCharacters` high enough to reach the starting version, e.g. 30000).
- If that fails, use `web_search_exa` to find the Claude Code changelog or GitHub releases page (github.com/anthropics/claude-code/releases) and fetch that instead.
- For the one or two biggest new features, fetch their docs page (the changelog usually links it) so you can explain how to turn them on.
- Use only what's on these pages. Don't fill gaps from memory.

## 3. Filter and explain

The changelog is long and mostly fixes. Keep only what a beginner would notice or use:

- **Keep:** new features, new commands or settings, new models, changes to skills, subagents, plugins, MCP, hooks, memory or permissions, and anything Windows/PowerShell-specific.
- **Skip:** bug fixes, enterprise/gateway/admin features, cloud-runner and SDK internals, unless the user asks.

Reply with:

```markdown
## Claude Code: <old version> → <newest version>
Installed: <version> (<up to date / behind: run `claude update`>)

### Headline: <feature name> (v<version>, <date>)
- **What it is**: ...
- **How to try it**: ... (PowerShell)
- **Source**: <URL>

### Also new
- **<Feature>** (v<version>): one sentence
```

Note when a feature is experimental or needs a newer version than the one installed.

## 4. Log it

Ask whether to save it. If yes, add the result to the top of `Whats_New.md` (create the file with a `# Claude Code: what's new` heading if it doesn't exist), under a `## <date>: checked up to v<newest version>` heading, so the next run knows where to start.

If a feature matches a topic in an unfinished session of `Learning_Note.md`, mention it so the user can fill in that topic with `/research-topic`.
