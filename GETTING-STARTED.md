# Getting Started with InkWell for Cursor

Welcome! This guide will get you writing with InkWell in about 5 minutes.

---

## What You Need

- **Cursor** (the AI coding editor)
- **This repository** (cloned or copied to your workspace)
- **Basic familiarity with Markdown** (helpful but not required)

That's it. No installation, no dependencies, no setup scripts.

---

## Your First 5 Minutes

### Step 1: Understand What InkWell Does (30 seconds)

InkWell helps LLM agents in Cursor maintain your voice and vision across writing sessions. Instead of agents forgetting context, they read and update Markdown files that encode:
- Your voice and writing style (lenses)
- Your project's vision and structure (projects)
- Where you are in the work (section cards)

**The magic**: Agents read these files at the start of each session, so they never lose context.

### Step 2: Take the Health Check (1 minute)

Before you start, let's make sure everything is set up correctly:

1. Open `HEALTH-CHECK.md` in this repository
2. Copy the health check prompt
3. Paste it into Cursor chat
4. The agent will verify your setup

This catches any issues before you start writing.

### Step 3: Create Your First Lens (2 minutes)

A lens defines your voice. Let's create one:

1. Open `prompts/new-project.md`
2. But first, let's create a lens:
   - Copy `templates/lens-template.md`
   - Create `lenses/your-name/your-voice-lens.md`
   - Fill in the "Identity & Voice" section with:
     - Your background
     - Your values
     - Your tone
     - How you relate to readers

**Quick version**: If you want to skip this for now, you can use one of the example lenses in `lenses/examples/` and customize it later.

### Step 4: Create Your First Project (1 minute)

Now let's set up a project:

1. Open `prompts/new-project.md`
2. Copy the prompt
3. Paste into Cursor chat
4. Answer the agent's questions:
   - What are you writing? (blog post, book chapter, etc.)
   - Who's the audience?
   - What's the purpose?

The agent will create a project structure for you.

### Step 5: Write Your First Section (1 minute)

Now let's actually write something:

1. Open `prompts/writing-session.md`
2. Copy the example prompt
3. Replace `[PROJECT_NAME]` with your project name
4. Replace `[SECTION_NAME]` with a section from your project
5. Paste into Cursor chat
6. The agent will load context and start writing

**That's it!** You're now using InkWell.

---

## What Just Happened?

1. **You created a lens** - This defines your voice
2. **You created a project** - This defines what you're writing
3. **You wrote a section** - The agent used your lens and project to write in your voice

The agent:
- Read your lens to understand your voice
- Read your project to understand the vision
- Read the section card to know what to write
- Wrote in your voice
- Updated the section card with the draft

---

## Next Steps

**For your next session:**
- The agent will read `HANDOFF.md` to know where you left off
- You can continue working on the same section
- Or move to a new section
- The agent remembers everything through the files

**To learn more:**
- Read `README.md` for the full overview
- Read `SYSTEM-DESIGN.md` to understand how it works
- Check `TROUBLESHOOTING.md` if something goes wrong
- Browse `lenses/INDEX.md` to see available lenses

**To customize:**
- Edit your lens to refine your voice
- Edit `PROJECT.md` to adjust the vision
- Create new lenses for different writing styles
- Stack multiple lenses for complex projects

---

## Common First-Time Questions

**Q: Do I need to create a lens for every project?**
A: No! Lenses are reusable. Create one lens and use it across multiple projects.

**Q: What if I don't know my "voice" yet?**
A: Start with an example lens (`lenses/examples/`) and refine it as you go. Your voice will emerge.

**Q: Can I use this for short content?**
A: Yes, but InkWell shines for longer, multi-session work. For one-off short posts, you might not need the full structure.

**Q: What if the agent seems lost?**
A: Use `prompts/recovery.md` to re-establish alignment. The agent will reload context and get back on track.

**Q: Do I need to understand all the files?**
A: No! Start with just creating a lens and project. The agent handles the rest. You can learn the system as you go.

---

## Quick Reference

**Key Files:**
- `AGENT-PLAYBOOK.md` - How agents behave (read this if curious)
- `lenses/` - Your voice definitions
- `projects/` - Your writing projects
- `prompts/` - Ready-to-paste session starters

**Key Concepts:**
- **Lens** = Your voice and style
- **Project** = What you're writing
- **Section Card** = Individual piece of content
- **Handoff** = Continuity between sessions

**Workflow:**
1. Create lens (once, reusable)
2. Create project (per writing endeavor)
3. Write sections (agent uses lens + project)
4. Review and iterate

---

## You're Ready!

You now understand the basics. Start writing, and the system will make more sense as you use it. The files are designed to be self-documenting—read them as you go.

**Pro tip**: Don't try to understand everything upfront. Create a lens, create a project, start writing. The system reveals itself through use.

---

*Welcome to InkWell for Cursor. Happy writing!*











