# Alex Byun - Portfolio Overview

Computer Science student (Sydney). I build **AI-augmented tools and agentic workflows**, and I work through my own life in parallel with AI while learning from the systems I build. Below is the map of what I've been accumulating: shipped, open-source tools first, then the personal "operating system" of AI-augmented knowledge bases behind them.

> Philosophy: *proof over credentials.* I'd rather show you something I built and broke and fixed than tell you what I studied. Everything here, I built and use daily.

---

## 🛠️ Shipped tools (open source)

### 1. claude-session-continuity - persistent memory for Claude Code
**[github.com/byun-alex/claude-session-continuity](https://github.com/byun-alex/claude-session-continuity)**

Claude Code starts every session with no memory of the last. I built a set of custom **slash-command skills + hooks** that give it durable, cross-session memory: `/wrapup` checkpoints a session into a structured handoff log, `/catchup` reconstructs context next time, `/catchup-all` briefs across every project. It's the documentation layer the tool was missing, and it auto-documents *my own work* as a side effect.

*Claude Code · skills · hooks · Markdown · a fixed entry schema as the contract between writer and reader.*

### 2. content-factory - an end-to-end agentic content pipeline
**[github.com/byun-alex/content-factory](https://github.com/byun-alex/content-factory)**

Claude orchestrates a chain of tools - music generation (Suno via a **Composio MCP server**), media generation, and FFmpeg video assembly, with **human approval gates** at each stage so nothing proceeds unchecked. The interesting part isn't the output; it's wiring four disconnected tools into one reliable, repeatable, documented workflow under an AI orchestrator.

*Claude · MCP · FFmpeg · approval-gated automation · human-in-the-loop design.*

### 3. brain-dashboard - a local "Jarvis" operations dashboard
**[github.com/byun-alex/brain-dashboard](https://github.com/byun-alex/brain-dashboard)**

A local web app that sits over all my projects: a chat pane plus an **embedded live Claude terminal** (WebSocket/ConPTY + xterm.js), project-context switching, and **real-time token-cost tracking** so the cost of every AI action is visible. Node + vanilla JS, no framework.

*Node.js · WebSocket · ConPTY · xterm.js · cost observability.*

### 4. job-ad-extractor - a measured LLM extraction system
**[github.com/byun-alex/job-ad-extractor](https://github.com/byun-alex/job-ad-extractor)**

Turns messy free-text job ads into clean, strict JSON. It's built like a *production* extraction step, not a prompt: **versioned prompts** with a changelog, a **structured-output validation gate** (pydantic) that provably rejects + logs malformed model output, and an **eval harness** - a hand-labelled golden set, field-by-field scoring, a regression check against the last run, and a Markdown report. Provider-agnostic (runs offline with a mock). The point is *measuring* extraction quality, which is what most LLM features skip.

*LLM extraction · prompt versioning · structured-output validation · eval harness · regression testing.*

### 5. morning-brief-agent - an autonomous, spec-driven cloud agent
**[github.com/byun-alex/morning-brief-agent](https://github.com/byun-alex/morning-brief-agent)**

A scheduled Claude Code cloud agent that every morning reads my calendar, inbox, to-dos, deadlines, and the weather, composes a CEO-style **Morning Brief**, and emails it to me - plus a strategic **Sunday Weekly Wrap**. The twist: the agent's entire behaviour is defined in **Markdown** - the spec files *are* the program, so changing the brief is an edit, not a redeploy. Calendar + inbox are wired through an MCP connector; deadlines come from source-of-truth tracker files, never invented.

*Claude Code cloud routines · cron scheduling · MCP (Calendar + Gmail) · spec-as-config · autonomous agents.*

### 6. planner - an interactive daily-planner MVP
**[github.com/byun-alex/planner](https://github.com/byun-alex/planner)**

A zero-dependency planner: type a task + a time, it drops onto an hour-by-hour timeline and persists in the browser. One self-contained `index.html`, ~150 lines of vanilla JS, no build or backend. The first finished slice of a larger idea - a *fun* weekly planner where engagement is the differentiator.

*Vanilla JS · localStorage · self-contained · shipped-small-and-finished.*

---

## 🧠 The systems behind the tools: AI-augmented knowledge bases

I don't just use these tools in isolation - I've built a set of **Obsidian vaults, each with its own `CLAUDE.md` behaviour spec, custom skills, and hooks**, so the assistant behaves differently for each purpose. This is where the agentic-workflow muscle actually got built. The two most developed are written up as architecture case studies (the vaults themselves stay private):

### second-brain-system - a personal accountability engine *(case study)*
**[github.com/byun-alex/second-brain-system](https://github.com/byun-alex/second-brain-system)**

A vault + custom AI behaviour spec + a daily **`/checkin`** slash-command skill that turns vague intentions into dated, tracked commitments and files the result automatically - built to fix a real problem (follow-through), with switchable coaching personas and an override. Architecture only; private journal content excluded.

### study-brain - an LLM-maintained study wiki *(case study)*
**[github.com/byun-alex/study-brain](https://github.com/byun-alex/study-brain)**

A study system where the human curates sources and the **AI writes and maintains the entire wiki** - turning raw slides/transcripts into beginner-first notes with every question answered and linked to the concept it tests, via a custom multi-step ingest skill and a strict schema. Architecture only; course content excluded.

**Also in the set (not yet written up):** a structured "learning Claude" vault (Anthropic Academy curriculum → concept hubs + skill tree), an idea-development & content-research vault, and **youtube-niche-automation** - a multi-agent content system (ideation → script → manager agents) defined as composable agent prompts.

Common thread: **custom Claude behaviour per context** (CLAUDE.md), **reusable skills** for the repetitive parts, **hooks** for automation, and **a central session diary** so nothing is forgotten between sessions.

---

## ⚙️ How I work

- **Agentic, human-in-the-loop.** Claude orchestrates; I gate the decisions that matter. Approval steps, not blind automation.
- **Skills + hooks over one-off prompts.** If I do something twice, I turn it into a reusable command.
- **MCP for tool-wiring.** Connecting AI to real external tools (calendar, email, music gen) through MCP servers rather than copy-paste.
- **Measure, don't assume.** For anything LLM-shaped, I build the eval/validation layer - proof it works, not just a demo that ran once.
- **Document as I build.** Every project carries its own context doc so a cold session - or another person - can pick it up.
- **Ship, then improve.** Time-boxed, finished, public - over endlessly polished and private.

---

## 🧰 Tech
Python · JavaScript / Node.js · Claude / LLM agentic workflows · MCP servers (Composio / Zapier) · prompt engineering · structured-output validation & evals · automation & tool integration · Git / GitHub · Obsidian · Markdown · FFmpeg · WebSocket / ConPTY.

**GitHub:** [github.com/byun-alex](https://github.com/byun-alex)
