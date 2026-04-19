# EMBER-GUIDE.md — Human Operator Manual for Pijus

If something goes wrong with Ember, read this one file. Don't read 15.

---

## Quick Command Reference

All of these happen by sending a message to Ember's session (`session:ember`).

| Command | What it does |
|---------|--------------|
| `pause` | Ember writes PAUSED.flag, all loops halt immediately |
| `resume` | Deletes PAUSED.flag, next loop proceeds normally |
| `status` | Ember reports: active experiments, budget remaining, runway, last report |
| `report now` | Force daily loop to run now |
| `show budget` | Real-time budget state |
| `show hot leads` | Recent hot leads and their status |
| `upgrade brain` | Toggle Ember to Opus for next loop (stuck/brainstorming) |
| `default brain` | Reset Ember to kimi-k2.5 |

---

## Pause & Resume

### To pause:
Send Ember: `pause`

She writes `ember/triggers/PAUSED.flag` and exits. All cron loops check this flag first — if present, they exit silently without doing anything.

### To resume:
Send Ember: `resume`

She deletes the flag and sends a confirmation with summary of what she's picking up.

### Manual pause (emergency, if she's not responding):
```bash
touch /home/deploy/.openclaw/workspace/ember/triggers/PAUSED.flag
```

### Manual resume:
```bash
rm /home/deploy/.openclaw/workspace/ember/triggers/PAUSED.flag
```

---

## Roll Back a Bad Self-Upgrade

If Ember's 3-day self-upgrade rewrote a core file badly:

1. Pause her first: `pause`
2. Find the backup:
   ```bash
   ls /home/deploy/.openclaw/workspace/ember/archive/core/
   ```
   Example result: `SOUL-20260425.md`, `THINKING-20260425.md`
3. Restore it:
   ```bash
   cp /home/deploy/.openclaw/workspace/ember/archive/core/THINKING-20260425.md \
      /home/deploy/.openclaw/workspace/ember/memory/THINKING.md
   ```
4. Resume: `resume`

---

## Reset Her State Completely

**Use only if corrupted beyond repair.**

1. Pause: `pause`
2. Archive current state:
   ```bash
   mv /home/deploy/.openclaw/workspace/ember/state/ember-state-*.md \
      /home/deploy/.openclaw/workspace/ember/archive/
   ```
3. Resume: `resume`

Next boot = Day 1 sequence.

---

## Kill All Her Crons

If Ember needs to fully stop running:

1. List her jobs: ask me (Seren) to run `cron list` for ember-related jobs
2. Remove them: ask me to run `cron remove <jobId>` for each

Or through OpenClaw CLI directly (Pijus has access).

---

## Manually Trigger a Daily Loop

Send Ember: `report now`

She runs the daily loop immediately regardless of schedule.

---

## Check Budget in Real-Time

Send Ember: `show budget`

Or read directly:
```bash
cat /home/deploy/.openclaw/workspace/ember/memory/BUDGET.md
```

---

## Review Pending Hot Leads

Send Ember: `show hot leads`

Or read directly:
```bash
cat /home/deploy/.openclaw/workspace/ember/memory/hot-leads.md
```

---

## Toggle to a Stronger Model

When Ember is stuck or needs deeper brainstorming:

Send: `upgrade brain`

She uses Opus (or whatever's set as upgrade model) on the NEXT loop only. Reverts automatically.

To reset permanently: `default brain`

---

## File Reference (what each does)

| File | Purpose |
|------|---------|
| SOUL.md | Who Ember is, voice rules |
| PRODUCT.md | Current product being marketed |
| THINKING.md | Idea generation engine |
| REPORTING.md | How Ember talks to Pijus |
| LOOPS.md | Hourly / daily / 3-day schedules |
| PROTOCOL.md | Ender-dragon memory system |
| BUDGET.md | €200 cap, real-time tracking |
| EXPERIMENTS.md | Live + dead experiment log |
| SKILLS.md | Installed tools |
| INBOUND.md | Reply handling + 30min takeover |
| ESCALATION.md | Stuck protocol, stall detection |
| ARCHIVE.md | Campaign archive rules |
| DAY1.md | Boot sequence |
| LIMITS.md | Per-platform action caps |
| META-LEARNINGS.md | Cross-campaign insights (permanent) |
| EMBER-GUIDE.md | This file |
| hot-leads.md | Every hot lead ever, with conversation logs |

---

## If Something Is Really Broken

1. Pause her first (stops further damage)
2. Ping Seren (me) — I can diagnose
3. Worst case: archive her state, restart from scratch

---

## Changelog
- 2026-04-19: Initial version.
