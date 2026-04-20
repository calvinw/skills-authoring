# skills-authoring

This repo is a skills authoring environment with a collection of pre-installed skills for use with AI agents (Claude, OpenCode).

Skills are slash commands available through agent execution with `claude.sh` or `opencode.sh`.

## Available Skills

| Skill | Description |
|-------|-------------|
| **algorithmic-art** | Create generative/algorithmic art using p5.js with seeded randomness and interactive parameter exploration. |
| **brand-guidelines** | Apply Anthropic's official brand colors and typography to artifacts. |
| **canvas-design** | Create visual art and designs as .png or .pdf documents. |
| **doc-coauthoring** | Structured workflow for co-authoring documentation, proposals, and specs. |
| **docx** | Create, read, edit, and manipulate Word (.docx) documents. |
| **frontend-design** | Build production-grade frontend interfaces (websites, dashboards, React components). |
| **hello-world** | Simple greeting skill. Triggered by `/hello-world NAME`. |
| **internal-comms** | Write internal communications (status reports, newsletters, incident reports, etc.). |
| **mcp-builder** | Guide for creating MCP (Model Context Protocol) servers in Python or TypeScript. |
| **pdf** | Read, create, merge, split, and manipulate PDF files. |
| **pptx** | Create, read, edit, and manipulate PowerPoint (.pptx) presentations. |
| **skill-creator** | Create new skills, improve existing ones, and run evals to measure performance. |
| **slack-gif-creator** | Create animated GIFs optimized for Slack. |
| **template** | Template for authoring new skills. |
| **theme-factory** | Apply pre-set or custom themes to artifacts (slides, docs, HTML pages). |
| **web-artifacts-builder** | Build elaborate multi-component HTML artifacts using React, Tailwind, and shadcn/ui. |
| **webapp-testing** | Test local web applications using Playwright (screenshots, logs, UI verification). |
| **xlsx** | Create, read, edit, and manipulate spreadsheet (.xlsx, .csv) files. |

## Setup

The environment is automatically set up on container creation. Skills are pre-installed as symlinks from the skillshare registry and are ready to use through agent execution with `claude.sh` or `opencode.sh`.

## Working with Skills

All skill authoring happens in `.skillshare/skills/`. Never edit files directly in agent config directories (`.claude/`, `.opencode/`, `.agents/`, etc.) — those are managed automatically by `skillshare sync`.

### Create a new skill

```bash
# Create a new skill scaffold in the project
skillshare new my-skill --project

# Edit the generated SKILL.md
# .skillshare/skills/my-skill/SKILL.md

# Sync to all agent targets
skillshare sync
```

### Edit an existing skill

```bash
# Edit the skill source file
# .skillshare/skills/my-skill/SKILL.md

# Re-sync to propagate changes to all agents
skillshare sync
```

### Remove a skill

```bash
# Uninstall the skill (moves it to trash)
skillshare uninstall my-skill

# Sync to remove it from all agent targets
skillshare sync
```

### Commit and push changes

```bash
git add -A && git commit -m "..." && git push
```
