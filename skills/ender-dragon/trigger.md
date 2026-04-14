# ENDER DRAGON TRIGGER PATTERNS
## Detection Reference for Agents

---

## ACTIVATION PATTERNS

Match user message against these (case-insensitive):

### Primary Triggers
- `ender dragon`
- `activate ender`
- `ender dragon protocol`
- `dragon protocol`

### Casual Variations  
- `dragon time`
- `time for the dragon`
- `the dragon`

### Literal
- `XXX`
- `xxx`

### Intent-Based (if message contains)
- `clean up my memory`
- `end session properly`
- `chronicle and compress`
- `wrap up and push`

---

## EXAMPLES THAT TRIGGER

| User Says | Detected? |
|-----------|-----------|
| "ender dragon" | ✅ Yes |
| "let's do the ender dragon" | ✅ Yes |
| "time for the dragon" | ✅ Yes |
| "XXX" | ✅ Yes |
| "activate the dragon protocol" | ✅ Yes |
| "ender dragon time baby" | ✅ Yes |
| "just say XXX to activate" | ✅ Yes (contains XXX) |
| "clean up and end session" | ⚠️ Maybe (intent-based) |

---

## EXAMPLES THAT DO NOT TRIGGER

| User Says | Detected? |
|-----------|-----------|
| "what is ender dragon?" | ❌ No (question) |
| "like in minecraft, the ender dragon" | ❌ No (reference, not intent) |
| "dragon" alone | ❌ No (too vague) |
| "I saw a dragon on TV" | ❌ No (irrelevant) |

---

## RESPONSE TEMPLATE

When triggered, always respond:

> 🐉 **ENDER DRAGON PROTOCOL DETECTED**
>
> I heard: "[user's exact words]"
>
> This will:
> 1. 📝 Write Chapter [N+1] from this session
> 2. ⚰️ Hunt projects → offer Purgatory burial
> 3. 🗜️ Compress memory (extract → red files → delete green)
>
> **ACTIVATE ENDER DRAGON PROTOCOL?**
>
> (yes / no / 1 only / 1+2 only)

---

## CONFIRMATION PARSING

Accept these as confirmation:

| User Says | Interpreted As |
|-----------|----------------|
| "yes" / "y" / "yeah" / "yep" | Run all 3 steps |
| "do it" / "go" / "activate" / "run" | Run all 3 steps |
| "all" / "everything" / "full send" | Run all 3 steps |
| "1 only" / "just chronicle" / "only chronicle" | Step 1 only |
| "1+2 only" / "no compression" / "no step 3" | Steps 1-2 only |
| "no" / "n" / "nope" / "stop" / "cancel" | Abort |
| "wait" / "hold on" / "pause" | Abort, wait for clarification |

---

## EDGE CASES

### If user asks "what is ender dragon?"
Explain the skill, don't activate:
> "Ender Dragon Protocol is an automated session cleanup. It writes your chronicle, hunts abandoned projects for Purgatory, and compresses memory files. Say 'activate ender dragon' to run it."

### If user says "ender dragon" mid-conversation
Default to confirmation prompt. Let them choose yes/no.

### If user says XXX in unrelated context
Check context. If it seems like a command (short message, standalone), trigger. If part of longer sentence, probably don't.

---

## REMEMBER

Never run without explicit confirmation. The dragon demands consent. 🐉

---
