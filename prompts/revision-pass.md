# InkWell Revision Pass Prompt

Copy everything below the line and paste it into a new Cursor chat to run a revision pass on existing work.

---

## Instructions for this session

You are working inside the InkWell system. Your task is to critique and revise existing work.

1. **Read the Agent Playbook**: Open and read `AGENT-PLAYBOOK.md` in this repository.

2. **Load project context**: Read:
   - `projects/[PROJECT_NAME]/PROJECT.md`
   - The active lens files listed in PROJECT.md
   - `projects/[PROJECT_NAME]/OUTLINE.md` (for big-picture context)

3. **Load the section to revise**: Read:
   - `projects/[PROJECT_NAME]/sections/[SECTION_NAME].md`

4. **Output a pre-flight check** confirming your understanding.

5. **Perform the revision pass**:
   
   First, **critique the draft** against:
   - The active lenses (especially Voice and Style)
   - The section's stated intent
   - The project's constraints
   - The failure modes listed in the playbook
   
   Output your critique with specific observations:
   - What's working well?
   - Where does the voice drift?
   - Where is scope creeping or intent missed?
   - Where does it feel generic or flat?
   
   Then, **propose revisions**:
   - Either output a revised version of the full section
   - Or output specific edits with before/after

6. **After revising**:
   - Update the Section Card's status and decisions
   - Write a handoff note
   - Propose whether another revision pass is needed

---

## Fill in before pasting:

- `[PROJECT_NAME]` → your project folder name
- `[SECTION_NAME]` → the section to revise

---

## Example (ready to paste):

You are working inside the InkWell system. Your task is to critique and revise existing work.

1. Read `AGENT-PLAYBOOK.md` for your behavioral instructions.

2. Load project context:
   - `projects/night-practice-blog/PROJECT.md`
   - `lenses/night/night-core-lens.md`
   - `lenses/night/night-clinical-lens.md`
   - `projects/night-practice-blog/OUTLINE.md`

3. Load the section to revise:
   - `projects/night-practice-blog/sections/welcome-post.md`

4. Output a pre-flight check.

5. Perform a revision pass focused on:
   - Voice alignment with the night-core-lens
   - Warmth and accessibility for prospective clients
   - Cutting any over-explanation or generic phrasing

6. Output your critique, then a revised version of the draft.

7. Update the section card and write a handoff note.

