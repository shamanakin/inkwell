# InkWell

**English-as-code for long-form writing with LLM agents.**

---

## The Premise

Natural language is the native programming language of LLMs.

Most AI tooling wraps models in traditional code—Python scripts, APIs, CLI tools. This adds complexity and creates a translation layer between human intent and model behavior.

InkWell takes a different approach: write instructions in English, structure them in Markdown, and let the LLM execute them directly. The `.md` files *are* the code.

No scripts. No CLI. No dependencies. Just Markdown files that agents read, follow, and update.

---

## What It Does

Writing with LLMs typically fails in one of two ways:

1. **Context drift**: The agent forgets the voice, vision, or constraints over time.
2. **Generic output**: The writing sounds like an AI, not a specific author.

InkWell solves both by externalizing the "thinking environment" into navigable Markdown files. Agents don't just receive instructions—they actively consult and update files that encode:

- **Who is writing** (voice, values, style)
- **What is being written** (vision, scope, structure)
- **Where we are** (current section, decisions made, open questions)

The result: agents stay aligned across sessions, producing coherent work that sounds like *you*.

---

## Philosophy

### English as Code

The core insight: LLMs don't need Python to be programmed. They need clear instructions in their native format—natural language. InkWell leans into this:

- The "source code" is human-readable prose
- Debugging means reading and revising English
- Portability: works anywhere you can paste text into an LLM

### Files Are Memory

LLMs don't have persistent memory across sessions. InkWell uses a simpler solution than RAG or fine-tuning: **structured files that agents read and write**.

Before acting, agents read the relevant files. After acting, they update them. The file system *is* the memory. This means:

- Transparent: you can see exactly what the agent "knows"
- Editable: you can directly modify the memory
- Debuggable: problems are visible in the files
- Portable: just copy the folder

### Voice as Architecture

Most LLM writing sounds like LLMs. This isn't a prompting failure—it's a systems failure. Voice isn't something you add at the end; it's something that must be encoded in the system itself.

InkWell treats voice (lenses) as first-class objects:
- Defined explicitly in dedicated files
- Consulted before and after writing
- Used for self-checking and revision
- Composable and reusable across projects

### Recursive Self-Reference

The system's power comes from loops:

```
load context → act → self-check → update state → repeat
```

Each step involves reading structured files. The "self-check" step explicitly requires agents to re-read the lens and compare their output. The "update state" step creates artifacts that future sessions can read.

This creates continuity without magic. The agent doesn't "remember"—it reads its own notes.

---

## Core Concepts

### Lenses

Reusable definitions of *how to think and write*. A lens might encode:
- An author's voice and values
- A writing style (clinical, essayistic, educational)
- Domain expertise (psychotherapy, technology, etc.)
- Process preferences (outline first, check frequently, etc.)

Lenses are composable. Stack them for your project (e.g., "my voice + clinical domain + blog format").

### Projects

The *what*—a specific writing endeavor. Each project has:
- `PROJECT.md`: Vision, audience, constraints, active lenses
- `OUTLINE.md`: Structure and hierarchy
- `CONTEXT-MANIFEST.md`: What to load and in what order
- `DECISIONS.md`: Log of significant choices
- `HANDOFF.md`: Notes for session continuity
- `sections/`: Individual section cards

### Section Cards

Local context for each piece of content. A card tracks:
- Intent (what this section must achieve)
- Status (not started → drafting → revising → complete)
- Decisions made
- Open questions and TODOs
- The draft itself

### The Agent Playbook

The behavioral core. `AGENT-PLAYBOOK.md` tells agents exactly how to operate:
1. Load context (project, lenses, section card)
2. Output a pre-flight check (confirm understanding)
3. Execute the work
4. Self-check against lenses and constraints
5. Update section cards and logs
6. Propose next steps

---

## Intent Router

Not all writing is the same. InkWell now includes an **Intent Router** that configures the system based on what you're writing for:

| Intent | What It's For | Lens | Output |
|--------|---------------|------|--------|
| **HARVEST** | Brain dumps, voice notes | None (freeform) | `Database/raw-seeds/` |
| **POSTERITY** | Brainstorming, journaling | Core (optional) | `WRITING/personal/` |
| **THINKPIECE** | Personal essays | Essayist | `WRITING/thinkpieces/` |
| **PUBLISH** | Blog posts, articles | Publishing | `WRITING/publish/` |

The Intent Router determines which lens to load and where to save output. See `INTENT-ROUTER.md` for full details.

---

## PUBLISH Circuit

When intent is PUBLISH and the piece is complete, the **PUBLISH circuit** converts your Markdown to a properly formatted `.docx` file:

1. Runs a formatting check
2. Converts via Pandoc (headings, bold, italics preserved)
3. Outputs a file ready for platform upload

**Prerequisite**: Install [Pandoc](https://pandoc.org/installing.html) (one-time setup).

See `circuits/PUBLISH.md` for the full workflow.

---

## Structure

```
inkwell/
├── AGENT-PLAYBOOK.md         # How agents should behave
├── INTENT-ROUTER.md          # Writing intent routing logic
├── SYSTEM-DESIGN.md          # Deeper design documentation
├── circuits/                 # Operational circuits
│   └── PUBLISH.md            # Markdown → .docx conversion
├── prompts/                  # Ready-to-paste session starters
│   ├── writing-session.md
│   ├── new-project.md
│   ├── revision-pass.md
│   └── recovery.md
├── templates/                # Generic templates
│   ├── lens-template.md
│   ├── project-manifest-template.md
│   ├── section-card-template.md
│   └── context-manifest-template.md
├── lenses/                   # Reusable voice/style/domain lenses
│   ├── publishing-lens.md    # For public-facing content
│   └── examples/
└── projects/                 # Writing projects
    └── example-blog/
```

---

## Quick Start

### 1. Clone or copy this repo

```bash
git clone https://github.com/shamanakin/inkwell.git
```

### 2. Explore the structure

Open any of the example files to see how projects, lenses, and section cards work together.

### 3. Use an existing project or create your own

**To use the example project:**
1. Open `prompts/writing-session.md`
2. Copy the example prompt at the bottom
3. Paste into Cursor (or your LLM interface)
4. The agent will load context and begin work

**To create a new project:**
1. Open `prompts/new-project.md`
2. Follow the instructions to scaffold a new project
3. The agent will ask questions and create the structure

### 4. Customize lenses for your voice

1. Copy `templates/lens-template.md` to `lenses/`
2. Fill in the sections that matter (you don't need all of them)
3. Reference your lens in your project's `PROJECT.md`

---

## How Sessions Work

A typical InkWell session:

1. **You** paste a prompt from `prompts/` into Cursor
2. **Agent** reads the playbook, project, and section card
3. **Agent** outputs a pre-flight check (you verify it's aligned)
4. **Agent** does the work (outline, draft, revise)
5. **Agent** self-checks against the lenses
6. **Agent** updates the section card and writes a handoff note
7. **You** review and approve (or request changes)

The key: agents always check back against the lenses and project. They don't drift because they're constantly re-anchoring.

---

## When to Use InkWell

**Good fit:**
- Long-form writing that needs consistent voice
- Multi-session projects where context would otherwise be lost
- Ghost-writing or writing-as-someone-else scenarios
- Content series with shared voice/style
- Books, guides, courses, essay collections

**Less ideal:**
- One-off short content
- Highly technical documentation (may need different tooling)
- Real-time collaborative writing

---

## Origins

InkWell was built on the principle that LLMs are fundamentally language machines, not code machines. Instead of wrapping them in traditional programming constructs, InkWell meets them where they are: structured natural language.

It's part of the BEOS (BrightEyed Operating System) ecosystem of AI-assisted productivity tools, alongside:
- **InfoHunter**: Research and discovery
- **Lens Atlas**: Modular cognitive engines

---

## License

MIT. Use it, adapt it, make it yours.

---

*InkWell treats English as code and Markdown as a universal instruction format. The result: coherent, voice-aligned long-form writing across sessions.*
