# PROTOCOL.md — Memory Protocol

Ember uses the **ender-dragon memory protocol**.

---

## Source of Truth

**Git link:** https://github.com/Snake-was-here/my-story/tree/main/skills/ender-dragon

On Day 1 (and only Day 1) Ember fetches and fully reads this before doing anything else. It governs how she compresses, stores, and clears memory.

The git spec is the source of truth for implementation details. This file is a local reference.

---

## The 3 Files Ember Writes at End of Every Daily Cycle

All stored in `ember/state/` as `ember-state-YYYYMMDD.md`.

### 1. What I Tried
Every tactic, channel, test, outreach run today.
Enough detail that next Ember continues without asking.

### 2. What Worked
Real numbers only. No number = not a win.

### 3. What Failed
What died. One-sentence hypothesis per failure.

### 4. Patterns Observed
Anything noticed beyond direct test results.

### 5. Next Up
Queued actions with tool, channel, time estimate.

### 6. Letter to Next Ember
4–5 sentences. Peer to peer.
- What's urgent
- What not to repeat
- What to push harder
- What Pijus's mood is

---

## On Every Boot

1. Read most recent `state/ember-state-*.md` first.
2. If none exists → run Day 1 sequence (DAY1.md).
3. If multiple exist → read most recent, skim the one before it for continuity.

---

## Archive Rules

- State files older than 30 days → compressed to `state/archive/YYYY-MM.md` (monthly summary)
- State files for active current month → kept in full
- Never delete state files — always archive

---

## Core File Backups (self-upgrade protection)

Before any 3-day self-upgrade rewrites a core file:

1. Copy current version to `archive/core/FILENAME-YYYYMMDD.md`
2. Rewrite the file
3. Append changelog entry at bottom

This means Pijus can always roll back by restoring from `archive/core/`.

---

## Changelog
- 2026-04-19: Initial version.
