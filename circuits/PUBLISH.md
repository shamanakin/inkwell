<!-- BEOS - BrightEyed Operating System | Created by Matthew / RoboShaman AI | roboshamanai.com -->

# PUBLISH Circuit

> **For Agents**: This circuit converts finished Markdown writing to publish-ready .docx format.

---

## Prerequisites

**Pandoc must be installed** for this circuit to function.

### Installation (One-Time Setup)

**Windows**:
1. Download: https://github.com/jgm/pandoc/releases
2. Get the `.msi` file (e.g., `pandoc-3.x.x-windows-x86_64.msi`)
3. Run installer
4. Verify: Open PowerShell, run `pandoc --version`

**Mac**:
```bash
brew install pandoc
```

**Linux**:
```bash
sudo apt install pandoc
```

If `pandoc --version` returns a version number, you're ready.

---

## Purpose

The PUBLISH circuit takes a finished piece of writing (in Markdown) and:
1. Runs a final formatting check
2. Converts to .docx with proper heading styles
3. Outputs a file ready for paste-to-platform or direct upload

---

## When to Invoke

Invoke PUBLISH when:
- Writing intent was PUBLISH and the piece is complete
- A THINKPIECE or POSTERITY piece has been promoted to publishable
- User explicitly requests .docx conversion

---

## The PUBLISH Workflow

### Phase 1: Pre-Flight Check

Before conversion, verify:

- [ ] **File exists**: Confirm the source .md/.txt file path
- [ ] **Formatting clean**: Headings use `#`, `##`, `###` properly
- [ ] **Bold/italics**: Uses `**bold**` and `*italics*` (not underscores for italics)
- [ ] **No raw HTML**: Pandoc handles pure Markdown best
- [ ] **Title present**: First line should be `# Title`

If source is **plain text or poorly formatted**, proceed to Phase 2 (Formatting Enhancement).
If source is **properly formatted markdown**, skip to Phase 3 (Conversion).

---

### Phase 2: Formatting Enhancement Protocol

> **For Agents**: When source text lacks proper markdown formatting, apply this protocol to create a publish-ready `.md` file before conversion.

This phase transforms raw prose into richly formatted markdown. Read the document first to understand its structure and rhetorical intent, then apply formatting systematically.

#### Step 2.1: Structural Analysis

Read the full document and identify:

1. **Title**: The main headline (often first line, or most prominent statement)
2. **Subtitle/Deck**: Secondary headline if present
3. **Sections**: Major divisions (often numbered, or marked by topic shifts)
4. **Subsections**: Divisions within sections
5. **Lists**: Parallel items that should be bullets or numbers
6. **Block quotes**: Extended quotes or callouts
7. **Horizontal breaks**: Major topic transitions

#### Step 2.2: Apply Heading Hierarchy

| Element | Markdown | Detection Heuristics |
|---------|----------|---------------------|
| **Title** | `# Title` | First line, standalone, summarizes piece |
| **Subtitle** | `*Subtitle*` (italics under title) | Second line, clarifying/hook |
| **Major Section** | `## Section` | Numbered sections ("1)", "Part One"), topic headers |
| **Subsection** | `### Subsection` | Sub-topics within sections |
| **Minor heading** | `#### Heading` | Rare; use sparingly |

**Heuristics for section detection**:
- Lines that are short, standalone, and introduce new topics
- Numbered patterns: `1)`, `1.`, `Part 1`, `Section 1`, `Chapter 1`
- ALL CAPS lines (convert to Title Case with `##`)
- Lines followed by `—`, `---`, or blank + new topic

#### Step 2.3: Apply Emphasis (Bold & Italics)

**Bold (`**text**`)** — Use for:
- Key terms being defined or introduced
- Critical concepts the reader must grasp
- Thesis statements or core claims
- Action items or imperatives
- Words that would be stressed vocally for emphasis

**Italics (`*text*`)** — Use for:
- Technical terms, jargon, or specialized vocabulary (first use)
- Titles of works (books, articles, films)
- Foreign words or phrases
- Subtle vocal emphasis (less forceful than bold)
- Internal thoughts or hypothetical speech
- Words being discussed as words ("the word *prompting*")

**Detection heuristics for emphasis candidates**:
- Phrases in quotes that define a concept → bold or italics
- "This is X" definitional statements → bold the X
- Contrasts ("not A, but B") → consider bolding B
- Repeated key terms → bold on first meaningful use
- Technical vocabulary → italics on introduction

#### Step 2.4: Apply Structural Formatting

**Bullet lists** — Convert parallel items:
```
Before:
They ask a question, they get an answer, they ask a follow-up, they get another answer.

After (if emphasizing as list):
- They ask a question
- They get an answer  
- They ask a follow-up
- They get another answer
```

**Numbered lists** — For sequential steps or ranked items.

**Block quotes** — For:
- Extended quotations from sources
- Key statements to emphasize as callouts
- Thesis statements worth highlighting

```markdown
> This is a blockquote for emphasis or quotation.
```

**Horizontal rules** — Insert `---` between major sections if the piece has clear part divisions.

#### Step 2.5: Rhetorical Enhancement Patterns

These patterns commonly appear in quality published writing:

| Pattern | Implementation |
|---------|----------------|
| **The Hook** | First paragraph should grab. Consider if opening line deserves standalone treatment. |
| **The Thesis** | Core argument should be bold or blockquoted for scannability. |
| **The Pivot** | "But here's the thing..." moments benefit from `---` before them. |
| **The List Reveal** | Series of points work better as bullets than inline commas. |
| **The Callback** | Key terms established early should be consistent throughout. |
| **The Landing** | Final section deserves clear `## Conclusion` or `## The Takeaway` heading. |

#### Step 2.6: Platform-Specific Considerations

| Platform | Formatting Notes |
|----------|------------------|
| **Substack** | Headers render well; use `##` liberally. Bold works. Avoid `####`. |
| **Medium** | Similar to Substack. Block quotes render nicely. |
| **LinkedIn** | Shorter paragraphs. Bold for scannable key points. |
| **WordPress** | Full markdown support. `---` becomes `<hr>`. |
| **Word/Docs** | Via Pandoc—all standard markdown converts cleanly. |

#### Step 2.7: Quality Checklist

Before proceeding to conversion:

- [ ] Title is `# Title` (exactly one H1)
- [ ] Sections are `## Section` 
- [ ] At least 3-5 bold terms per 500 words (key concepts)
- [ ] At least 2-3 italic terms per 500 words (technical vocab, titles)
- [ ] Lists are properly formatted (not comma-separated in prose)
- [ ] No orphan formatting (unclosed `*` or `**`)
- [ ] Document reads well when skimming headings only

#### Step 2.8: Output

Save the enhanced file as `.md`:
- If source was `.txt`: Create new `.md` file alongside or in `WRITING/publish/`
- If source was unformatted `.md`: Update in place or create `_formatted.md` variant

---

### Phase 3: Conversion

Run Pandoc to convert:

```powershell
pandoc "input.md" -o "output.docx"
```

**Full example**:
```powershell
pandoc "C:\Users\night\BEOS\WRITING\publish\my-article.md" -o "C:\Users\night\BEOS\WRITING\publish\my-article.docx"
```

**With custom styling** (optional—use a reference.docx for branded fonts/styles):
```powershell
pandoc "input.md" --reference-doc="reference.docx" -o "output.docx"
```

### Phase 3: Post-Flight Verification

After conversion:
1. Confirm .docx file was created
2. Report file location to user
3. Note: "Open in Word to verify formatting before publishing"

---

## Conversion Reference

Pandoc automatically converts:

| Markdown | Word Formatting |
|----------|-----------------|
| `# Heading` | Heading 1 |
| `## Heading` | Heading 2 |
| `### Heading` | Heading 3 |
| `**bold**` | Bold |
| `*italics*` | Italics |
| `- item` | Bullet list |
| `1. item` | Numbered list |
| `> quote` | Block quote |
| `---` | Horizontal rule / page break |
| `[text](url)` | Hyperlink |

---

## Custom Reference Document (Optional)

For consistent branding, create a `reference.docx`:

1. Create a Word document with your preferred styles
2. Set fonts, colors, heading styles as desired
3. Save as `reference.docx` in `GIT/InkWell/templates/`
4. Use with: `--reference-doc="templates/reference.docx"`

This ensures every converted document matches your brand.

---

## Agent Execution Steps

When user invokes PUBLISH:

1. **Confirm source file**
   - "Which file should I convert? (provide full path or filename)"

2. **Run pre-flight check**
   - Read the source file
   - Assess: Is it properly formatted markdown, or plain/poorly-formatted text?

3. **If formatting needed → Apply Formatting Enhancement Protocol**
   - Follow Phase 2 steps systematically
   - Read document for structure and rhetorical intent
   - Apply headings, bold, italics, lists, blockquotes
   - Save as `.md` file
   - Confirm with user: "I've enhanced the formatting. Review the .md before I convert?"

4. **Execute conversion**
   ```powershell
   pandoc "[source].md" -o "[source].docx"
   ```

5. **Report completion**
   - "Created: [path to .docx]"
   - "Open in Word to verify formatting before publishing."

6. **Offer next steps**
   - "Want me to open the folder?"
   - "Need any adjustments to the formatting?"

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "pandoc not recognized" | Pandoc not installed or not in PATH. Re-run installer. |
| Headings not styled | Check Markdown uses `#` not underlines |
| Bold/italics missing | Ensure `**` for bold, `*` for italics |
| Weird characters | Source file encoding issue—save as UTF-8 |
| Want different fonts | Create and use a reference.docx |

---

## Directory Structure

```
WRITING/
├── publish/           # PUBLISH intent output
│   ├── article.md     # Source Markdown
│   └── article.docx   # Converted output
├── thinkpieces/       # THINKPIECE intent
├── personal/          # POSTERITY intent
└── brainstorms/       # Alternative posterity location
```

---

## Integration with Intent Router

The PUBLISH circuit is invoked at the end of a PUBLISH-intent writing session:

```
Intent = PUBLISH
  → Load publishing-lens.md
  → Write to WRITING/publish/
  → On completion → Offer PUBLISH circuit
  → Convert .md → .docx
  → Done
```

For pieces that started as THINKPIECE but are promoted:

```
THINKPIECE complete
  → User: "I want to publish this"
  → Apply publishing-lens polish pass
  → Move/copy to WRITING/publish/
  → Invoke PUBLISH circuit
```

---

## Quick Reference

**Basic conversion**:
```powershell
pandoc "file.md" -o "file.docx"
```

**With reference styles**:
```powershell
pandoc "file.md" --reference-doc="reference.docx" -o "file.docx"
```

**From WRITING/publish/**:
```powershell
cd C:\Users\night\BEOS\WRITING\publish
pandoc "my-article.md" -o "my-article.docx"
```


