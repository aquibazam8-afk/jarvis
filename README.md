# 🤖 Jarvis — A Multi-Agent Personal AI Operating System

A local, file-based **multi-agent system** built on [Claude Code](https://www.claude.com/product/claude-code). Jarvis acts as a personal "second brain": a coordinating main agent that delegates work to specialized sub-agents across distinct life and work domains — career, data analytics, content, agriculture, and daily operations.

> Built to explore agent orchestration, context engineering, and practical AI automation.

---

## 🧠 Architecture

Jarvis uses a **coordinator + sub-agent** pattern. The main agent reads persistent context files on startup, then routes deep tasks to isolated sub-agents, each with its own system prompt and tool permissions.

```
jarvis/
├── CLAUDE.md            # Main agent brain — behavior + delegation rules
├── SOUL.md              # Personality / tone definition
├── USER.md              # Operator profile (templated here)
├── memory/
│   └── MEMORY.md        # Persistent cross-session memory (agent updates it)
├── outputs/             # All generated deliverables land here
└── .claude/
    ├── agents/          # 5 specialized sub-agents
    │   ├── career.md    #   job search, resume tailoring, application tracking
    │   ├── analyst.md   #   SQL / Python / Tableau / Power BI / portfolio projects
    │   ├── creator.md   #   YouTube content pipeline (research → script → production)
    │   ├── agri.md      #   farm + agronomy planning, govt schemes
    │   └── ops.md       #   daily planning, weekly reviews, task triage
    └── commands/        # Slash commands
        ├── wake.md      #   /wake     — load all context + greet
        ├── plan-day.md  #   /plan-day — today's priorities from memory
        ├── job-hunt.md  #   /job-hunt — find + apply + log jobs
        ├── video-idea.md#   /video-idea — full content pipeline
        └── farm-check.md#   /farm-check — seasonal farm/garden status
```

### Key design ideas
- **Persistent memory.** The agent appends to `MEMORY.md` after meaningful tasks, giving continuity across sessions without re-explaining context.
- **Context separation.** Each sub-agent runs in its own context window, keeping the main thread clean and tokens efficient.
- **Least privilege.** Read-only agents get only read tools; builder agents get write/execute. Permissions are scoped per agent.
- **Token awareness.** Sub-agents are invoked only when a task justifies a separate context; quick questions are answered inline.

---

## 🚀 Setup

1. Install [Claude Code](https://www.claude.com/product/claude-code).
2. Clone this repo and open the folder in your editor.
3. Fill in `USER.md` with your own profile.
4. Open the project in Claude Code and type `/wake`.

The agent loads `CLAUDE.md`, `SOUL.md`, `USER.md`, and `MEMORY.md`, then greets you and surfaces your pending tasks.

---

## 🛠️ Tech & concepts demonstrated
- Claude Code sub-agents (YAML-frontmatter Markdown definitions)
- Multi-agent orchestration and task delegation
- Context / memory engineering for stateful agents
- Custom slash commands as reusable workflows
- Prompt design for role-specialized agents

## 🗺️ Roadmap
- [ ] Telegram bridge for phone access (read/respond on the go)
- [ ] Voice I/O (Whisper speech-to-text + TTS)
- [ ] Presence-detection sub-agent for home automation
- [ ] Optional StackChan desk-robot hardware front-end

---

## 📄 License
MIT — see [LICENSE](LICENSE).

*Built by [Aquib Azam Ansari](https://github.com/aquibazam8-afk) — Data Analyst | MBA Agribusiness | exploring applied AI.*
