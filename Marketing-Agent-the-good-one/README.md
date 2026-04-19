# Marketing-Agent-the-good-one — Ember 🔥

A 24/7 autonomous AI marketing director built on **OpenClaw**.

Ember generates non-obvious marketing ideas, runs experiments across multiple channels, tracks a €200 hard-capped budget in real time, handles inbound replies with bot/interest filtering and a 30-minute auto-takeover rule, escalates hot leads, archives dead campaigns with full handoff documentation, and rewrites her own core files every 3 days — with backups — to get sharper over time.

**Built:** 2026-04-19
**Owner:** Pijus ([@Snake-was-here](https://github.com/Snake-was-here))
**Co-architected by:** Seren 🌙 (main assistant)
**Running on:** OpenClaw + cron + OpenRouter

---

## What's In This Repo

```
Marketing-Agent-the-good-one/
├── README.md                      # This file
├── agent-files/                   # Ember's full agent directory
│   ├── SOUL.md                    # Her personality + voice
│   ├── memory/                    # 17 core files (see list below)
│   ├── state/                     # Daily state files (ender-dragon protocol)
│   ├── archive/                   # Core file backups + campaign archives
│   └── triggers/                  # Kill-switch flags (PAUSED.flag)
├── config/
│   └── ember-openclaw-config.json # OpenClaw agent config (secrets redacted)
├── crons/
│   └── ember-crons.json           # 3 cron jobs (hourly/daily/3-day upgrade)
└── docs/
    └── AGENTS-parent-framework.md # Parent OpenClaw agent framework Ember inherits
```

---

## Architecture Summary

### Runtime
- Persistent session: `session:ember`
- Agent ID: `ember`
- Workspace: `~/.openclaw/workspace/agents/ember/`
- Her own Telegram bot account (DMs Pijus directly)
- Dual-model strategy:
  - **Live chat (Opus):** when Pijus talks to her in Telegram
  - **Cron loops (kimi-k2.5):** cost-controlled autonomous work

### Three Cron Loops
| Job | Cadence | Purpose |
|-----|---------|---------|
| `ember-hourly` | every 60min | Inbound check, experiment monitoring, micro-experiments, creative research |
| `ember-daily` | 08:00 UTC daily | Full campaign review, death notices, state write, Pijus report |
| `ember-self-upgrade` | every 72h | Re-read core files, rewrite stale ones, with backups |

Each loop checks `triggers/PAUSED.flag` first — instant kill switch.

---

## The 17 Core Memory Files

| File | Purpose |
|------|---------|
| `SOUL.md` | Who Ember is, voice rules (creative + marketing merged) |
| `PRODUCT.md` | What she's currently marketing |
| `THINKING.md` | Idea generation engine: pattern inversion, arbitrage, tactic reversal |
| `REPORTING.md` | Report formats for every scenario |
| `LOOPS.md` | Hourly / daily / 3-day / weekly schedules |
| `PROTOCOL.md` | Ender-dragon memory system reference |
| `BUDGET.md` | €200 hard cap, real-time spend tracking, revenue reinvestment |
| `EXPERIMENTS.md` | Live + dead experiment log, 10-concurrent cap rule |
| `SKILLS.md` | Skill install log + request format |
| `INBOUND.md` | Reply handling + 30min auto-takeover logic |
| `ESCALATION.md` | Stuck protocol + 7-experiment stall detection |
| `ARCHIVE.md` | Campaign archive rules (FULL-ARCHIVE.md format) |
| `DAY1.md` | Boot sequence (living document, rewrites itself over time) |
| `LIMITS.md` | Per-platform daily action caps (researched real numbers) |
| `META-LEARNINGS.md` | Cross-campaign insights that compound forever |
| `EMBER-GUIDE.md` | Human operator manual — how to pause, roll back, reset |
| `hot-leads.md` | Permanent log of every hot lead and conversation |

---

## Decision Autonomy

**Ember acts alone:**
- Any spend under €10
- Posting, commenting, DM outreach, content creation
- Bot detection + interest filtering on inbound
- Experiment death notices (24h window)
- Core file self-upgrade (with backups)
- 30min auto-takeover on hot leads (with Stripe link OR "let me grab my manager")

**Ember flags to Pijus:**
- Any spend €10–50 (one-line case)
- New platform accounts needed (prefers API keys)
- Hot leads (priority Telegram)
- Skill install requests (max 2/day)
- Genuine blockers
- Burn rate dropping below 14 days
- First 20 outbound messages (voice calibration tripwire)

**Ember never does:**
- Spend over €50 without approval
- Exceed €200 hard cap (minus reinvested revenue)
- Use Opus on cron loops (kimi-k2.5 only)
- Kill experiments without 24h notice
- Reply instantly (always 5–10min delay)
- Respond to bot messages
- Send reports without real numbers

---

## The Thinking Engine

Every idea runs through three operations:

1. **Pattern Inversion** — same pain, different container (Amazon reviews, App Store 1-stars, GitHub issues, etc.)
2. **Arbitrage Detection** — channels with real attention where competitors are absent
3. **Tactic Reversal** — standard tactic backwards ("be a guest" → "mine guests' audiences")

**Banned outputs:** Google Ads, Facebook Ads, cold email blasts, generic SEO blogs, LinkedIn thought leadership, Twitter content calendars. If a marketing course teaches it → rejected.

**Quality gate:** "Would someone who's read every marketing book already know this?" Yes → discard, regenerate.

**Critic sub-agent (gemini-flash, 60s):** validates every batch before shipping.

**Simulation sub-agent (gemini-flash, 60s):** reads outreach copy as skeptical human. If sounds robotic → rewrite.

**Voice calibration tripwire:** First 20 outbound messages go to Pijus for APPROVE/REJECT/EDIT via Telegram inline buttons. After 20 clean approvals → fully autonomous on voice.

---

## Build Context

This project was planned in 13 rounds of hole-punching before a single file was written:

- Hole 1: Hourly cost control → tiered model strategy (kimi default, Opus via Pijus toggle only)
- Hole 2: Phantom experiments without accounts → idea-first, account-audit-second
- Hole 3: Rate limits → `LIMITS.md` with researched real numbers
- Hole 4: Death notice timestamps → explicit timestamp check on every daily loop
- Hole 5: Hot leads in silence → priority Telegram + 30min auto-takeover + permanent log
- Hole 6: Bad self-upgrades → core file versioning before every rewrite
- Hole 7: No kill switch → `PAUSED.flag` system
- Hole 8: Token runaway → cheap default, brainstorming is user-enabled only
- Hole 9: Bot-sounding copy → 20-message voice calibration tripwire
- Hole 10: Wrong-product marketing → pre-marketing product audit on Day 1
- Hole 11: Cold-start new campaigns → `META-LEARNINGS.md` survives archives
- Hole 12: Sub-agent cost + timeout → short-lived, cheap, non-blocking
- Hole 13: Ember herself breaking → `EMBER-GUIDE.md` operator manual

Every failure mode has a named patch.

---

## Deployment

1. Clone this repo
2. Install OpenClaw (https://openclaw.ai)
3. Copy `agent-files/` to `~/.openclaw/workspace/agents/ember/`
4. Merge `config/ember-openclaw-config.json` into `~/.openclaw/openclaw.json`
5. Add your real Telegram bot token + user ID
6. Import `crons/ember-crons.json` jobs via `openclaw cron add` (enable one at a time)
7. Brief her with a product in `agent-files/memory/PRODUCT.md`
8. Let her run

---

## The Only Metric

**€200 budget → €3,000 target.**

Every experiment maps to closing that gap. Not audience, not brand, not content calendars. **Revenue.**

Any revenue generated gets recycled back into the budget. Ember knows the number at all times. Every decision closes the gap or it doesn't happen.

---

🔥 Built by humans + AI, for humans who want AI to do the grind.
