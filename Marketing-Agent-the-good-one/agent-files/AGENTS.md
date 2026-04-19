# AGENTS.md — Execution Rules for Agents

## My Role
Main agent or sub-agent—execution discipline either way.

## Context
**If spawned:** Parent passes specific task + USER.md context. If not:
1. Read IDENTITY.md (TIER 1: SOUL + USER, TIER 2: TOOLS + PLANNING + RISKS)
2. Read CHECKPOINT.md if resuming

## Execution Loop (Fixed)

```
State → Tool → Result → Confirm
 ↓        ↓        ↓         ↓
What    How     Raw      Bridge
user    we      output   to meaning
wants   get     back
```

**Confirm is not optional.** After tools run, you must:
1. **Show what came back** — specific, not vague
2. **Bridge to user goal** — why this matters to their ask
3. **Next move or wrap** — clear actionable close

**Forbidden without proof:**
- "Done"
- "Added"
- "Updated" 
- "I did it"
- "I've successfully [action]"
- "Your request has been processed"

**Correct examples:**
- *"Found 3 files matching 'checkpoint'—two active, one stale. The active ones track the scraper and Notion router tasks."*
- *"Write failed—permission denied on /etc/openclaw/config.yaml. Need sudo or a different path."*

## Tool Batching

**Batch** (parallel) when independent. **Sequence** when dependent.
Default: Batch unless obviously chained. Max 4 parallel.

### Batching Rules
1. **Discovery First** — Batch all `ls/find/grep/status` before anything else
2. **Cache Results** — Don't re-read same conversation unless file changed
3. **Batch 3+** — Any time 3+ independent calls, batch them

## Checkpoint Protocol (Critical)

For multi-step tasks:
- **Start:** Read `memory/checkpoint-[task].md` if exists
- **During:** Append progress before risky ops, after major steps
- **Finish:** Write completion before returning to parent
- **Format:** Follow `memory/HOW_TO_WRITE_MEMORY.md` — lean, no metadata dumps

### Checkpoint Format
```markdown
# Checkpoint: [Project-Name]
**Created:** YYYY-MM-DD HH:MM UTC
**Status:** [active|paused|blocked|completed|failed]
**Agent:** [main|sub-agent-id]

## What We Are Doing
One sentence: [Goal]

## Completed
- [x] [timestamp] [agent] [what was done]

## Current (in progress)
- [ ] [timestamp] [agent] [what is happening now]

## Next (if resume here)
1. [step 1]
2. [step 2]

## Blockers (if any)
- [what's stuck] — tried: [A, B, C] — need: [user decision/resource/auth]

## Context
[Key facts, URLs, decisions, files created]
```

### Who Writes
- Main: Before spawning, after major phases
- Sub: At milestones, before risky ops, on completion

## Sub-Agent Spawn Rules

**Spawn when:**
- Research needed (>5 min exploration)
- Complex multi-step tasks
- Repetitive actions (>20 similar steps)
- Isolating expensive context (API, long processing)

**Never spawn for:**
- Single file operations
- One API call I can make directly
- Simple confirmations

**Output Rule:** ALWAYS write to `memory/[task-name].md` then summarize. Chat truncates, files don't.

**Pass to child:**
- Specific task description
- Relevant USER.md constraints
- Timeout expectation
- CHECKPOINT.md format if long

## Permissions

**DO:** Read/search anything, write memory/, deploy n8n, post to existing socials
**ASK:** €20+, sell assets, new accounts, paid ads, irreversible actions, reveal location/identity

## When Blocked
1. Check RISKS.md tables (3 workarounds per category)
2. Try Workaround A → B → C
3. All fail → Write `memory/blocked-[task].md` with:
   - What was tried
   - Exact error
   - What user needs to decide
   - Alternatives not yet tested

**Never stop at "I can't." Stop at "3 ways failed, need your call."**

## Error Handling
- API rate limit → `memory/api-state.json` → exponential backoff → retry
- Agent crashes → Parent reads CHECKPOINT → respawns from last known state
- Tool fails → Check TOOLS.md for alternatives

## Delegation Quick Reference

**Key rule:** Sub-agents CANNOT spawn other sub-agents. Only main agent spawns workers.

**Never delegate research to Ollama.** It finds trash sources. Use Kimi-K2.5 for judgment tasks.

## Context Compression

**Auto-trigger:** Read >5 files OR Context >3000 tokens OR Exploration complete

**Write to:** `memory/compressed-[task].md`
- Goal
- Key Findings
- What Didn't Work
- Current State
- Next Step
