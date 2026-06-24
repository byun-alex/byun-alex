# Alex Byun — Portfolio Overview

Computer Science student (Sydney). I build **AI-augmented tools and agentic workflows**, and I work through my own life in parallel with AI while learning from the systems I build. Below is the map of what I've been accumulating: shipped, open-source tools first, then the personal "operating system" of AI-augmented knowledge bases behind them.

> Philosophy: *proof over credentials.* I'd rather show you something I built and broke and fixed than tell you what I studied. Everything here, I built and use daily.

---

## 🛠️ Shipped tools (open source)

### 1. claude-session-continuity — persistent memory for Claude Code
**[github.com/byun-alex/claude-session-continuity](https://github.com/byun-alex/claude-session-continuity)**

Claude Code starts every session with no memory of the last. I built a set of custom **slash-command skills + hooks** that give it durable, cross-session memory: `/wrapup` checkpoints a session into a structured handoff log, `/catchup` reconstructs context next time, `/catchup-all` briefs across every project. It's the documentation layer the tool was missing, and it auto-documents *my own work* as a side effect.

*Claude Code · skills · hooks · Markdown · a fixed entry schema as the contract between writer and reader.*

### 2. content-factory — an end-to-end agentic content pipeline
**[github.com/byun-alex/content-factory](https://github.com/byun-alex/content-factory)**

Claude orchestrates a chain of tools — music generation (Suno via a **Composio MCP server**), media generation, and FFmpeg video assembly, with **human approval gates** at each stage so nothing proceeds unchecked. The interesting part isn't the output; it's wiring four disconnected tools into one reliable, repeatable, documented workflow under an AI orchestrator.

*Claude · MCP · FFmpeg · approval-gated automation · human-in-the-loop design.*

### 3. brain-dashboard — a local "Jarvis" operations dashboard
**[github.com/byun-alex/brain-dashboard](https://github.com/byun-alex/brain-dashboard)**

A local web app that sits over all my projects: a chat pane plus an **embedded live Claude terminal** (WebSocket/ConPTY + xterm.js), project-context switching, and **real-time token-cost tracking** so the cost of every AI action is visible. Node + vanilla JS, no framework.

*Node.js · WebSocket · ConPTY · xterm.js · cost observability.*

---

## 🧠 The system behind it: AI-augmented knowledge bases

I don't just use these tools in isolation — I've built a set of **Obsidian vaults, each with its own `CLAUDE.md` behaviour spec, custom skills, and hooks**, so the assistant behaves differently for each purpose. This is where the agentic-workflow muscle actually got built.

- **A personal productivity & accountability system** — a vault + a custom daily `/checkin` skill that turns vague intentions into dated, tracked commitments and files the result automatically. Built to fix a real problem (follow-through), and I run it every day.
- **A structured "learning Claude" vault** — the Anthropic Academy curriculum mapped into concept hubs, a skill tree, and a questions inbox; notes link back to what I've built so theory stays attached to practice.
- **An idea-development & content-research vault** — where business and content ideas get developed past the one-line stage, with research on automation tooling and channel-launch playbooks.
- **A study system** — coursework organised in Obsidian with custom Claude skills for note generation and review.
- **youtube-niche-automation** — a multi-agent content system (ideation → script → manager agents) defined as composable agent prompts.

Common thread: **custom Claude behaviour per context** (CLAUDE.md), **reusable skills** for the repetitive parts, **hooks** for automation, and **a central session diary** so nothing is forgotten between sessions.

---

## ⚙️ How I work

- **Agentic, human-in-the-loop.** Claude orchestrates; I gate the decisions that matter. Approval steps, not blind automation.
- **Skills + hooks over one-off prompts.** If I do something twice, I turn it into a reusable command.
- **MCP for tool-wiring.** Connecting AI to real external tools (music gen, etc.) through MCP servers rather than copy-paste.
- **Document as I build.** Every project carries its own context doc so a cold session — or another person — can pick it up.
- **Ship, then improve.** Time-boxed, finished, public — over endlessly polished and private.

---

## 🧰 Tech
Python · JavaScript / Node.js · Claude / LLM agentic workflows · MCP servers · prompt engineering · automation & tool integration · Git / GitHub · Obsidian · Markdown · FFmpeg · WebSocket / ConPTY.

**GitHub:** [github.com/byun-alex](https://github.com/byun-alex)
