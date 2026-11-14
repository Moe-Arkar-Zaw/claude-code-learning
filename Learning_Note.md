## 1.

- **Installation**: Install Claude Code with the native installer, then open a new terminal and run `claude --version`. If it prints a version number, it's installed. Native installs update themselves in the background.
  - Syntax: `irm https://claude.ai/install.ps1 | iex` (install, PowerShell) · `claude --version` (check it works) · `claude update` (update) · `claude doctor` (check install problems)
- **Tabs**: The Claude Desktop app has separate tabs, including Code and Cowork. Code is Claude Code with a graphical interface, for working in a project folder. Cowork is for multi-step, non-coding tasks with your files.
  - Syntax: no command; you click the tabs in the Desktop app. Running `claude` in the terminal gives you the same Claude Code as the Code tab.
- **Uploading**: In Claude Code you don't upload files one by one. You open Claude in a folder (or pick the folder in the Code tab), and it can read the files there. Then you ask questions about them.
  - Syntax: `cd "D:\my folder"` then `claude` (work in a folder) · `@Learning_Note.md` (point Claude at a file in your prompt) · `claude --add-dir "D:\other folder"` or `/add-dir` (add another folder)
- **Terminal Usage**: Claude Code runs in a terminal (PowerShell or CMD on Windows). Go to your project folder, run `claude`, and type requests in plain language. Commands that start with `/` control the session itself.
  - Syntax: `claude` (start) · `claude "explain this project"` (start with a prompt) · `claude -c` (continue last chat) · `claude -r` (pick an old chat to resume) · `claude -p "question"` (answer once, then exit) · `/help` · `/exit`

---
## 2.

- **Anthropic connection**: Claude Code needs an internet connection to Anthropic's servers (`api.anthropic.com`). If it can't connect, check your network, DNS, VPN, proxy or firewall, or try another network. To test whether DNS is the problem, run `nslookup api.anthropic.com 1.1.1.1`: if it returns IP addresses, your network's own DNS is the problem.
  - Syntax: `nslookup api.anthropic.com 1.1.1.1` (test DNS) · `curl.exe -I https://api.anthropic.com` (any HTTP reply, even 404, means you're connected) · `claude auth status` (check login) · `/doctor`
- **Claude Code prompting**: A good prompt gives the task, the context (which files or parts of the project), any constraints, and the result you want. Clear, specific prompts get better and more accurate answers.
  - Syntax: `@file` (add a file as context) · `! git status` (run a shell command from the prompt) · `Esc` (stop Claude) · `/rewind` (go back to an earlier message) · `/clear` (start a fresh conversation)
- **Claude .md file meaning**: A `.md` file is a Markdown file: plain text with simple formatting such as headings, bullet lists, links and code blocks. `CLAUDE.md` is a special Markdown file that Claude Code reads automatically at the start of every session. You use it to give Claude standing instructions about your project.
  - Syntax: `/init` (create CLAUDE.md for a project) · `/memory` (open memory files to edit) · `./CLAUDE.md` (this project) · `~/.claude/CLAUDE.md` (all projects) · Markdown: `# heading`, `- bullet`, `**bold**`, `` `code` ``
- **Subagents**: Helper agents that Claude hands a focused task to, such as research, debugging or testing. Each one works in its own context window and returns only a summary, which keeps the main conversation clean. Several can run in parallel.
  - Syntax: `.claude/agents/<name>.md` (this project) · `~/.claude/agents/<name>.md` (all projects) · "use the note-writer agent to fill in session 3" (call one by name)
- **Plan mode**: A mode where Claude only reads and researches. It makes no changes, then proposes a step-by-step plan for you to approve before it starts editing. It's useful for larger or riskier tasks.
  - Syntax: `Shift+Tab` (switch permission modes until "plan mode" shows) · `claude --permission-mode plan` (start in plan mode)
- **Building an agent**: A custom agent (subagent) is one Markdown file. At the top are settings: a name, a description of when to use it, and optionally its tools, model and memory. Below them are its instructions. Where you save the file decides where the agent is available: `.claude/agents/` for this project only, `~/.claude/agents/` for all projects.
  - Syntax: one Markdown file in `.claude/agents/`:
    ```markdown
    ---
    name: note-writer
    description: When Claude should use this agent
    tools: Read, Edit, WebFetch
    model: sonnet
    memory: project
    ---
    Instructions for the agent go here.
    ```

---
## 3.

- **Agent view**: One screen that shows all your background Claude Code sessions: which are working, which need your input, and which are done. You can start new sessions from it, peek at one and reply, or open its full conversation. It's a research preview.
  - Syntax: `claude agents` (open agent view) · `←` (from a session: send it to agent view) · `/bg` (move the current session to the background) · `claude --bg "task"` (start a background session) · `Space` (peek at a session) · `Enter` (open it) · `Esc` (leave)
- **Subagents**: Subagents run inside your current session and report their result back to the main conversation, while the main conversation keeps the overall picture. Claude can start them on its own, or you can ask for a specific one by name.
  - Syntax: `/tasks` (see running and finished subagents, and stop them) · `/agents` (shows where subagent files live) · `.claude/agents/<name>.md`
- **Agent teams**: Several separate Claude Code sessions working as a team. A lead assigns work, and teammates share a task list and message each other directly. Agent teams are experimental, off by default, and use many more tokens than subagents.
  - Syntax: `$env:CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS = "1"` then `claude` (turn on; experimental) · "Spawn three teammates: one on UX, one on architecture, one devil's advocate" · `↑`/`↓` + `Enter` (pick a teammate and message it)
- **Skills in Claude Code**: A skill is a folder with a `SKILL.md` file of instructions for one kind of task. Claude only sees its name and description until a request matches it, then loads the full instructions. You can also run one yourself with `/skill-name`.
  - Syntax: `.claude/skills/<name>/SKILL.md` (this project) · `~/.claude/skills/<name>/SKILL.md` (all projects) · `/research-topic mcp` (run a skill: `/skill-name` + arguments)
- **Plugins in Claude Code**: A plugin is a package that adds skills, agents, hooks and MCP servers to Claude Code in one install. You install plugins from marketplaces, which are catalogs of plugins. They make it easy to share a setup.
  - Syntax: `/plugin` (browse and install) · `/plugin install commit-commands@claude-plugins-official` (install one: `name@marketplace`) · `claude plugin list` (list installed) · `/reload-plugins` · `/exa:search` (a plugin's skill: `/plugin:skill`)
- **Claude Code MCP**: MCP (Model Context Protocol) is an open standard for connecting Claude Code to outside tools and data, such as web search, databases, GitHub or Slack. Each connection is an MCP server that gives Claude new tools.
  - Syntax: `claude mcp add --transport http <name> <url>` (add a server) · `claude mcp list` (list servers) · `/mcp` (check status and sign in, inside a session)
