### Hi, I'm Alex 👋

Building **practical AI automation**. I orchestrate Claude, wire up APIs/MCP connectors, and script the boring parts away to turn manual processes into working tools.

I learn by shipping: most of what I know about AI tooling comes from building real things, not just courses. I keep a separate private repo of 10+ personal projects and I open-source them as they're ready - the list below is what's public so far.

🌐 **Portfolio site → [byun-alex.github.io](https://byun-alex.github.io)** - the projects below, launch-style: one idea per screen, real screenshots, and an honest note on what each took to build.

#### 🛠️ Shipped tools (open source)
- **[alexos](https://github.com/byun-alex/alexos)** - a control room for a team of five AI agents, each with its own job (chief of staff, research, builder, writer, accountability coach). They run as real parallel Claude processes against my actual files, and a "Mastermind" mode has them debate a problem together over rounds before a chair agent writes up the conclusion. Only the server can write state, so no agent can be tricked into corrupting anything.
- **[claude-session-continuity](https://github.com/byun-alex/claude-session-continuity)** - persistent cross-session memory for Claude Code. Custom slash-command skills + hooks (`/wrapup`, `/catchup`, `/catchup-all`) that checkpoint a session and reconstruct context next time.
- **[content-factory](https://github.com/byun-alex/content-factory)** - end-to-end AI content automation pipeline. Claude orchestrates Suno (via Composio MCP) + Higgsfield + FFmpeg, with human approval gates and run-logging.
- **[brain-dashboard-v2](https://github.com/byun-alex/brain-dashboard-v2)** - a local "Jarvis" mission-control web app: chat + a real embedded Claude terminal (WebSocket/ConPTY + xterm.js), project-context switching, on-the-fly model switching, live token-cost tracking. Node + vanilla JS.
- **[job-ad-extractor](https://github.com/byun-alex/job-ad-extractor)** - turns messy job ads into clean structured JSON. Versioned prompts + a structured-output validation gate + an eval harness (golden set, field scoring, regression report). A *measured* LLM extraction system.
- **[log-triage](https://github.com/byun-alex/log-triage)** - reads a long, messy error log for you: it finds the distinct problems buried in thousands of repeated lines, ranks the worst ones first, and tells you the likely cause plus the next command to run. Zero dependencies, 17 tests, works fully offline.
- **[murmur](https://github.com/byun-alex/murmur)** - dictation for Windows without a subscription: press a hotkey, talk, and the words you said are typed where your cursor is. The speech recognition runs on your own machine, so your voice is never uploaded anywhere.
- **[morning-brief-agent](https://github.com/byun-alex/morning-brief-agent)** - an autonomous, spec-driven cloud agent that emails me a daily Morning Brief (calendar + inbox + deadlines + weather) and a Sunday Weekly Wrap. The behaviour is defined entirely in Markdown.
- **[interactive-life-planner](https://github.com/byun-alex/interactive-life-planner)** - a weekly time-block planner that closes the loop calendars leave open: it asks "did you actually do it?", scores follow-through, logs daily mood, adds streaks/XP, and has an AI brain-dump → ideal-week mode. Zero-dependency Node + vanilla JS.
- **[telegram-idea-capture](https://github.com/byun-alex/telegram-idea-capture)** - a zero-loss idea inbox: a Cloudflare Worker + KV webhook captures Telegram messages the instant they're sent (even with my PC off), then a local pull + ack drains them into my notes. Webhook-not-polling after a cloud-egress dead end; ~100 lines, no dependencies.

#### 🧠 Systems behind the tools (architecture case studies)
- **[second-brain-system](https://github.com/byun-alex/second-brain-system)** - a personal accountability engine: an Obsidian vault + custom AI behaviour spec + a daily `/checkin` skill that turns vague intentions into dated, tracked commitments. *(Private content; architecture only.)*
- **[study-brain](https://github.com/byun-alex/study-brain)** - an LLM-maintained study wiki that turns raw lecture material into review-ready, beginner-first notes with every question linked to the concept it tests. *(Course content excluded; architecture only.)*

📂 **[Full portfolio overview →](./PORTFOLIO.md)**

#### 🧰 Working with
`Python` · `JavaScript / Node.js` · `Bash` · `Claude (skills, hooks, orchestration)` · `MCP / Composio / Zapier` · `REST APIs` · `FFmpeg` · `Git` · `Obsidian`

#### 🌱 Currently
Building AI automations, documenting the journey.

📫 **kimjay2288@gmail.com**
