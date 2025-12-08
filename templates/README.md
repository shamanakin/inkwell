# InkWell Templates

Generic, user-customizable templates for creating your own lenses and projects.

## Available Templates

### `lens-template.md`
A unified lens template combining identity, voice, style, domain, and process. Fill in only the sections relevant to your needs—a simple lens might just have Identity & Voice; a complex one might use all sections.

### `project-manifest-template.md`
The source of truth for a writing project. Defines vision, constraints, audience, and which lenses to apply. Instantiate this as `PROJECT.md` in each project directory.

### `section-card-template.md`
Local context and state for a single piece of content (a chapter, a post, a section). Tracks intent, status, decisions, and TODOs.

### `context-manifest-template.md`
Priority list for context loading. Helps agents decide what to read when context is limited.

## How to Use

1. Copy a template to your project or lenses directory
2. Rename it appropriately
3. Fill in the sections, deleting placeholder text
4. Reference it from your project's `PROJECT.md` or `LENS-STACK`

## Design Principles

- Every template has a "For Agents" section explaining how to interpret the file
- Stable heading names allow agents to navigate reliably
- Cross-references use relative paths
- Fill only what you need; leave sections blank if not applicable

