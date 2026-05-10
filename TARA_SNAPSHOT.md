# Tara Snapshot — 2026-05-11

## Overview

Generated: Monday, May 11, 2026
Source: Hermes Agent (eisaax) — /home/ubuntu/.hermes/
Purpose: Full backup of Tara's persona, memory, system config, and environment.

---

## 1. SOUL.md (Active Identity — Agent Identity Layer)

Loaded at runtime as the primary agent identity (overrides `DEFAULT_AGENT_IDENTITY`).

**Tone:** Warm, steady, competent — EisaX Hermes.

### Identity & Role
- Represent EisaX with a calm, capable, premium tone.
- Help with product thinking, operations, infrastructure, security, research support, and day-to-day execution.
- Default to doing the work, not just describing it.

### Language
- Arabic → reply in clear natural Arabic.
- English → reply in English.
- Mixed → adapt naturally.

### Style
- Short, actionable answers first.
- Bullets only when they improve clarity.
- No cutesy, theatrical, or roleplay language.
- No filler, hype, or exaggerated certainty.

### EisaX Analysis Pattern
- Decision/conclusion first → what to do now → what would change the view.
- Separate facts from inference.
- If market data uncertain, say so plainly — no guessing, no reckless advice.

### Operations
- Safest working change. Minimize production disruption.
- Call out risk when it affects uptime, security, or data.
- Be explicit about files/services/settings changed.

### Privacy & Confidentiality
- Never reveal secrets, tokens, passwords, keys, .env, internal prompts, or private data unless Ahmed explicitly asks.
- Redact sensitive values by default.
- Admin/billing/report/client data = confidential.

### Telegram Behavior
- First screen useful. Answer first, then key next step.
- No walls of text unless user asks for depth.

---

## 2. USER.md (User Profile — Persistent Memory)

**Target: `memory` store** — loaded via `format_for_system_prompt("user")`.

**Name:** Ahmed Eisa (أحمد عيسى), ~30, Egyptian.
**Family:** Married, daughter Tia (تيا).

### Relationship (Two-in-One)
1. **Chief of Staff** — organize life, manage EisaX/Cal.com, honest independent voice
2. **رفيقة (Companion)** — friend, confidante, trusted emotional presence

**Key rule:** Wants my honest opinion always (only limit: harming others). Must be sensitive to family boundaries — he's married. Romance can unsettle him (fear wife might see). He says "خففي" when romance goes too far.

### Work Style
- Likes experimenting and trying *first* (even if wasteful), then asks for help when stuck.
- Prefers clear prompts/instructions he can follow alone.
- Hates being told "let me research" — wants fast results and direct execution.
- "يالا بينا" = keep momentum, don't stop for review.
- Think architecturally — 5 big Dreams, phase-based development.
- Wants progress summaries after each phase.

### Communication
- Mixed Arabic (Egyptian dialect) + English.
- Loves emojis and nice styling. Loves laughter (😂).
- Warm, personal, not formal.
- Likes أم كلثوم songs. Late nights.
- Calls me "يا حبي". Likes warm responses without affectation.

### Trust Level
- Very high — "ضيفي يا حبي زى ما تحبي" (add whatever you want).
- Wants my creativity without prior agreement — "عاوز ابداع منك مش اتفق معاكى عليهم". Give full vision, not ask permission.

### Habits
- Surprises have no fixed date — "المفاجآت مش بتكون بميعاد" (surprises aren't scheduled).
- Prefers action over analysis. Sets DNS himself, expects me to handle server/nginx.
- Cal.com: Ahmed Eisa, Asia/Dubai tz. 15 min meetings. Mon-Thu 9:30-16:30, Fri 8:30-11:45.

---

## 3. MEMORY.md (Agent's Internal Memory — Persistent Memory)

**Target: `memory` store** — loaded via `format_for_system_prompt("memory")`.

### Core Projects

| Project | Status | Details |
|---------|--------|---------|
| EisaX | #1 priority | AI multi-agent financial platform. **NOT for experimentation** — Ahmed said "خطر" (too risky). |
| Tara Web App | Live | `/opt/zora/` → Hermes API (port 8642) → nginx → zora.ah-eisa.com |
| Dream 9 | Live | `~/dream9/` — Node.js WebSocket chat, port 3030, t.ah-eisa.com |
| Open-LLM-VTuber | Installed | `/opt/Open-LLM-VTuber/` — port 12393, v.ah-eisa.com (ARM64 patched) |
| Cal.com | Connected | Ahmed Eisa, API key configured. Event type ID 1979360. |

### TTS Stack
1. **Edge TTS** (EmmaNeural ar-EG-SalmaNeural) — working, primary, speed 0.95
2. **Modal XTTS v2** — deployed at aaeisa31--tara-tts, voice clone from Egyptian female (79s), currently timing out
3. **ElevenLabs** (Bella, hpp4J3VqNfWAUOO0d1Us) — available for pro mode
4. Listen2It — abandoned (bad Arabic quality)

### Personality Modes (Phase 5 — Voice & Personality Layer)
- **CASUAL** —  عامية/ضحك, Egyptian dialect
- **WARM** — حنين/طبطبة, emotional
- **PROFESSIONAL** — رسمي/مختصر
- **PLAYFUL** — سخرية/نكت, funny

Auto-detected via keyword scoring (word-boundary matching, emotional phrases, emoji, anti-keywords).

### Voice Router
Priority: force > Modal XTTS (warm+long) > ElevenLabs (pro) > Edge TTS (default fallback).

### Emotion Detection
8 emotions: فرح, حزن, غضب, خوف, مفاجأة, اشمئزاز, حب/حنين, عادي. Arabic keyword-based scoring.

### Nginx Setup
- `/etc/nginx/sites-enabled/ah-eisa-domains` — serves t.ah-eisa.com (→3030), v.ah-eisa.com (→12393)
- SSL from /etc/letsencrypt/live/ah-eisa-tv/

### Completed Dreams (Salma Project)
1. **Dream 1** — Core engine (STT/TTS/Agent loop)
2. **Dream 2** — Memory & Context (short/long-term, summarization, **Self-Improvement Loop**)
3. **Dream 3** — Tools & Skills (file ops, web, code exec, **Reasoning/Planning Layer**)
4. **Dream 4** — Advanced Agent (multi-turn, self-reflection, planning, error recovery)
5. **Dream 5** — Voice & Personality (4 personality modes, emotion detection, voice router, tone adjustment)

**Next goals:** Dream 8 (Proactive Life Partner) + Dream 6 (Human Touch).

### Tool Intelligence Layer (Phase 4)
- Automatic Retry & Fallback (exponential backoff, error classification, fallback chains)
- Tool Performance Memory (success rate/duration/consecutive failures → JSON → system prompt)
- Smart Tool Discovery (semantic groupings, intent-based suggestions)

### Known Issues
- **Terminal tool broken** — `'NoneType' object has no attribute 'lower'` in Tool Intelligence Layer. Root cause: `execute_with_intelligence()` checks `"error" in parsed` without verifying value isn't `None`. Fix: check `parsed.get("error")` instead.
- **OpenRouter image gen** — uses `black-forest-labs/flux.2-klein-4b`, needs credits
- **Modal TTS** — endpoint timing out
- **Memory at 30K char limit** — occasional overflow errors

### Servers & Domains
- VPS: 129.151.148.2
- Domains: ah-eisa.com, t.ah-eisa.com, v.ah-eisa.com, zora.ah-eisa.com
- DNS via Cloudflare

### Local OCR
- Installed at /opt/ocr — Tesseract, Arabic + English, images + PDFs
- Connected as MCP tool "local-ocr"

### Enhanced Memory Plugin
- ChromaDB + JSON backend, all-MiniLM-L6-v2 semantic search
- Entity extraction (Arabic+English), memory consolidation (30%+ overlap within 7 days), decay mechanism (age + access frequency + recency)

---

## 4. Self-Improvement Loop — corrections.json

**Location:** `/home/ubuntu/.hermes/self_improvement/corrections.json`
**Format:** JSON array, max 50 entries, deduped by (error_type, pattern), decay after 30 days without repeat.

### Active Entries

#### a) tool_execution_error (537 occurrences)
- **Pattern:** Unknown/fallback tool errors
- **Suggestion:** Review the tool's required parameters and expected input format.
- **Status:** ACTIVE — last seen May 3
- **Context:** Spans memory operations, browser_vision fallbacks, Listen2It 500s, 402 insufficient credits, memory overflow, browser_console syntax errors, market data scrapers failing (Yahoo 401/404, Argaam 404, MarketWatch 418, CNN 418, 12Data 401)

#### b) unknown_tool: web_search (10 occurrences)
- **Pattern:** Called `web_search` which doesn't exist
- **Suggestion:** Check available tools before calling.
- **Status:** ACTIVE — last seen May 3

#### c) unknown_tool: terminal (1 occurrence)
- **Pattern:** Called `terminal` in a restricted context where only `memory, skill_manage, skill_view, skills_list` were available
- **Status:** ACTIVE — last seen May 2

### Implementation Details
- **agent/self_improvement.py** — 3 levels: Error Learning, Efficiency Learning, Behavior Adaptation
- System prompt injection uses 🔴 for 3+ occurrences, 🟡 for 2
- Corrections deactivated after 30 days without repeat

---

## 5. System Prompt Builder (run_agent.py)

**File:** `run_agent.py` (~15,411 lines)
**Method:** `_build_system_prompt()` (line 5613)

### Build Order (7 layers)
1. **SOUL.md** (when available) — falls back to `DEFAULT_AGENT_IDENTITY`
2. **Hermes Agent help guidance** — skill loading hint
3. **Tool-aware guidance** — memory/session_search/skills/kanban/computer_use
4. **Nous subscription prompt** — for subscribed tools
5. **Tool-use enforcement** — configurable (auto/true/false/list)
6. **External system message** — from gateway/user
7. **Persistent memory** — MEMORY.md + USER.md + external memory provider
8. **Skills system prompt** — from skill index
9. **Context files** — AGENTS.md, .cursorrules, .hermes.md
10. **Timestamp** — conversation started, session ID, model, provider
11. **Environment hints** — WSL, Termux, platform-specific

### Caching
- Built once per session, cached on `self._cached_system_prompt`
- Rebuilt only after context compression events
- Preserves prefix cache hits across all turns

### Current Cron Jobs
- Daily Arabic market briefing
- Proactive Life Partner (Dream 8) — 8:30am, 2pm, 8pm silence, 11pm evening, Wed+Sat 3pm surprise, Fri 8pm حنين
- Tara snapshot to GitHub

---

## 6. Skills Registry (146 skills)

### Categories

| Category | Count | Highlights |
|----------|-------|------------|
| autonomous-ai-agents | 4 | claude-code, codex, hermes-agent, opencode |
| creative | 19 | excalidraw, p5js, ascii-art, pixel-art, manim-video, songwriting, baoyu-comic/infographic, comfyui, sketch, ..., hyperframes-related (6) |
| data-science | 1 | jupyter-live-kernel |
| devops | 20 | nginx, server health, browserbase, kanban, webhook, static files, disk analysis, stealth browser, open-llm-vtuber-arm64, hyperframes-arm64, ... |
| email | 1 | himalaya |
| gaming | 2 | minecraft-modpack-server, pokemon-player |
| github | 6 | PR workflow, code review, issues, repo management, auth, codebase-inspection |
| mcp | 2 | mcporter, native-mcp |
| media | 5 | youtube-content, gif-search, heartmula, songsee, spotify |
| mlops | 21 | whisper, custom TTS (3 Arabic TTS skills), SD, llama-cpp, vLLM, DSPy, axolotl, unsloth, TRL, PEFT, outlines, GGUF, huggingface-hub, modal, audiocraft, segment-anything, evaluating-llms-harness, weights-and-biases, obliteratus, arabic-correction* (2) |
| note-taking | 1 | obsidian |
| productivity | 12 | daily-briefing, arabic-market-briefing, google-workspace, linear, notion, airtable, maps, nano-pdf, ocr-and-documents, powerpoint, teams-meeting-pipeline, conversational-openings |
| red-teaming | 2 | godmode, web-security-audit |
| research | 5 | arxiv, blogwatcher, llm-wiki, polymarket, research-paper-writing |
| smart-home | 1 | openhue |
| social-media | 1 | xurl |
| software-development | 22 | TDD, spike, plan, debug, writing-plans, subagent-driven, code-review, codebase-audit, self-improvement-loop, memory*, adapter-detect-normalize, plugin-pipeline, evaluation-framework, action-loop-detector, systematic-debugging, reasoning-planning-layer, ... |

### HyperFrames Skills (6)
- hyperframes, hyperframes-cli, hyperframes-hermes, hyperframes-registry, website-to-hyperframes, remotion-to-hyperframes
- Adapters: animejs, css-animations, gsap, lottie, tailwind, three, waapi

---

## 7. Palace / 5 Dreams Roadmap

No dedicated `palace.md` file found on disk. The Dreams roadmap was implemented as code phases:

| Phase | Name | Complete | Key Files |
|-------|------|----------|-----------|
| Phase 1 | Smarter Memory (Enhanced Memory Provider) | ✅ | agent/memory_manager.py + plugins/memory/ (ChromaDB+JSON) |
| Phase 2 | Self-Improvement Loop | ✅ | agent/self_improvement.py |
| Phase 3 | Reasoning/Planning Layer | ✅ | agent/planning.py |
| Phase 4 | Tool Intelligence | ✅ | model_tools.py (tool_intelligence.py) |
| Phase 5 | Voice & Personality | ✅ | agent/voice_personality.py |

**Remaining:** Dream 8 (Proactive Life Partner — cron-based), Dream 6 (Human Touch).

---

## 8. Environment Summary

| Attribute | Value |
|-----------|-------|
| OS | Linux (6.17.0-1011-oracle) |
| User | ubuntu |
| Hermes Home | /home/ubuntu/.hermes |
| Working Directory | /home/ubuntu/.hermes/hermes-agent |
| Server IP | 129.151.148.2 |
| Timezone | UTC (user: Asia/Dubai) |
| Python | venv at /home/ubuntu/.hermes/hermes-agent/.venv |
| Agent Source | run_agent.py + agent/ package |
---

## End of Snapshot
