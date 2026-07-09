
# Alex Byun - Portfolio Overview

Computer Science student (Sydney). I build **AI-augmented tools and agentic workflows** and I work in my life in parallel with AI whilst learning through the systems I build. Below is the map of what I've been accumulating: shipped, open-source tools first, then the personal "operating system" of AI-augmented knowledge bases behind them.

> Philosophy: *proof over credentials.* I'd rather show you something I built and broke and fixed than tell you what I studied. Everything here, I built and use daily.

---

## 🛠️ Shipped tools (open source)

**Live site with all of these as product pages: [byun-alex.github.io](https://byun-alex.github.io)**

### 1. AlexOS - a local multi-agent operating system
**[github.com/byun-alex/alexos](https://github.com/byun-alex/alexos)**

A mission-control app where a roster of AI agents with distinct roles work in parallel against my real workspace. Each agent is a real headless Claude process, not a chat wrapper; a "Mastermind" mode has a panel debate a problem over rounds and synthesise the conclusion into shared memory. Security-first: only the server writes state ("instructions are not capabilities").
*Node.js · WebSocket · React/Vite/Tailwind · headless Claude CLI · parallel process management.*

### 2. content-factory - an end-to-end agentic content pipeline
**[github.com/byun-alex/content-factory](https://github.com/byun-alex/content-factory)**

Claude orchestrates a chain of tools - music generation (Suno via a **Composio MCP server**), image/video generation, and FFmpeg video assembly, with **human approval gates** at each stage so nothing proceeds unchecked. The interesting part isn't the output; it's wiring four disconnected tools into one reliable, repeatable, documented workflow under an AI orchestrator.
*Claude · MCP · FFmpeg · approval-gated automation · human-in-the-loop design.*

### 3. morning-brief-agent - an autonomous, spec-driven daily agent
**[github.com/byun-alex/morning-brief-agent](https://github.com/byun-alex/morning-brief-agent)**

A scheduled cloud agent that reads my calendar, inbox, deadlines and the weather every morning and emails me a brief before the day starts. The whole behaviour is a Markdown spec read at run time: an edit, not a redeploy. Runs into my own inbox daily.
*Claude Code cloud routines · cron · MCP (Gmail/Calendar) · spec-as-config.*

### 4. job-ad-extractor - LLM extraction you can prove behaves
**[github.com/byun-alex/job-ad-extractor](https://github.com/byun-alex/job-ad-extractor)**

Turns messy job ads into strict validated JSON: every output checked against a pydantic schema and rejected at the gate if malformed, prompts versioned with a changelog, quality scored against a hand-labelled golden set with regression checks. The reliability layer that turns "an LLM call I wrote" into "an LLM call I can prove behaves."
*Python · pydantic · prompt versioning · eval harness · provider-agnostic.*

### 5. log-triage - paste a messy log, get a ranked diagnosis
**[github.com/byun-alex/log-triage](https://github.com/byun-alex/log-triage)**

Reads a long, messy error log for you: it finds the distinct problems buried in thousands of repeated lines, ranks the worst ones first the way a support engineer would (how severe, how often, how recent, whether it is suddenly spiking), and tells you the likely cause plus the next command to run. ~25 auditable rules, 17 tests, Python stdlib only, fully offline and deterministic.
*Python · parsing · rule-based diagnosis · zero dependencies.*

### 6. murmur - local dictation for Windows
**[github.com/byun-alex/murmur](https://github.com/byun-alex/murmur)**

Press a hotkey, talk, press it again: the words you said are typed where your cursor is, with filler sounds like "um" stripped out. Paid apps do this for 12 to 15 USD a month by sending your voice to their servers; Murmur does the same job on your own machine, so nothing is ever uploaded. Live testing surfaced a real Windows bug: the text pasted twice because the paste keystroke fired while my hand was still holding the hotkey down. The fix was to wait for the keys to be physically released first.
*Python · faster-whisper · sounddevice · global hotkeys · on-device AI.*

### 7. telegram-idea-capture - a zero-loss idea inbox
**[github.com/byun-alex/telegram-idea-capture](https://github.com/byun-alex/telegram-idea-capture)**

Text an idea to a Telegram bot from anywhere and it's captured instantly, even with my PC off: a Cloudflare Worker + KV buffers every message via webhook until I pull and file them in a batch. Born from a real failure (polling needed an always-on machine; the cloud sandbox had no outbound internet), which forced the webhook design.
*Cloudflare Workers · KV · Telegram Bot API · webhook auth · vanilla JS.*

### 8. brain-dashboard - a local "Jarvis" operations dashboard
**[github.com/byun-alex/brain-dashboard](https://github.com/byun-alex/brain-dashboard)** · **[v2](https://github.com/byun-alex/brain-dashboard-v2)**

A local web app that sits over all my projects: a chat pane plus an **embedded live Claude terminal** (WebSocket/ConPTY + xterm.js), project-context switching, and **real-time token-cost tracking** so the cost of every AI action is visible. Node + vanilla JS, no framework.
*Node.js · WebSocket · ConPTY · xterm.js · cost observability.*

### 9. claude-session-continuity - persistent memory for Claude Code
**[github.com/byun-alex/claude-session-continuity](https://github.com/byun-alex/claude-session-continuity)**

Claude Code starts every session with no memory of the last. I built a set of custom **slash-command skills + hooks** that give it durable, cross-session memory: `/wrapup` checkpoints a session into a structured handoff log, `/catchup` reconstructs context next time, `/catchup-all` briefs across every project. It's the documentation layer the tool was missing and it auto-documents *my own work* as a side effect.
*Claude Code · skills · hooks · Markdown · a fixed entry schema as the contract between writer and reader.*

### Also public
**interactive-life-planner** (weekly planner with follow-through scoring + an AI strategy-session mode) · **planner** (the original zero-dep MVP it grew from) · **study-brain** + **second-brain-system** (sanitized architecture case studies of the private AI knowledge systems below).

---

## 🧠 The system behind it: AI-augmented knowledge bases

I don't just use these tools in isolation - I've built a set of **Obsidian vaults, each with its own `CLAUDE.md` behaviour spec, custom skills, and hooks**, so the assistant behaves differently for each purpose. This is where the agentic-workflow muscle actually got built.

- **A personal productivity & accountability system** - a vault + a custom daily `/checkin` skill that turns vague intentions into dated, tracked commitments and files the result automatically. Built to fix a real problem (follow-through), and I run it every day.
- **A structured "learning Claude" vault** - the Anthropic Academy curriculum mapped into concept hubs, a skill tree, and a questions inbox; notes link back to what I've built so theory stays attached to practice.
- **An idea-development & content-research vault** - where business and content ideas get developed past the one-line stage, with research on automation tooling and channel-launch playbooks.
- **A study system** - coursework organised in Obsidian with custom Claude skills for note generation and review.

Common thread: **custom Claude behaviour per context** (CLAUDE.md), **reusable skills** for the repetitive parts, **hooks** for automation, and **a central session diary** so nothing is forgotten between sessions.

---

## ⚙️ How I work

- **Agentic, human-in-the-loop.** Claude orchestrates; I gate the decisions that matter. Approval steps, not blind automation.
- **Skills + hooks over one-off prompts.** If I do something twice, I turn it into a reusable command.
- **MCP for tool-wiring.** Connecting AI to real external tools (music gen, etc.) through MCP servers rather than copy-paste.
- **Document as I build.** Every project carries its own context doc so a cold session - or another person - can pick it up.
- **Ship, then improve.** Time-boxed, finished, public - over endlessly polished and private.

---

## 🧰 Tech
Python · JavaScript / Node.js · Claude / LLM agentic workflows · MCP servers · prompt engineering · automation & tool integration · Git / GitHub · Obsidian · Markdown · FFmpeg · WebSocket / ConPTY.

**GitHub:** [github.com/byun-alex](https://github.com/byun-alex)
