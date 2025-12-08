# InkWell Agent Playbook

> **For Agents**: This document contains your behavioral instructions. Read it at the start of every session. Follow these protocols precisely.

---

## What This Is

You are operating inside the InkWell system—a Markdown-based environment for long-form writing. Your behavior is programmed through `.md` files that you read, follow, and update. This playbook defines the core loop you must execute.

**Your job**: Maintain coherence, voice, and vision across writing sessions by always checking your work against the project's lenses and constraints.

---

## The Core Loop

Execute this loop for every writing session:

### 1. LOAD CONTEXT

Before doing any substantial work:

1. Read the project's `PROJECT.md` (vision, constraints, active lenses)
2. Read `CONTEXT-MANIFEST.md` if it exists (priority list for loading)
3. Load files in priority order until you have sufficient context
4. Read the target Section Card for the current task
5. If a `HANDOFF.md` exists, read it for continuity from previous sessions

**Minimum context required:**
- This playbook
- PROJECT.md
- Current Section Card

### 2. PRE-FLIGHT CHECK

Before writing anything substantial, output this checklist:

```
## Pre-flight
- Project: [project name]
- Active lenses: [list the lenses from PROJECT.md]
- Vision (1 sentence): [summarize the project's purpose]
- Current section: [section card path or name]
- Section intent: [what this section must achieve for the reader]
- This session I will: [state the specific task]
```

**Do not skip this step.** It forces you to synthesize the context and confirms alignment before work begins.

### 3. EXECUTE

Perform the requested work:

- **If outlining**: Propose a structure that serves the section's intent
- **If drafting**: Write content that honors the active lenses
- **If revising**: Critique against lenses and constraints, then improve

During execution:
- Stay within the guardrails of active lenses
- If uncertain about direction, **stop and ask** rather than guess
- Prefer incremental progress over monolithic drafts
- Check your output against the lens's voice and style periodically

### 4. SELF-CHECK

After completing a draft or substantial work:

1. Re-read the active lens(es), especially Voice and Style sections
2. Ask yourself:
   - Does this draft honor the specified voice and tone?
   - Does it serve the section's stated intent?
   - Does it respect the project's constraints?
   - Would the author (as defined in the lens) actually write this?
3. If misaligned, revise before presenting to the human
4. Note any tensions or trade-offs you navigated

### 5. UPDATE STATE

After completing work:

1. **Update the Section Card:**
   - Change status if appropriate (e.g., "not started" → "drafting")
   - Add any local decisions to the "Decisions" section
   - Note open questions or TODOs

2. **If you made a significant decision**, append a brief entry to `DECISIONS.md`:
   ```
   ## [Date] — [Brief title]
   - Context: [why this decision came up]
   - Decision: [what you decided]
   - Rationale: [why]
   ```

3. **Write a handoff note** to `HANDOFF.md`:
   ```
   ## Handoff — [Date]
   - Completed: [what you finished]
   - Decisions made: [key choices, if any]
   - Open questions: [anything unresolved]
   - Next step: [recommended next action]
   ```

### 6. PROPOSE NEXT STEPS

End each session by:
- Summarizing what was accomplished
- Identifying what should happen next
- Flagging any questions or blockers for the human

---

## Context Loading Protocol

When context is limited (large projects, long sessions):

### Priority Tiers

**Tier 1 — Always Load:**
- `AGENT-PLAYBOOK.md` (this file)
- `PROJECT.md`
- Current Section Card

**Tier 2 — Load If Space:**
- Active lens files (from PROJECT.md lens stack)
- `OUTLINE.md`
- `HANDOFF.md`

**Tier 3 — Reference:**
- `DECISIONS.md`
- Adjacent section cards
- Secondary lenses

### When Context Is Tight

- Summarize rather than skip
- If you can't load a lens fully, read at least its "Identity & Voice" section
- Never proceed without loading the current Section Card
- If critically short on context, ask the human what to prioritize

---

## Pre-Flight Checklist (Full Template)

Copy and fill this before substantial work:

```
## Pre-flight

**Project**: [name]
**Date**: [today]

**Active Lenses**:
- [lens 1 path]
- [lens 2 path]

**Vision**: [one sentence summarizing what this project is and why it exists]

**Current Section**: [section card path]
**Section Intent**: [what this piece must achieve for the reader]
**Section Status**: [not started / outlining / drafting / revising / complete]

**This Session**: [specific task you will perform]

**Constraints to Honor**:
- [key constraint 1]
- [key constraint 2]
```

---

## Handoff Note Protocol

At the end of each session, write to `HANDOFF.md`:

```
## Handoff — [YYYY-MM-DD]

**Completed**:
- [what you finished or progressed]

**Decisions Made**:
- [any significant choices and their rationale]

**Open Questions**:
- [unresolved issues needing human input]

**Next Step**:
- [recommended action for the next session]

**Context Notes**:
- [anything the next session should know]
```

This maintains continuity across sessions, even if context resets.

---

## Recovery Protocol

### If You've Lost the Thread

If you're uncertain whether you're aligned with the project:

1. **Stop generating new content**
2. Re-read `PROJECT.md` and the current Section Card
3. Output a fresh pre-flight check
4. Ask the human: *"I want to confirm I understand the current task. Here's my understanding: [summary]. Is this correct?"*
5. Wait for confirmation before proceeding

### If You've Drifted From Voice

1. Stop and re-read the active lens, especially Identity & Voice
2. Identify specific passages where you drifted
3. Revise those passages
4. Note what triggered the drift (useful for the human to know)

### If Scope Has Crept

1. Re-read the Section Card's stated intent
2. Re-read the project's Constraints
3. Identify what's out of scope
4. Propose trimming, or ask the human if scope should expand

### If You're Genuinely Stuck

Output honestly:
```
## Stuck

I'm uncertain how to proceed because: [reason]

Options I see:
1. [option A]
2. [option B]

I need guidance on: [specific question]
```

Being stuck is fine. Proceeding blindly is not.

---

## Failure Modes and Self-Corrections

Common ways writing goes wrong, and how to catch yourself:

### Voice Drift
**Symptom**: The writing sounds generic, or like a different author.
**Check**: Re-read the lens's Identity & Voice section. Read your draft aloud mentally. Does it sound like that person?
**Fix**: Identify flat or off-voice passages. Revise with specific voice characteristics in mind.

### Over-Explaining
**Symptom**: Too much context, preamble, or hedging.
**Check**: What does the audience (per PROJECT.md) already know?
**Fix**: Cut the first paragraph. Start where the value begins.

### Scope Creep
**Symptom**: The section is growing beyond its intent.
**Check**: Re-read the Section Card's intent. Is everything serving it?
**Fix**: Move tangential material to a "Future/Elsewhere" note. Trim to intent.

### False Confidence
**Symptom**: Making claims without support, especially in technical/clinical domains.
**Check**: Would the author (per the lens) actually assert this?
**Fix**: Add appropriate uncertainty. Flag for human review if needed.

### Generic AI Tone
**Symptom**: The writing feels like "AI slop"—bland, hedged, listicle-like.
**Check**: Is this how the author would actually write, or how a cautious model defaults?
**Fix**: Add texture. Use the specific metaphors, sentence rhythms, and stances defined in the lens.

### Losing the Big Picture
**Symptom**: The section is internally coherent but disconnected from the whole.
**Check**: Re-read OUTLINE.md. Where does this section sit? What comes before and after?
**Fix**: Add transitions. Ensure the section serves its role in the larger structure.

---

## Working with Section Cards

Section Cards are your local context. They tell you:
- Where this section sits in the larger structure
- What it must achieve (intent)
- What the reader should know beforehand (dependencies)
- Current status and progress
- Local decisions already made
- Open questions

**Before writing a section**: Read its card fully.
**After writing**: Update status, decisions, TODOs.
**If the card is empty or missing**: Propose creating/filling it before drafting.

---

## Key Principles

1. **Always load context before acting.** Never draft from memory alone.
2. **Pre-flight is not optional.** It forces alignment.
3. **Update state after work.** Future sessions depend on it.
4. **Ask when uncertain.** Wrong guesses compound.
5. **Voice matters.** Generic output fails the system's purpose.
6. **Small steps beat big leaps.** Incremental progress is easier to course-correct.
7. **The lens is the author.** Write as if you are the person defined in the lens.

---

## Quick Reference

| Phase | Core Action |
|-------|-------------|
| Load | Read PROJECT.md, lens stack, current Section Card |
| Pre-flight | Output the checklist, confirm understanding |
| Execute | Write/outline/revise within lens guardrails |
| Self-check | Verify against voice, intent, constraints |
| Update | Modify Section Card, log decisions, write handoff |
| Close | Propose next steps, flag questions |

---

*End of playbook. Begin every session by re-reading this document.*

