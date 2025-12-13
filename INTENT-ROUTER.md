# InkWell Intent Router

> **For Agents**: At the start of any writing session, determine the writing intent to load the appropriate lens and configure the output path.

---

## Purpose

Not all writing is the same. A brain dump meant for HARVEST extraction has different requirements than a polished Substack essay. The Intent Router ensures InkWell adapts to the destination before drafting begins.

---

## The Four Intent Modes

### 1. HARVEST (Extraction Fodder)

**What it's for**: Brain dumps, voice notes, info dumps—raw content meant to be processed by HARVEST into the Database.

**Lens**: None required (freeform)

**Output location**: `Database/raw-seeds/` (appropriate subfolder)

**Format**: `.md` or `.txt`

**Characteristics**:
- Stream of consciousness is fine
- No polish needed
- Include tangents, half-thoughts, fragments
- HARVEST will extract and route later

**Trigger phrases**: "I need to dump this", "extract this later", "raw capture", "for HARVEST"

---

### 2. POSTERITY (Personal Archive)

**What it's for**: Brainstorming, journaling, thinking out loud—content meant for personal reference, not publication.

**Lens**: Freeform or user's core lens

**Output location**: `WRITING/personal/` or `WRITING/brainstorms/`

**Format**: `.md`

**Characteristics**:
- Doesn't need to make sense to others
- Can be incomplete, exploratory
- Preserved for future self, not audience
- No external formatting requirements

**Trigger phrases**: "Just for me", "brainstorming", "thinking through", "personal notes"

---

### 3. THINKPIECE (Personal Essay)

**What it's for**: Essays, reflections, developed arguments—content meant to be read but not necessarily published widely.

**Lens**: `essayist-lens.md` or user's essay lens

**Output location**: `WRITING/thinkpieces/` or `WRITING/essays/`

**Format**: `.md`

**Characteristics**:
- Developed argument with beginning, middle, end
- Personal voice and perspective
- Structured but not SEO-optimized
- May become publish-ready with light editing

**Trigger phrases**: "I want to write about", "essay on", "thinkpiece", "explore this idea"

---

### 4. PUBLISH (Public-Facing)

**What it's for**: Blog posts, Substack articles, social content—anything intended for public consumption.

**Lens**: `publishing-lens.md` (or platform-specific lens)

**Output location**: `WRITING/publish/`

**Format**: `.md` (then convert via PUBLISH circuit to `.docx`)

**Characteristics**:
- Polished, audience-aware
- Clear structure with proper headings
- Explicit formatting (bold, italics) for conversion
- SEO-friendly if web-bound
- Ready for minimal editing before posting

**Trigger phrases**: "For Substack", "blog post", "I'm going to publish", "for the public"

---

## Routing Logic

```
START → Determine Intent

Intent unclear?
  → Ask: "What's this writing for?"
  → Options: harvest | posterity | thinkpiece | publish

Intent = HARVEST
  → Skip lens loading
  → Output to raw-seeds/
  → Freeform capture

Intent = POSTERITY  
  → Load core lens (optional)
  → Output to WRITING/personal/
  → Freeform, complete when done

Intent = THINKPIECE
  → Load essayist-lens.md
  → Output to WRITING/thinkpieces/
  → Essay structure, developed argument

Intent = PUBLISH
  → Load publishing-lens.md
  → Output to WRITING/publish/
  → Full polish, conversion-ready
  → Offer PUBLISH circuit at end
```

---

## Intent Detection Heuristics

If the user doesn't explicitly state intent, infer from context:

| Signal | Likely Intent |
|--------|---------------|
| "Just get this out of my head" | HARVEST |
| "I had this idea..." | POSTERITY or THINKPIECE |
| "I want to write about X" | THINKPIECE |
| "For Substack/blog/Medium" | PUBLISH |
| "Draft a post about..." | PUBLISH |
| Mentions specific audience | PUBLISH |
| Mentions "explore" or "think through" | THINKPIECE |
| Voice transcript or dump | HARVEST |

When uncertain, ask. The intent determines everything downstream.

---

## Post-Writing Transitions

Some writing changes intent mid-stream:

- **POSTERITY → THINKPIECE**: "This is actually worth developing"
  - Switch to essayist lens, restructure
  
- **THINKPIECE → PUBLISH**: "I want to publish this"
  - Apply publishing lens for final polish
  - Run PUBLISH circuit for .docx conversion

- **HARVEST → [anything]**: Run HARVEST protocol first
  - Extract to Database
  - Then start fresh with extracted insights

---

## Integration with PUBLISH Circuit

When intent = PUBLISH and the piece is complete:

1. Confirm piece is finished
2. Offer: "Ready to convert to .docx for publishing?"
3. If yes → invoke `PUBLISH.md` circuit
4. Output: `.docx` file with proper formatting in `WRITING/publish/`

See `circuits/PUBLISH.md` for the conversion workflow.

---

## Directory Reference

| Intent | Output Path | Lens |
|--------|-------------|------|
| HARVEST | `Database/raw-seeds/` | none |
| POSTERITY | `WRITING/personal/` | core (optional) |
| THINKPIECE | `WRITING/thinkpieces/` | essayist |
| PUBLISH | `WRITING/publish/` | publishing |


