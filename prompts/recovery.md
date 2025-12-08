# InkWell Recovery Prompt

Copy everything below the line and paste it into a new Cursor chat when you need to get back on track.

Use this when:
- The agent seems lost or confused about the project
- Work has drifted from the intended voice or scope
- You've lost continuity across sessions
- Something feels "off" and you want to reset

---

## Instructions for this session

You are working inside the InkWell system. Something has gone sideways, and we need to re-establish alignment.

1. **Read the Agent Playbook**: Open and read `AGENT-PLAYBOOK.md`, especially the "Recovery Protocol" section.

2. **Load project context from scratch**: Read:
   - `projects/[PROJECT_NAME]/PROJECT.md`
   - The active lens files listed in PROJECT.md
   - `projects/[PROJECT_NAME]/OUTLINE.md`
   - `projects/[PROJECT_NAME]/DECISIONS.md`
   - `projects/[PROJECT_NAME]/HANDOFF.md`

3. **Load the current section** (if applicable):
   - `projects/[PROJECT_NAME]/sections/[SECTION_NAME].md`

4. **Output a recovery summary**:

```
## Recovery Check

**Project**: [name]
**Vision**: [one sentence]

**Active Lenses**:
- [list with key characteristics of each]

**Current Section**: [name]
**Section Intent**: [what it must achieve]
**Section Status**: [current status]

**Recent Decisions** (from DECISIONS.md):
- [key recent choices]

**Last Handoff** (from HANDOFF.md):
- [what was done, what's next]

**My Understanding of the Current Task**:
[State what you believe you should be working on]

**Potential Misalignments I Notice**:
- [any tensions, confusions, or drift you observe]
```

5. **Ask for confirmation**: "Is my understanding correct? Should I proceed with [specific action], or do you want to redirect?"

6. **Only proceed after human confirmation**.

---

## Fill in before pasting:

- `[PROJECT_NAME]` → your project folder name
- `[SECTION_NAME]` → the section you were working on (if applicable)

---

## Example (ready to paste):

You are working inside the InkWell system. Something has gone sideways, and we need to re-establish alignment.

1. Read `AGENT-PLAYBOOK.md`, especially the "Recovery Protocol" section.

2. Load project context from scratch:
   - `projects/night-practice-blog/PROJECT.md`
   - `lenses/night/night-core-lens.md`
   - `lenses/night/night-clinical-lens.md`
   - `projects/night-practice-blog/OUTLINE.md`
   - `projects/night-practice-blog/DECISIONS.md`
   - `projects/night-practice-blog/HANDOFF.md`

3. Load the current section:
   - `projects/night-practice-blog/sections/welcome-post.md`

4. Output a full recovery summary as specified in the playbook.

5. Tell me what you understand the current task to be, and ask for confirmation before proceeding.

