# Lens Index

> Catalog of all available lenses in InkWell for Cursor. Use this to discover lenses for your projects.

---

## How to Use This Index

**Finding a Lens:**
- Browse by category below
- Check the "Use Cases" for each lens
- Read the lens file to see full details
- Stack multiple lenses for complex projects

**Creating Your Own:**
- Copy `templates/lens-template.md`
- Place in `lenses/your-name/your-lens.md`
- Add it to this index (optional, for sharing)

---

## Example Lenses

**Location**: `lenses/examples/`

These are starter templates you can customize:

### `therapist-lens.md`
- **Use Case**: Client-facing content, blog posts, educational materials
- **Voice**: Warm, professional, relational
- **Domain**: Psychotherapy, mental health
- **Tone**: Grounded, direct, gentle when needed

### `essayist-lens.md`
- **Use Case**: Exploratory essays, long-form thought pieces
- **Voice**: Curious, reflective, nuanced
- **Domain**: General (adaptable)
- **Tone**: Conversational, exploratory

### `technical-writer-lens.md`
- **Use Case**: Documentation, technical guides, tutorials
- **Voice**: Clear, precise, helpful
- **Domain**: Technology, software
- **Tone**: Professional, instructional

### `example-author-lens.md`
- **Use Case**: Generic template for any author
- **Voice**: Customizable
- **Domain**: General
- **Tone**: Customizable

---

## Inspired-By Lenses

**Location**: `lenses/inspired-by/`

These lenses distill the stylistic essence of famous authors without direct mimicry. Use them to add flavor to your writing.

**See**: `lenses/inspired-by/README.md` for full details on how to use these.

### Fiction Authors

- **`jk-rowling-inspired.md`** - Narrative clarity, character voice, accessible complexity
- **`hemingway-inspired.md`** - Minimalism, subtext, iceberg theory
- **`faulkner-inspired.md`** - Stream of consciousness, layered perspectives, dense prose
- **`jack-vance-inspired.md`** - Rich vocabulary, baroque descriptions, picaresque tone
- **`james-joyce-inspired.md`** - Experimental structure, linguistic play, interiority
- **`anne-rice-inspired.md`** - Atmospheric prose, sensual detail, gothic mood
- **`shakespeare-inspired.md`** - Rhetorical structure, wordplay, dramatic rhythm
- **`stephen-king-inspired.md`** - Conversational horror, accessible prose, character focus
- **`george-rr-martin-inspired.md`** - Epic scope, multiple perspectives, moral complexity
- **`tom-clancy-inspired.md`** - Technical precision, procedural detail, authoritative tone
- **`dean-koontz-inspired.md`** - Suspense pacing, philosophical undertones, accessible prose
- **`david-eddings-inspired.md`** - Epic fantasy structure, clear heroes/villains, accessible prose
- **`suzanne-collins-inspired.md`** - Tight pacing, accessible prose, social commentary
- **`chuck-palahniuk-inspired.md`** - Minimalist prose, transgressive themes, punchy rhythm

### Poets

- **`emily-dickinson-inspired.md`** - Compression, dashes, elliptical thought
- **`walt-whitman-inspired.md`** - Expansive lists, democratic voice, organic structure

### Philosophers & Psychologists

- **`nietzsche-inspired.md`** - Aphoristic style, provocative assertions, philosophical depth
- **`carl-jung-inspired.md`** - Symbolic thinking, archetypal language, depth psychology
- **`sigmund-freud-inspired.md`** - Analytical structure, clinical precision, theoretical depth

---

## Social Media Lenses

**Location**: `lenses/social-media/`

Specialized lenses for social media content generation.

### `growth-lens.md`
- **Use Case**: Social media posts optimized for growth
- **Voice**: Value-first, authentic, non-combative
- **Domain**: Social media (platform-agnostic)
- **Tone**: Uplifting, educational, engaging
- **Features**: Growth principles, algorithm optimization, engagement tactics

### `x-twitter-voice.md`
- **Use Case**: X (Twitter) specific content
- **Voice**: Platform-optimized
- **Domain**: X/Twitter
- **Tone**: Concise, engaging, authentic
- **Features**: Character limits, thread structure, timing optimization

**See**: `lenses/social-media/README.md` for social media workflow details.

---

## Private Lenses

**Location**: `lenses/private/` (gitignored)

These are user-specific lenses not tracked in the repository. Examples might include:
- Personal voice lenses
- Client-specific lenses
- Proprietary style guides

**Note**: Private lenses are not listed here for privacy reasons. Check your `lenses/private/` directory for your personal lenses.

---

## Lens Stacking Guide

You can combine multiple lenses for complex projects:

**Example Stack:**
```
1. your-personal-voice-lens.md (base voice)
2. therapist-lens.md (domain expertise)
3. essayist-lens.md (format/style)
```

**Order Matters:**
- First lens = base voice
- Subsequent lenses = modifiers
- Later lenses override earlier ones when there's conflict

**Common Stacks:**
- Personal voice + Domain lens + Format lens
- Inspired-by lens + Domain lens (for stylistic flavor)
- Growth lens + Platform lens + Personal voice (for social media)

---

## Contributing Lenses

If you create a lens that might help others:

1. **For Public Lenses:**
   - Place in `lenses/examples/` or appropriate category
   - Add to this index
   - Include clear use cases

2. **For Inspired-By Lenses:**
   - Place in `lenses/inspired-by/`
   - Follow the naming: `[author-name]-inspired.md`
   - Add to this index

3. **For Social Media Lenses:**
   - Place in `lenses/social-media/`
   - Add to this index

**Lens Quality:**
- Clear identity and voice definition
- Specific style rules
- Failure modes listed
- Activation section (when to use)

---

## Finding the Right Lens

**For Your First Project:**
1. Start with an example lens (`lenses/examples/`)
2. Customize it to match your voice
3. Create your own lens later if needed

**For Stylistic Flavor:**
1. Browse inspired-by lenses
2. Stack with your base voice lens
3. Test and refine

**For Social Media:**
1. Use `growth-lens.md` as base
2. Add platform-specific lens (`x-twitter-voice.md`)
3. Add your personal voice lens

**For Domain Expertise:**
1. Use or create a domain lens
2. Stack with your voice lens
3. Add format lens if needed

---

## Lens Maintenance

**Keeping Lenses Updated:**
- Review lenses periodically
- Refine based on writing output
- Update failure modes as you discover new patterns
- Document what works

**Version Control:**
- Lenses are Markdown files—track changes in git
- Private lenses are gitignored (as intended)
- Public lenses can be versioned and shared

---

*Last updated: [Check git history]*

*To add a lens to this index, edit this file and follow the existing format.*











