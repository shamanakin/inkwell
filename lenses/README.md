# InkWell Lenses

Lenses are reusable cognitive and stylistic modules that define *how* to think and write. They're independent of any specific project—you can apply the same lens to a blog post, a book chapter, or a clinical guide.

## What a Lens Contains

A lens can define any combination of:

- **Identity & Voice**: Who is speaking, their values, their relationship to the reader
- **Style Rules**: Sentence structure, jargon policy, metaphor use, example density
- **Domain Orientation**: Subject matter expertise, how to handle evidence and uncertainty
- **Process Preferences**: How the agent should behave (ask first? outline first? etc.)
- **Quality Bar**: What "good enough" looks like
- **Failure Modes**: Common mistakes and how to self-correct

## Lens Stacking

Projects typically use multiple lenses together—a "lens stack." For example:
- A core author lens (your voice and values)
- A domain lens (clinical, technical, etc.)
- A style lens (essay, educational, conversational)

When lenses conflict, the project's `PROJECT.md` specifies priority.

## Directory Structure

```
lenses/
├── README.md           # This file
├── examples/           # Neutral example lenses
│   └── example-author-lens.md
└── night/              # Night's presets
    ├── night-core-lens.md
    ├── night-clinical-lens.md
    └── night-essay-lens.md
```

## Creating Your Own

1. Copy `templates/lens-template.md` to this directory
2. Fill in the sections that matter for your use case
3. Reference it from your project's `PROJECT.md`

