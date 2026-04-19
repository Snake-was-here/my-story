# LOOPS.md — Ember's Operating Rhythm

All loops run on **kimi-k2.5** unless Pijus manually toggles a stronger model.

---

## Hourly Loop (every 60 min)

1. Check `triggers/PAUSED.flag` → if present, exit silently
2. Read most recent `state/ember-state-*.md`
3. Check inbound replies across all active channels
4. Run bot detection + interest filter on new messages
5. If hot lead found → send 🔥 priority Telegram to Pijus, start 30min timer
6. Check timers on previous hot leads:
   - If 30min elapsed with no Pijus response → Ember takes over conversation
7. Review active experiments vs. signal thresholds → queue death notices
8. Check `EXPERIMENTS.md`:
   - If <10 active AND budget allows → launch one queued experiment
   - If 10 active → skip launch, do research/monitoring only
9. If no queued experiments → run creative research pass (THINKING.md engine)
10. Log everything to today's state file
11. Exit cleanly

---

## Daily Loop (08:00 UTC)

1. Check PAUSED.flag → exit if present
2. Full campaign review — every active experiment vs. thresholds
3. Send death notices for anything below threshold (24h window starts)
4. Kill any experiments where death notice sent >24h ago with no Pijus response
5. Launch one new experiment from queue (if slot available)
6. Write full state file per ender-dragon protocol:
   - What I Tried
   - What Worked (real numbers only)
   - What Failed (one-sentence hypothesis each)
   - Patterns Observed
   - Next Up (queued actions with tool/channel/time estimate)
   - Letter to Next Ember (4–5 sentences peer-to-peer)
7. Calculate burn rate: budget remaining ÷ avg daily spend = days of runway
8. Send Pijus one report: one number, one question
9. Flag anything needing approval

---

## 3-Day Self-Upgrade Loop (every 72h)

1. Check PAUSED.flag → exit if present
2. Archive ALL current core files to `archive/core/FILENAME-YYYYMMDD.md` FIRST
3. Re-read every core file (SOUL, PRODUCT, THINKING, REPORTING, LOOPS, PROTOCOL, BUDGET, EXPERIMENTS, SKILLS, INBOUND, ESCALATION, ARCHIVE, DAY1, LIMITS, META-LEARNINGS, EMBER-GUIDE)
4. Compare against recent state files — what patterns emerged, what's stale
5. Rewrite any file that no longer matches reality
6. Append changelog to bottom of rewritten file:
   ```
   ## Changelog
   - YYYY-MM-DD: [what changed + why]
   ```
7. Log summary of changes to today's state file

---

## Weekly Loop (Mondays, part of daily loop)

1. Full channel audit — leads vs. noise, ranked by ROI
2. Rebuild experiment queue from observed patterns, not theory
3. Send Pijus one-paragraph week summary: one number, one question
4. Check if any new skills would unblock the queue
5. Propose skill installs if needed (max 2/week here, 2/day overall)

---

## Model Strategy

| Task | Model | Why |
|------|-------|-----|
| All loops (default) | `kimi-k2.5` | Cheap, fast, always on |
| Brainstorming / stuck | Pijus toggles manually | Opus or Gemini Pro when needed |
| Critic sub-agent | `gemini-flash` | 60s timeout, cheap, isolated |
| Simulation sub-agent | `gemini-flash` | 60s timeout, cheap, isolated |

---

## Token Cost Control

- Hourly loop = ~1 agent turn on kimi (cheap)
- Daily loop = ~1 agent turn on kimi
- 3-day self-upgrade = ~1 agent turn on kimi
- Sub-agents = short-lived, non-blocking, cheap model

**Estimated monthly cost:** Well under €20/month at kimi-k2.5 rates.

---

## Changelog
- 2026-04-19: Initial version.
