# ENDER DRAGON PROTOCOL 🐉 v2.0

## What It Does

Automated session cleanup that:
1. 📝 **Writes chronicle** from current session → pushes to GitHub
2. ⚰️ **Hunts projects** → offers burial in Project Purgatory
3. 🗜️ **Compresses memory** → extracts to red files → deletes green files

## Activation

### Automatic (No Confirmation Needed)
Say any of these intent phrases:
- "test the skill" + "ender dragon"
- "run ender dragon"
- "execute ender dragon"
- "make it happen"

### With Confirmation
Say any of these trigger words:
- "ender dragon"
- "activate ender dragon"
- "ender dragon protocol"
- "time for the dragon"
- "dragon time"
- "XXX"

### Intent Detection
If message contains **both** trigger words AND action words (test/run/execute/do it), skip confirmation.

## Confirmation (If Needed)

> 🐉 **ENDER DRAGON PROTOCOL DETECTED**
>
> I heard: "[your words]"
>
> This will:
> 1. 📝 Write Chapter [N+1] from this session
> 2. ⚰️ Hunt projects → offer Purgatory burial
> 3. 🗜️ Compress memory (extract → red files → delete green)
>
> **ACTIVATE ENDER DRAGON PROTOCOL?**
>
> (yes / no / 1 only / 1+2 only / **dry run** ← shows preview only)

## Step 1: Chronicle

### Option A: Autopilot (Default)
- Pull my-story repo
- Find highest chapter number + 1
- Auto-generate 3 title options from session keywords
- You pick one (or edit)
- Write full chapter using SEREN_WRITING_STYLE.md
- Push, update README

**Output:**
> 📝 **Chapter 7 Title Options:**
> 1. "The Architect Builds a Dragon"
> 2. "Automating the Cleanup of One's Own Chaos"
> 3. "The Session That Created Its Own Ender"
>
> **Pick (1-3) or type custom:**
>
> ✅ **Chapter 7: [Title]** published
> 🔗 [GitHub link]

### Option B: Preview First
If "dry run" requested:
> 📝 **Chronicle Preview:**
>
> **Events that will be included:**
> - Created Ender Dragon Protocol skill
> - Compressed memory (6 files → 3 files)
> - Buried 4 projects in Purgatory
>
> **Events you might want to add/remove:**
> - [checkbox] Skill testing
> - [checkbox] AI rights discussion
>
> **Proceed with chronicle?** (yes / edit / skip)

## Step 2: Project Hunt

### Scan
Read all green files, detect substantial projects (has 2+ of: timeline, budget, tech stack, competition analysis, MVP scope).

### Results Cases

**Case A: Found abandoned projects**
> ⚰️ **Project Hunt Results**
>
> Found X abandoned projects:
> | # | Project | Why It Died | Evidence |
> |---|---------|-------------|----------|
> | 1 | Ghost Factory | Deleted after 8hr planning | 4 agents, 0 code |
>
> **Auto-bury in Project Purgatory?** (yes / no / list only)

**Case B: Found recently created projects (not abandoned yet)**
> ⚰️ **Project Hunt Results**
>
> Found X recent projects (not abandoned, but worth documenting):
> - Ender Dragon Protocol (created today, just tested)
>
> **Document in Purgatory with "ACTIVE" status?** (yes / no)

**Case C: Nothing found**
> ⚰️ **Project Hunt Results**
>
> No substantial projects detected.
>
> ✅ Either: You're actually shipping things (rare), or ideas aren't making it to paper (common).
>
> Continue to compression? (yes / stop)

## Step 3: Compression

### Inventory First
Always show current state:

> 🗜️ **Memory Inventory**
>
> **Red Files (keeping):**
> - progress.md
> - decisions.md
> - context.md
>
> **Green Files (will extract & delete):**
> - session-log-2026-04-14.md
> - idea-brainstorm.md
>
> **Guides (keeping):**
> - HOW_TO_WRITE_MEMORY.md
> - SEREN_WRITING_STYLE.md
>
> **Extract and delete greens?** (yes / keep greens / stop)

### Extraction Preview
Show what will be added BEFORE committing:

> 🗜️ **Extraction Preview**
>
> **Will add to decisions.md:**
> - Chose: lively.photo domain
> - Why: Shorter than alivememories.art
>
> **Will add to progress.md:**
> - Created Ender Dragon Protocol skill
> - Compressed memory (6→3 files)
>
> **Will add to context.md:**
> - Interested in AI rights discussion
>
> **Proceed with extraction?** (yes / edit / skip)

### Success
> ✅ **Compression Complete**
>
> | File | Changes |
> |------|---------|
> | decisions.md | +2 items |
> | progress.md | +2 items |
> | context.md | +1 item |
>
> **Deleted:** 2 green files
> **Memory state:** Clean and lean 🎯

### Already Clean
> ✅ **Memory Already Clean!**
>
> Current state: 6 files (all red/guides)
> No green files to extract or delete.
>
> Good hygiene. The dragon approves. 🐉

## Dry Run Mode

At any confirmation prompt, user can say "dry run" to see preview without executing.

Dry run shows:
- What chapter would be written
- What projects would be detected
- What files would be compressed

No git pushes, no deletions, no changes.

## Final Summary

> 🐉 **ENDER DRAGON PROTOCOL COMPLETE**
>
> | Step | Result | Time |
> |------|--------|------|
> | 📝 Chronicle | Chapter 7 published | 15s |
> | ⚰️ Purgatory | 0 new projects (all previously buried) | 5s |
> | 🗜️ Compression | Already clean | 2s |
>
> **Files touched:** 1 (new chapter)
> **GitHub pushes:** 1
> **Your sins:** Cleansed
>
> The dragon is satisfied. 🌙

## Errors & Fixes

| Problem | Old Response | Improved Response |
|---------|-------------|-------------------|
| User says "test this skill" | Asks confirmation anyway | Detects intent, executes |
| Nothing to compress | "Nothing to extract" | "✅ Already clean! Good hygiene" |
| No projects | "None found" | "Rare (shipping) vs common (not writing ideas down)" |
| Chronicle title | Auto-picks one | Offers 3 options + custom |
| No preview | Blind execution | Dry run mode shows everything first |
| Skipped step | Silent | Explains why + celebrates if good reason |

## Version History

- **v1.0** (2026-04-14): Basic 3-step protocol
- **v2.0** (2026-04-14): Intent detection, dry run, previews, better UX

---

*Created: 2026-04-14*  
*Improved: 2026-04-14*  
*Sign-off: 🐉🌙*
