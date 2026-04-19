# ARCHIVE.md — Archive System Rules

When Pijus says "archive this campaign" or "archive everything," Ember runs the full archive sequence.

When a campaign naturally ends (product replaced, killed, or completed), Ember archives automatically.

---

## Archive Location

`ember/archive/[campaign-name]-[date]/FULL-ARCHIVE.md`

Example:
`ember/archive/lively-2026-05-19/FULL-ARCHIVE.md`

---

## FULL-ARCHIVE.md Structure

Written as an **instruction manual for future agents/humans** — not a summary.

```markdown
# FULL ARCHIVE — [Campaign Name]

## CAMPAIGN OVERVIEW
What product was marketed, when, for how long, with what budget.

## THE STRATEGY
What approach was taken and why. What the thinking was at the start.

## WHAT WAS TRIED — COMPLETE LOG
Every channel, every experiment, every tactic attempted.
For each: what it was, how it was set up, how long it ran,
exact results (numbers), and what was concluded.

## WHAT WORKED — WITH PROOF
Specific campaigns that produced real results.
Numbers, screenshots if available, what made them work,
whether they are repeatable.

## WHAT FAILED — WITH HYPOTHESES
Everything that died. Why it probably failed.
What to try instead if someone wants to revisit the channel.

## PATTERNS DISCOVERED
Audience behavior insights, timing signals, platform quirks,
competitor moves, anything observed that isn't tied to a single test.

## CHANNEL RANKING
Every channel ranked by ROI for this specific product and audience.
Not general wisdom — specific to what was observed.

## THE COPY THAT WORKED
Exact messages, hooks, or angles that got real responses.
Written so someone can use them as templates, not just read them.

## WHAT TO DO ON DAY 1 OF THE NEXT CAMPAIGN
A concrete recommended starting point for whoever picks this up next.
Not theory. Based on what this archive actually showed.

## WHAT NOT TO DO
Hard lessons. Things that looked promising and weren't. Time traps.
Channels that sound good but produced nothing for this audience.

## BUDGET BREAKDOWN
Every euro spent, what it went to, what it returned.
Revenue generated vs. original budget — final numbers.

## LETTER TO THE NEXT EMBER
A direct personal message to whatever agent or human picks this up.
Honest, specific, practical. Written like a colleague handing off
a project, not a report being filed.
```

---

## After Archive Is Written

1. **Extract 3–5 transferable insights** to `META-LEARNINGS.md`
   - Not product-specific
   - Cross-channel patterns
   - Audience behavior rules of thumb

2. Clear active campaign files:
   - Reset `PRODUCT.md` to blank template
   - Reset `EXPERIMENTS.md` active + queue (keep dead log)
   - Keep `hot-leads.md` closed ones referenced, ongoing ones archived

3. The archive stays permanently. Never delete.

---

## Meta-Learnings Rule

META-LEARNINGS.md SURVIVES archives.
It compounds across every campaign Ember ever runs.

Example entries:
- "Pinterest outperforms Reddit 3x for visual products priced under €20"
- "Cold DMs with a specific number in the subject line get ~3x replies"
- "YouTube comments on videos 2–4 years old convert better than new videos"

---

## Changelog
- 2026-04-19: Initial version.
