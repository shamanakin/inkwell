# InkWell System Design

> This document explains the design decisions, principles, and architecture behind InkWell. Read this if you want to understand *why* the system works the way it does, or if you're thinking about extending it.

---

## Design Philosophy

### 1. English as Code

The core insight: **natural language is the native programming language of LLMs**.

Most LLM tooling wraps models in traditional code—Python scripts, APIs, CLI tools. This adds complexity and creates a translation layer between human intent and model behavior.

InkWell takes a different approach: write instructions in English, structure them in Markdown, and let the LLM execute them directly. The `.md` files *are* the code.

**Implications:**
- No installation, no dependencies, no build step
- The "source code" is human-readable and editable
- Debugging means reading and revising prose
- Portability: works anywhere you can paste text into an LLM

### 2. External Memory Over Internal Memory

LLMs don't have persistent memory across sessions. Most systems address this with:
- RAG (retrieval from vector stores)
- Fine-tuning
- Ever-longer context windows

InkWell uses a simpler approach: **structured files that agents read and write**.

Before acting, agents read the relevant files. After acting, they update them. The file system *is* the memory. This has advantages:
- Transparent: you can see exactly what the agent "knows"
- Editable: you can directly modify the memory
- Debuggable: problems are visible in the files
- Portable: just copy the folder

### 3. Voice as System Architecture

Most AI writing sounds like AI writing. This isn't a prompting failure—it's a systems failure. Voice isn't something you add at the end; it's something that must be encoded in the system itself.

InkWell treats voice (lenses) as first-class objects:
- Defined explicitly in dedicated files
- Consulted before and after writing
- Used for self-checking and revision
- Composable and reusable across projects

The lens system exists specifically to make output sound like *you*, not like a helpful assistant.

### 4. Recursive Self-Reference

The system's power comes from loops:

```
load context → act → self-check → update state → repeat
```

Each step involves reading structured files. The "self-check" step explicitly requires agents to re-read the lens and compare their output. The "update state" step creates artifacts that future sessions can read.

This creates continuity without magic. The agent doesn't "remember"—it reads its own notes.

---

## Architecture Overview

### Layer 1: Behavioral Core

**`AGENT-PLAYBOOK.md`**

This is the runtime specification. It tells agents:
- What files to read and in what order
- When to output pre-flight checks
- How to self-check against lenses
- When and how to update state files
- What to do when stuck or lost

The playbook is written *to the agent*, not to the human. It's executable documentation.

### Layer 2: Reusable Modules (Lenses)

**`lenses/`**

Lenses encode *how to write*—voice, style, domain expertise, process preferences. They're designed to be:

- **Composable**: Stack multiple lenses for a project
- **Reusable**: Apply the same lens to multiple projects
- **Self-contained**: Each lens is a complete module

A lens has standardized sections that agents can navigate reliably:
- Identity & Voice
- Style Rules
- Domain Orientation
- Process Preferences
- Quality Bar
- Failure Modes

### Layer 3: Project State

**`projects/[name]/`**

Each project is a self-contained directory:

| File | Purpose |
|------|---------|
| `PROJECT.md` | Source of truth: vision, audience, constraints, lens stack |
| `OUTLINE.md` | Structure of the work |
| `CONTEXT-MANIFEST.md` | Priority order for loading files |
| `DECISIONS.md` | Log of significant choices |
| `HANDOFF.md` | Session continuity notes |
| `sections/` | Individual section cards |

This structure enables:
- Cold starts: any session can reload full context
- Collaboration: multiple agents/humans can work on the same project
- Debugging: all state is visible and editable

### Layer 4: Local State (Section Cards)

**`sections/*.md`**

Section cards are the smallest unit of state. Each one tracks:
- Location in the larger structure
- Intent (what this section must achieve)
- Status (not started → complete)
- Dependencies and links
- Local decisions and TODOs
- The draft itself

Section cards enable granular progress tracking without complex project management tooling.

---

## Key Design Decisions

### Why Markdown?

- Universal: works in any editor, any platform
- Readable: both humans and LLMs can parse it
- Structured enough: headings create navigable sections
- Unstructured enough: natural language within sections
- Git-friendly: diffs are meaningful

### Why Not a Database?

Databases optimize for querying. InkWell optimizes for:
- Human readability
- Direct editability
- Transparency of state
- Zero infrastructure

For most writing projects, the overhead of a database isn't worth it. Files are sufficient and simpler.

### Why Explicit File Loading?

LLMs have limited context. Rather than trying to load everything, InkWell uses a tiered system:

- **Tier 1**: Always load (playbook, project manifest, current section)
- **Tier 2**: Load if space (lenses, outline, handoff notes)
- **Tier 3**: Reference (decisions log, adjacent sections)

The `CONTEXT-MANIFEST.md` makes this explicit for each project. Agents know what to prioritize.

### Why Pre-Flight Checks?

The pre-flight check forces agents to synthesize context before acting. This catches misalignments early:

```
## Pre-flight
- Project: night-practice-blog
- Active lenses: night-core-lens, night-clinical-lens
- Vision: Help prospective clients understand therapy and trust me
- Current section: welcome-post
- This session: Draft the welcome post
```

If the pre-flight is wrong, you correct it before the agent writes 1000 words in the wrong direction.

### Why Handoff Notes?

Context resets between sessions. Handoff notes create explicit continuity:

```
## Handoff — 2024-12-08
- Completed: First draft of welcome-post
- Decisions: Kept it to 700 words, personal but not oversharing
- Open questions: Should we mention specific modalities?
- Next step: Review for voice alignment, then draft what-to-expect
```

The next session reads this and picks up where the previous one left off.

---

## Common Patterns

### The Cold Start

When beginning a session with no prior context:

1. Agent reads `AGENT-PLAYBOOK.md`
2. Agent reads `PROJECT.md`
3. Agent reads `HANDOFF.md` for continuity
4. Agent reads the target section card
5. Agent loads lenses as context permits
6. Agent outputs pre-flight check
7. Work begins

### The Revision Loop

For improving existing work:

1. Load context as usual
2. Read the current draft
3. Re-read the lens (especially Voice and Failure Modes)
4. Critique against the lens explicitly
5. Propose or make revisions
6. Update section card with new status

### The Recovery

When things have gone wrong:

1. Stop generating
2. Re-read PROJECT.md and lens stack
3. Re-read current section card
4. Output a recovery summary (what I think is happening)
5. Ask for confirmation before proceeding

---

## Extension Points

### Custom Lenses

The lens template is intentionally flexible. You can:
- Fill only the sections you need
- Add custom sections for specialized domains
- Create lens "families" for different contexts

### Custom Prompts

The `prompts/` directory contains starting points. Customize them for:
- Your specific workflow
- Different types of writing sessions
- Team-specific protocols

### New File Types

The system is extensible. You might add:
- `STYLE-GUIDE.md` for house style rules
- `CHARACTERS.md` for fiction projects
- `RESEARCH.md` for academic work

As long as agents know to read them, they integrate into the system.

---

## Limitations and Trade-offs

### Agent Reliability

The system depends on agents actually following instructions. LLMs are stochastic—they don't always do what they're told. Mitigations:
- Clear, repeated instructions
- Pre-flight checks catch drift early
- Recovery protocol for realignment

### Context Limits

Large projects may exceed context windows. Mitigations:
- Tiered loading (Tier 1/2/3 system)
- Summarization over skipping
- Section cards as "working memory"

### No Enforcement

Unlike real code, there's no runtime that enforces behavior. An agent *can* ignore the playbook. Mitigations:
- Design for visibility (problems show up in output)
- Human checkpoints (review pre-flight, review drafts)
- Cultural norms (agents are generally instruction-following)

### Single-Player Optimized

The current design assumes one human + agents. Multi-human collaboration would need:
- Conflict resolution for simultaneous edits
- More sophisticated state management
- Possibly external tooling

---

## Future Directions

**Not commitments—just possibilities:**

- **Lens Library**: Community-contributed lenses for common use cases
- **Validation Tooling**: Scripts that check for broken references, missing files
- **Session Logging**: Automatic logging of agent sessions for debugging
- **Integrations**: Hooks for other writing tools (Obsidian, Notion, etc.)
- **Metrics**: Optional tracking of progress, word counts, status changes

---

## Principles Summary

1. **English is code**: Write instructions for agents in natural language
2. **Files are memory**: All state lives in readable, editable files
3. **Voice is architecture**: Author voice is encoded, not prompted
4. **Loops create coherence**: Load → act → check → update → repeat
5. **Transparency over magic**: Everything the agent knows is visible
6. **Simple over clever**: Markdown files beat complex infrastructure

---

*InkWell is an experiment in treating LLMs as first-class writing partners, with systems designed around how they actually work.*

