# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Marp-based presentation repository for managing personal presentation materials. All presentations are written in Markdown and converted to HTML/PDF/PowerPoint using Marp CLI.

## Build Commands

```bash
# Install dependencies (required first time)
npm install

# Build presentations
npm run build          # Build all presentations to HTML
npm run build:sample   # Build specific presentation

# Development mode
npm run watch          # Auto-rebuild on changes
npm run server         # Live server with hot reload

# Export formats
npm run pdf:sample     # Export to PDF
npm run pptx:sample    # Export to PowerPoint
npm run clean          # Remove all generated files
```

## Repository Structure

Each presentation lives in its own directory under `/presentations/`:
- Source file: `slides.md` (Marp markdown)
- Generated files: `slides.html`, `slides.pdf`, `slides.pptx` (git-ignored)
- Planning: `draft.md` (optional, for story/content planning)

## Creating New Presentations

1. Create a new directory: `presentations/your-presentation-name/`
2. Create `slides.md` with Marp frontmatter:
```markdown
---
marp: true
theme: gaia
paginate: true
---
```
3. Add build script to package.json if needed for specific presentation

## Marp Conventions

- Default theme: `gaia`
- Japanese language content expected
- Custom styling via frontmatter `style:` block
- Slide separation with `---`
- VSCode Marp extension recommended for preview

## Node.js Requirements

- Node.js 22+ (specified in .nvmrc and package.json engines)
- npm 10+ required