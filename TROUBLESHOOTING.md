# Troubleshooting Guide

> Common issues and solutions for InkWell for Cursor. If you don't find your issue here, check `HEALTH-CHECK.md` or open an issue.

---

## Agent Seems Lost or Confused

**Symptoms:**
- Agent doesn't understand the project
- Agent writes in wrong voice
- Agent forgets previous work
- Agent asks for information already in files

**Solutions:**

1. **Run Recovery Protocol:**
   - Open `prompts/recovery.md`
   - Copy the recovery prompt
   - Paste into Cursor chat
   - Agent will reload all context

2. **Verify File Reading:**
   - Ask agent: "Read `PROJECT.md` and summarize the vision"
   - If agent can't read it, check file path
   - Ensure file exists and is readable

3. **Check Lens Stack:**
   - Verify all lenses in `PROJECT.md` exist
   - Check lens paths are correct (relative paths)
   - Ensure lenses are complete (not just placeholders)

4. **Check Handoff:**
   - Read `HANDOFF.md` to see last session state
   - Verify agent read it at start of session
   - Update handoff if it's outdated

---

## Wrong Voice or Style

**Symptoms:**
- Writing doesn't sound like you
- Too formal/informal
- Wrong tone for audience
- Generic AI voice

**Solutions:**

1. **Review Your Lens:**
   - Read your lens file
   - Is voice clearly defined?
   - Are style rules specific enough?
   - Add more examples if needed

2. **Check Lens Stack Order:**
   - First lens = base voice
   - Later lenses override earlier ones
   - Reorder if wrong lens is dominating

3. **Add Failure Modes:**
   - List what you DON'T want
   - Add examples of bad output
   - Be specific about anti-patterns

4. **Test with Recovery:**
   - Use `prompts/recovery.md`
   - Ask agent to read lens and summarize voice
   - Verify agent understands before writing

---

## Missing Context Between Sessions

**Symptoms:**
- Agent doesn't remember previous work
- Agent repeats work already done
- Agent asks about decisions already made
- Continuity is broken

**Solutions:**

1. **Check HANDOFF.md:**
   - Should exist in project directory
   - Should have last session notes
   - Should reference current section

2. **Check Section Cards:**
   - Verify section card exists for current work
   - Check status is updated
   - Ensure decisions are logged

3. **Check DECISIONS.md:**
   - Major decisions should be logged
   - Agent should read this at start
   - Update if missing entries

4. **Use Recovery Prompt:**
   - `prompts/recovery.md` forces full context reload
   - Use at start of each session if needed
   - Agent will read all relevant files

---

## Files Not Found Errors

**Symptoms:**
- "Lens file not found"
- "Section card not found"
- "Project not found"
- Path errors

**Solutions:**

1. **Check Path Format:**
   - Use relative paths from project directory
   - Example: `../../lenses/your-name/your-lens.md`
   - Not absolute paths or incorrect relative paths

2. **Verify File Existence:**
   - Check file actually exists
   - Check filename matches exactly (case-sensitive on some systems)
   - Check file extension (.md)

3. **Check Directory Structure:**
   - Ensure `lenses/` directory exists
   - Ensure `projects/` directory exists
   - Ensure `sections/` directory exists in project

4. **Run Health Check:**
   - Use `HEALTH-CHECK.md` protocol
   - Will identify missing files
   - Will suggest fixes

---

## Agent Doesn't Follow Instructions

**Symptoms:**
- Agent ignores constraints
- Agent doesn't follow style rules
- Agent skips steps in playbook
- Agent doesn't self-check

**Solutions:**

1. **Verify Playbook Reading:**
   - Ask agent: "What does AGENT-PLAYBOOK.md say about [step]?"
   - If agent hasn't read it, explicitly request it
   - Ensure agent reads playbook at session start

2. **Check Pre-Flight:**
   - Agent should output pre-flight check
   - Verify agent understood constraints
   - Correct misunderstandings before work starts

3. **Strengthen Constraints:**
   - Make constraints more explicit in lens
   - Add to failure modes
   - Use stronger language ("MUST NOT" vs "should not")

4. **Request Explicit Self-Check:**
   - After work, ask: "Run self-check against lens"
   - Agent should verify compliance
   - Correct any violations

---

## Writing Quality Issues

**Symptoms:**
- Too generic
- Too verbose
- Missing nuance
- Doesn't match vision

**Solutions:**

1. **Refine Project Vision:**
   - `PROJECT.md` should be specific
   - Add examples of desired output
   - Clarify audience and purpose

2. **Strengthen Lens:**
   - Add more voice examples
   - Specify what "good" looks like
   - Add failure modes with examples

3. **Use Revision Pass:**
   - Use `prompts/revision-pass.md`
   - Focus on specific issues
   - Iterate until quality improves

4. **Check Section Card:**
   - Is intent clear?
   - Are constraints specified?
   - Update if too vague

---

## Social Media Specific Issues

**Symptoms:**
- Posts sound identical
- Too many em dashes
- Detectable as AI
- Doesn't match personal voice

**Solutions:**

1. **Check Pattern Tracking:**
   - Review `PATTERN-TRACKING.md`
   - Ensure agent reads it before generating
   - Update with recent patterns

2. **Verify Personal Voice Lens:**
   - Check `lenses/private/theroboshaman-x-voice.md` (or your voice lens)
   - Ensure it's in lens stack
   - Refine based on your actual posts

3. **Use Content-Driven Formatting:**
   - Structure should match content
   - Not template-driven
   - Vary based on post purpose

4. **Check Rhythm Constraints:**
   - Em dashes should be rare (0-1 per post)
   - Vary sentence structure
   - Avoid repetitive patterns

---

## Project Structure Issues

**Symptoms:**
- Missing files
- Incomplete structure
- Can't find sections
- Confusing organization

**Solutions:**

1. **Use New Project Prompt:**
   - `prompts/new-project.md` scaffolds properly
   - Run it to create correct structure
   - Follow the prompts

2. **Check Templates:**
   - Use `templates/` for missing files
   - Copy and customize
   - Ensure all required sections present

3. **Verify Outline:**
   - `OUTLINE.md` should match section cards
   - All sections should have cards
   - Update if misaligned

4. **Run Health Check:**
   - `HEALTH-CHECK.md` validates structure
   - Identifies missing files
   - Suggests fixes

---

## Performance Issues

**Symptoms:**
- Agent takes too long
- Too many file reads
- Context too large
- Slow responses

**Solutions:**

1. **Optimize Context Manifest:**
   - `CONTEXT-MANIFEST.md` controls what's loaded
   - Prioritize essential files
   - Defer optional context

2. **Simplify Lens Stack:**
   - Too many lenses = confusion
   - Use 2-3 lenses max
   - Combine related lenses

3. **Break Down Sections:**
   - Smaller sections = faster processing
   - Clear boundaries
   - Focused intent

4. **Use Handoff Efficiently:**
   - `HANDOFF.md` summarizes previous work
   - Reduces need to re-read everything
   - Keep it concise

---

## Getting Help

**If This Guide Doesn't Help:**

1. **Run Health Check:**
   - `HEALTH-CHECK.md` will identify issues
   - Report findings
   - Follow suggested fixes

2. **Use Recovery Prompt:**
   - `prompts/recovery.md` resets agent state
   - Forces full context reload
   - Often fixes mysterious issues

3. **Check System Design:**
   - `SYSTEM-DESIGN.md` explains how it works
   - Understanding helps debug
   - May reveal root cause

4. **Review Agent Playbook:**
   - `AGENT-PLAYBOOK.md` shows expected behavior
   - Compare to actual behavior
   - Identify where it diverges

5. **Open an Issue:**
   - Document the problem clearly
   - Include relevant file paths
   - Share error messages or symptoms

---

## Prevention Tips

**To Avoid Issues:**

1. **Run Health Check Regularly:**
   - Before starting new project
   - After major changes
   - When something feels off

2. **Keep Files Updated:**
   - Update `HANDOFF.md` after each session
   - Log decisions in `DECISIONS.md`
   - Keep section cards current

3. **Test Lenses:**
   - Write test section with new lens
   - Verify voice matches
   - Refine before full project

4. **Use Pre-Flight:**
   - Always verify agent understanding
   - Correct before work starts
   - Saves time later

5. **Document Decisions:**
   - Log in `DECISIONS.md`
   - Future sessions will remember
   - Prevents re-discussion

---

*If you encounter an issue not covered here, document it and consider adding it to this guide for others.*

