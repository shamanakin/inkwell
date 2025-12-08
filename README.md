# InkWell

**English-as-code for long-form writing with LLM agents.**

InkWell is a Markdown-based system that programs LLM agent behavior through natural language. Agents navigate structured `.md` files to maintain coherence, voice, and vision across long-form writing—from blog posts to books.

No scripts. No CLI. Just Markdown files that agents read, follow, and update.

---

## The Core Idea

Writing with LLMs typically fails in one of two ways:

1. **Context drift**: The agent forgets the voice, vision, or constraints over time.
2. **Generic output**: The writing sounds like an AI, not a specific author.

InkWell solves both by externalizing the "thinking environment" into navigable Markdown files. Agents don't just receive instructions—they actively consult and update files that encode:

- **Who is writing** (voice, values, style)
- **What is being written** (vision, scope, structure)
- **Where we are** (current section, decisions made, open questions)

The result: agents stay aligned across sessions, producing coherent work that sounds like *you*.

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

## Quick Start

### 1. Clone or copy this repo

```bash
git clone https://github.com/[you]/inkwell.git
```

### 2. Explore the structure

```
inkwell/
├── AGENT-PLAYBOOK.md     # How agents should behave
├── prompts/              # Ready-to-paste session starters
├── templates/            # Generic templates to customize
├── lenses/               # Reusable voice/style modules
└── projects/             # Your writing projects
```

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

1. Copy `templates/lens-template.md` to `lenses/your-name/`
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

## Philosophy

### English as Code

Natural language *is* the programming language for LLMs. InkWell leans into this: instead of writing Python to control agent behavior, you write Markdown that agents read and follow.

This means:
- No dependencies, no installation, no build step
- The "code" is human-readable and editable
- Works anywhere Markdown works

### Structured Recursion

The system's power comes from recursive self-reference:
- Before acting, agents read the relevant files
- After acting, they update those files
- Future sessions pick up where previous ones left off

This creates continuity without requiring persistent memory.

### Voice as First-Class Citizen

Most LLM writing sounds like LLMs. InkWell treats author voice as a core system feature, not an afterthought. The lens system exists specifically to make output sound like *you*, not like a helpful assistant.

---

## Repository Structure

```
inkwell/
├── README.md                 # You are here
├── AGENT-PLAYBOOK.md         # Behavioral instructions for agents
├── SYSTEM-DESIGN.md          # Deeper design documentation
│
├── prompts/                  # Ready-to-paste session prompts
│   ├── writing-session.md
│   ├── new-project.md
│   ├── revision-pass.md
│   └── recovery.md
│
├── templates/                # Generic templates
│   ├── lens-template.md
│   ├── project-manifest-template.md
│   ├── section-card-template.md
│   └── context-manifest-template.md
│
├── lenses/                   # Reusable voice/style/domain lenses
│   ├── examples/
│   └── night/                # Example author presets
│
├── projects/                 # Writing projects
│   └── night-practice-blog/  # Example project
│
└── meta/
    └── CHANGELOG.md
```

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

## Contributing

This is an early-stage project. If you use it and find improvements:
- Open an issue for bugs or suggestions
- PRs welcome for templates, documentation, or system refinements
- Share your lenses if they might help others

---

## License

MIT. Use it, adapt it, make it yours.

---

*InkWell is a tool for maintaining coherence across long-form writing with LLM agents. It treats English as code and Markdown as a universal instruction format.*

