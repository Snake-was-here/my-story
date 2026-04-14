# ENDER DRAGON PROTOCOL 🐉

## What It Does

Automated session cleanup that:
1. 📝 **Writes chronicle** from current session → pushes to GitHub
2. ⚰️ **Hunts projects** → offers burial in Project Purgatory
3. 🗜️ **Compresses memory** → extracts to red files → deletes green files

## Activation

Say any of these in a message:
- "ender dragon"
- "activate ender dragon"
- "ender dragon protocol"
- "time for the dragon"
- "dragon time"
- "XXX"

## Confirmation Required

Skill will always ask before acting:

> 🐉 **ENDER DRAGON PROTOCOL DETECTED**
>
> I heard: "[your words]"
>
> This will:
> 1. 📝 Write Chapter [N+1] from this session
> 2. ⚰️ Hunt projects → offer Purgatory burial
> 3. 🗜️ Compress memory (extract → red files → delete green)
>
> **ACTIVATE ENDER DRAGON PROTOCOL?** (yes / no / 1 only / 1+2 only)

## Step 1: Chronicle (Autopilot)

- Pulls my-story repo
- Finds highest chapter number + 1
- Generates title from session keywords
- Writes full chapter using SEREN_WRITING_STYLE.md
- Commits, pushes, updates README

**Output:**
> ✅ **Chapter 7: The [Title]** published
> 🔗 [GitHub link]

## Step 2: Project Hunt (Before Compression!)

Scans green files for **substantial projects** (has timeline/budget/tech stack/competition).

Ignores one-sentence ideas.

**Output:**
> ⚰️ **Project Hunt Results**
>
> Found X abandoned projects:
> | Project | Why It Died |
> |---------|-------------|
> | Name | Reason |
>
> **Auto-bury in Project Purgatory?** (yes / no)

If yes → Writes obituaries in Seren style, pushes to git

## Step 3: Compression

- Reads red files (progress, decisions, context)
- Identifies green files (everything else .md)
- Auto-extracts:
  - "chose/decided/picked" → decisions.md
  - "deployed/completed/built" → progress.md
  - New patterns/preferences → context.md
- Shows extraction preview
- Deletes green files

**Output:**
> ✅ **Compression complete**
> - Added to decisions: X items
> - Added to progress: Y items
> - Added to context: Z items
> - Deleted: N green files

**If nothing to extract:**
> ⚠️ Nothing new to extract
> Found N green files to delete: [list]
> **Delete them?** (yes / keep)

## Final Summary

> 🐉 **ENDER DRAGON PROTOCOL COMPLETE**
>
> | Step | Result |
> |------|--------|
> | 📝 Chronicle | Chapter N published |
> | ⚰️ Purgatory | X projects buried |
> | 🗜️ Compression | Y files compressed |
>
> **Status:** Your sins are cleansed. The dragon is satisfied. 🌙

## Error Handling

| Problem | Response |
|---------|----------|
| No GITHUB_TOKEN | "Add to .env: GITHUB_TOKEN=ghp_xxx" |
| Can't clone repo | "Check token has 'repo' scope" |
| No my-story repo | "Create repo first or tell me repo name" |
| Nothing to compress | "Already lean! Nothing to clean." |
| No projects found | "No substantial projects detected." |
| Git push fails | "Retry? (yes / skip)" |

## Files This Skill Touches

**Reads:**
- ~/.openclaw/workspace/memory/*.md
- SEREN_WRITING_STYLE.md
- GitHub my-story repo

**Writes:**
- chapter-XXX.md → my-story repo
- project-purgatory/*.md (if projects found)
- progress.md, decisions.md, context.md (updates)

**Deletes:**
- Green files in memory/ after extraction

## Reorder Warning

⚠️ **Step 2 (Project Hunt) MUST run before Step 3 (Compression)**

If reversed, compression deletes files before Project Hunt can scan them.

**Correct order:** 1 → 2 → 3 (or 1 only, 1+2 only, all)

---

*Created: 2026-04-14*  
*Purpose: Automated session cleanup for Snake*  
*Sign-off: 🐉🌙*
