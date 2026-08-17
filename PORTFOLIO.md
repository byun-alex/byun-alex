# Alex Byun - Portfolio Overview

Computer Science student (Sydney). I build **AI-augmented tools and agentic workflows**, and I run my own life on the systems I build, which is where most of what I know actually came from. Below is the map: shipped open-source tools first, then the things I deployed and operated rather than authored, then the personal "operating system" of knowledge bases behind all of it.

> Philosophy: *proof over credentials.* I would rather show you something I built and broke and fixed than tell you what I studied. Everything here, I built and use daily.

**Counting honestly:** 18 public project repositories, plus the portfolio site and the profile README.

---

## 🛠️ Shipped tools (open source)

**Live site with all of these as product pages: [byun-alex.github.io](https://byun-alex.github.io)**

### 1. AlexOS - a local multi-agent operating system
**[github.com/byun-alex/alexos](https://github.com/byun-alex/alexos)**

A mission-control app where a roster of AI agents with distinct roles work in parallel against my real workspace. Each agent is a real headless Claude process, not a chat wrapper; a "Mastermind" mode has a panel debate a problem over rounds and synthesise the conclusion into shared memory. Security-first: only the server writes state ("instructions are not capabilities"), so a persona cannot be tricked into corrupting it.
*Node.js · WebSocket · React/Vite/Tailwind · headless Claude CLI · parallel process management.*

### 2. market-data-scanner - real-time ingestion and indicator engine
**[github.com/byun-alex/market-data-scanner](https://github.com/byun-alex/market-data-scanner)**

A Core-Engine / Adapter design where async exchange adapters (Binance REST warmup plus a live WebSocket kline stream, and a keyless Korean-equity feed I reverse-engineered) normalise every source into one candle model, so adding a market is one new adapter and never a change downstream. A rolling per-symbol store rejects still-forming, duplicate and out-of-order candles, driven by real WebSocket behaviour, so indicator windows cannot be silently corrupted. 49 tests, standard library only.

This is the data-engineering half of a larger private scanner. The trading strategy in that private system is a domain expert's intellectual property and is deliberately not published; what is public is entirely my own engineering, and I verified that before pushing.
*Python · async I/O · ports-and-adapters · test-first · zero dependencies.*

### 3. overnight-agent - a verify-gated autonomous job runner
**[github.com/byun-alex/overnight-agent](https://github.com/byun-alex/overnight-agent)**

Hand a coding agent a job spec before bed, wake to a finished branch and an honest report. A dispatcher launches a worktree-isolated worker, a watchdog kills stalls, and an independent verify gate checks the claimed output against the actual files before anything is accepted. Designed around five named failure modes of unattended runs, with a stop-condition contract in the job spec.
*Bash · WSL · git worktrees · Telegram reporting · designing for failure modes rather than the happy path.*

### 4. content-factory - an end-to-end agentic content pipeline
**[github.com/byun-alex/content-factory](https://github.com/byun-alex/content-factory)**

Claude orchestrates a chain of tools: music generation (Suno via a **Composio MCP server**), image and video generation, and FFmpeg assembly, with **human approval gates** at each stage so nothing proceeds unchecked. The interesting part is not the output, it is wiring several disconnected tools into one reliable, repeatable, documented workflow under an AI orchestrator. Publishing runs headless through the YouTube Data API with per-channel OAuth clients, which is what finally killed a recurring token-expiry failure.
*Claude · MCP · FFmpeg · OAuth · approval-gated automation.*

### 5. morning-brief-agent - an autonomous, spec-driven daily agent
**[github.com/byun-alex/morning-brief-agent](https://github.com/byun-alex/morning-brief-agent)**

A scheduled cloud agent that reads my calendar, inbox, deadlines and the weather every morning and emails me a brief before the day starts. The whole behaviour is a Markdown spec read at run time: an edit, not a redeploy. Running into my own inbox daily since June.
*Claude Code cloud routines · cron · MCP (Gmail/Calendar) · spec-as-config.*

### 6. job-ad-extractor - LLM extraction you can prove behaves
**[github.com/byun-alex/job-ad-extractor](https://github.com/byun-alex/job-ad-extractor)**

Turns messy job ads into strict validated JSON: every output checked against a pydantic schema and rejected at the gate if malformed, prompts versioned with a changelog, quality scored against a hand-labelled golden set with regression checks. The reliability layer that turns "an LLM call I wrote" into "an LLM call I can prove behaves."
*Python · pydantic · prompt versioning · eval harness · provider-agnostic.*

### 7. log-triage - paste a messy log, get a ranked diagnosis
**[github.com/byun-alex/log-triage](https://github.com/byun-alex/log-triage)**

Reads a long, messy error log for you: it finds the distinct problems buried in thousands of repeated lines, ranks the worst ones first the way a support engineer would (how severe, how often, how recent, whether it is suddenly spiking), and tells you the likely cause plus the next command to run. ~25 auditable rules, 17 tests, Python standard library only, fully offline and deterministic.
*Python · parsing · rule-based diagnosis · zero dependencies.*

### 8. murmur - local dictation for Windows
**[github.com/byun-alex/murmur](https://github.com/byun-alex/murmur)**

Press a hotkey, talk, press it again: the words you said are typed where your cursor is, with filler sounds stripped out. Paid apps do this for 12 to 15 USD a month by sending your voice to their servers; Murmur does the same job on your own machine, so nothing is ever uploaded. Live testing surfaced a real Windows bug: the text pasted twice because the synthetic paste keystroke fired while my hand was still physically holding the hotkey down. The fix was to wait for key release first.
*Python · faster-whisper · sounddevice · global hotkeys · on-device AI.*

### 9. brain-dashboard - a local "Jarvis" operations dashboard
**[github.com/byun-alex/brain-dashboard](https://github.com/byun-alex/brain-dashboard)** · **[v2](https://github.com/byun-alex/brain-dashboard-v2)**

A local web app that sits over all my projects: a chat pane plus an **embedded live Claude terminal** (WebSocket/ConPTY + xterm.js), project-context switching, and **real-time token-cost tracking** so the cost of every AI action is visible. Node plus vanilla JS, no framework. Getting the terminal working meant root-causing a Node 24 native-binding incompatibility on Windows and identifying the correct prebuilt fork, which I wrote up so it is reproducible.
*Node.js · WebSocket · ConPTY · xterm.js · cost observability.*

### 10. todo-viz - a checklist that writes back into the file
**[github.com/byun-alex/todo-viz](https://github.com/byun-alex/todo-viz)**

My whole task list is one Markdown file, so this turns it into a clickable checklist in the browser and writes every tick straight back into that same file. The easy version writes on every click and corrupts the file the first time two things edit at once. The real work was the safe-write path: re-read fresh on every write, match the target line by index **and** exact text, reject with a conflict error if the file has shifted, and swap atomically through a temp file and a rename.
*Python standard library · atomic writes · optimistic concurrency · vanilla JS.*

### Also public
**claude-session-continuity** (custom slash-command skills and hooks that give Claude Code durable cross-session memory: `/wrapup` checkpoints a session, `/catchup` reconstructs it) · **telegram-idea-capture** (a Cloudflare Worker plus KV webhook that captures every message the instant it is sent, even with my PC off; the design came from a real dead end, a polling agent with no outbound internet) · **ai-avatar-pipeline** (a persona-driven video pipeline written up as a case study, with the third-party parts credited rather than claimed) · **interactive-life-planner** (weekly planner with follow-through scoring and an AI strategy-session mode) · **planner** (the zero-dependency MVP it grew from) · **study-brain** and **second-brain-system** (sanitised architecture case studies of the private knowledge systems below).

---

## 🔧 Deployed and operated, not authored

Some of the most useful things I have done were not greenfield builds. I think it is worth being precise about which is which.

### Instagram comment-to-DM automation, self-hosted and live
**Application: [diwenne/openreply](https://github.com/diwenne/openreply) · my deployment and fixes: [my fork](https://github.com/tradealex2288-star/openreply)**

The hosted product that does this bills per person contacted, so it gets more expensive exactly when it works. I deployed an open-source clone of that one feature myself instead: **Next.js on Vercel** for the dashboard, OAuth callback and Meta webhooks, and a **queue worker with Postgres and Redis on Railway**, split out because a queue consumer has to stay awake and a serverless function sleeps between requests. About $5 a month, uncapped, live against real traffic.

Then it broke in production, on a post at 57,000 views: duplicate replies and DMs, every send logging FAILED. The cause was not in the code. A second tool was still connected to the same account and double-firing, and because the platform permits exactly one private reply per comment, its message landed first and mine came back as an API error. The tell was a missing emoji on the duplicate's button, which my template always sends. Diagnosing it against the live database surfaced two genuine bugs underneath, both fixed and pushed to my fork: a retry storm, and a race where the webhook and the reconciliation poll could claim the same comment at worker concurrency five, so the send-log insert is now the atomic claim with a lease on pending rows.

The lesson generalises past this stack: when an automation double-fires, confirm nothing else is connected doing the same job before you touch a line of code, because a second tool leaves no trace inside the first one's logs.
*Vercel · Railway · Postgres · Redis · BullMQ · OAuth and webhooks · production incident root-cause.*

### Ad-reel compiler, built on an open-source editor

The reels for my own product are all the same video with different words, so the words became data and the video became code written once: lines in a JSON file, one command, finished vertical mp4s out. The part I care about is the build-time guard that refuses to render any reel carrying a figure a buyer could read as proof (a price paired with a volume, a follower count, a bare `NNk`). It fails the build rather than warning, because a warning inside a batch of eighteen gets scrolled past.

The renderer underneath is Hassan Aboul Hasan's open-source [claude-youtube-editor](https://github.com/hassancs91/claude-youtube-editor). That spine is his work. Mine is the compiler on top of it.
*Remotion · data-driven rendering · build-time validation gates · Node.*

---

## 🧠 The system behind it: AI-augmented knowledge bases

I do not use these tools in isolation. I have built a set of **Obsidian vaults, each with its own `CLAUDE.md` behaviour spec, custom skills, and hooks**, so the assistant behaves differently for each purpose. This is where the agentic-workflow muscle actually got built.

- **A personal productivity and accountability system** - a vault plus a custom daily `/checkin` skill that turns vague intentions into dated, tracked commitments and files the result automatically. Built to fix a real problem (follow-through), and I run it every day.
- **A structured "learning Claude" vault** - the Anthropic Academy curriculum mapped into concept hubs, a skill tree, and a questions inbox; notes link back to what I have built so theory stays attached to practice.
- **An idea-development and content-research vault** - where business and content ideas get developed past the one-line stage.
- **A study system** - coursework organised in Obsidian with custom skills for note generation and review, including an offline flashcard app generated from raw course notes where every card carries an explain-from-scratch layer for a reader with zero background.

Common thread: **custom Claude behaviour per context** (CLAUDE.md), **reusable skills** for the repetitive parts, **hooks** for automation, and **a central session diary** so nothing is forgotten between sessions.

---

## ⚙️ How I work

- **Agentic, human-in-the-loop.** Claude orchestrates; I gate the decisions that matter. Approval steps, not blind automation.
- **Skills and hooks over one-off prompts.** If I do something twice, I turn it into a reusable command.
- **MCP for tool-wiring.** Connecting AI to real external tools through MCP servers rather than copy-paste.
- **Verify before done.** A claim is not accepted because the agent said so. Where there was no test framework, I have built cheap structural checks rather than skip verification.
- **Credit what is not mine.** If I deployed it rather than wrote it, the page says so.
- **Document as I build.** Every project carries its own context doc so a cold session, or another person, can pick it up.
- **Ship, then improve.** Time-boxed, finished, public, over endlessly polished and private.

---

## 🧰 Tech
Python · JavaScript / Node.js · Claude and LLM agentic workflows · MCP servers · prompt engineering · async I/O and WebSocket streams · Postgres · Redis · Vercel · Railway · Cloudflare Workers · REST/JSON and OAuth · Git / GitHub · FFmpeg · Obsidian · Markdown.

**GitHub:** [github.com/byun-alex](https://github.com/byun-alex)
