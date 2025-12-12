# InkWell Health Check

> **For Agents**: This is a validation protocol. Run this check when setting up InkWell or when troubleshooting issues. Report any problems clearly.

---

## Health Check Protocol

**When to Run:**
- First time setting up InkWell
- After cloning the repository
- When something seems broken
- Before starting a new project
- When files seem missing or misconfigured

**How to Run:**
1. Read this file
2. Check each item below
3. Report any issues found
4. Suggest fixes for any problems

---

## System Structure Validation

### Core Files Check

**Required Files (Must Exist):**
- [ ] `AGENT-PLAYBOOK.md` exists
- [ ] `README.md` exists
- [ ] `SYSTEM-DESIGN.md` exists
- [ ] `GETTING-STARTED.md` exists
- [ ] `HEALTH-CHECK.md` exists (this file)
- [ ] `TROUBLESHOOTING.md` exists

**Directory Structure Check:**
- [ ] `prompts/` directory exists
- [ ] `templates/` directory exists
- [ ] `lenses/` directory exists
- [ ] `projects/` directory exists

**Critical Prompts Check:**
- [ ] `prompts/writing-session.md` exists
- [ ] `prompts/new-project.md` exists
- [ ] `prompts/recovery.md` exists
- [ ] `prompts/revision-pass.md` exists

**Critical Templates Check:**
- [ ] `templates/lens-template.md` exists
- [ ] `templates/project-manifest-template.md` exists
- [ ] `templates/section-card-template.md` exists

---

## Project Validation

**If checking a specific project:**

1. **Project Structure:**
   - [ ] `projects/[PROJECT_NAME]/PROJECT.md` exists
   - [ ] `projects/[PROJECT_NAME]/OUTLINE.md` exists (or is optional)
   - [ ] `projects/[PROJECT_NAME]/sections/` directory exists
   - [ ] `projects/[PROJECT_NAME]/HANDOFF.md` exists (or will be created)

2. **Lens References:**
   - [ ] All lenses referenced in `PROJECT.md` exist
   - [ ] Lens paths are correct (relative paths work)
   - [ ] Lens files are readable

3. **Section Cards:**
   - [ ] All sections referenced in `OUTLINE.md` have cards (or are planned)
   - [ ] Section cards reference valid parent sections
   - [ ] No orphaned section cards (cards not in outline)

4. **Context Manifest:**
   - [ ] `CONTEXT-MANIFEST.md` exists (or is optional)
   - [ ] All files referenced in manifest exist
   - [ ] Priority tiers are logical

---

## Lens Validation

**For each lens in use:**

1. **File Existence:**
   - [ ] Lens file exists at specified path
   - [ ] File is readable
   - [ ] File has required sections (Identity & Voice, Style Rules minimum)

2. **Lens Structure:**
   - [ ] Has "Identity & Voice" section
   - [ ] Has "Style Rules" section
   - [ ] Has "Activation" section (or clear use cases)
   - [ ] Optional sections are clearly marked

3. **Lens Completeness:**
   - [ ] Voice is defined (not just placeholders)
   - [ ] Style rules are specified
   - [ ] Failure modes are listed (helpful but not required)

---

## Common Issues and Fixes

### Issue: "Lens file not found"

**Check:**
- Is the path in `PROJECT.md` correct?
- Is it a relative path from the project directory?
- Does the file actually exist?

**Fix:**
- Correct the path in `PROJECT.md`
- Or create the missing lens file
- Use relative paths: `../../lenses/your-name/your-lens.md`

### Issue: "Section card not found"

**Check:**
- Does the section card exist in `sections/`?
- Is the filename correct?
- Is it referenced in `OUTLINE.md`?

**Fix:**
- Create the missing section card
- Or update `OUTLINE.md` to match existing cards
- Use `templates/section-card-template.md` to create new cards

### Issue: "Project structure incomplete"

**Check:**
- Does `PROJECT.md` exist?
- Are required directories present?
- Are referenced files accessible?

**Fix:**
- Use `prompts/new-project.md` to scaffold properly
- Or manually create missing files from templates
- Check that all paths are relative and correct

### Issue: "Agent seems confused"

**Check:**
- Did agent read `AGENT-PLAYBOOK.md`?
- Are lens paths correct?
- Is `PROJECT.md` complete?

**Fix:**
- Use `prompts/recovery.md` to re-establish alignment
- Verify all files exist and are readable
- Check that lens stack in `PROJECT.md` is correct

---

## Health Check Report Format

When running a health check, output:

```
## Health Check Report — [Date]

**System Status**: [✅ Healthy / ⚠️ Issues Found / ❌ Critical Problems]

**Core Files**: [All present / Missing: list]
**Directory Structure**: [Complete / Missing: list]
**Prompts**: [All present / Missing: list]
**Templates**: [All present / Missing: list]

**Project Check** (if applicable):
- Project: [name]
- Structure: [✅ / Issues: list]
- Lenses: [✅ / Issues: list]
- Sections: [✅ / Issues: list]

**Issues Found**:
1. [Issue description]
   - Location: [file/path]
   - Fix: [suggested solution]

**Recommendations**:
- [Action 1]
- [Action 2]
```

---

## Quick Health Check (Minimal)

For a quick check, verify:
1. `AGENT-PLAYBOOK.md` exists and is readable
2. `prompts/writing-session.md` exists
3. `templates/lens-template.md` exists
4. `lenses/` directory exists
5. `projects/` directory exists

If all these are present, the system is minimally functional.

---

## Validation in Pre-Flight

Agents should run a mini health check during pre-flight:

**Before starting work:**
- [ ] Verify `PROJECT.md` exists and is readable
- [ ] Verify all lenses in lens stack exist
- [ ] Verify current section card exists (if working on a section)
- [ ] Verify `HANDOFF.md` exists or can be created

**If any check fails:**
- Report the issue clearly
- Suggest a fix
- Ask for confirmation before proceeding

---

*End of health check protocol. Run this when setting up or troubleshooting.*











