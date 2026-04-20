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

## Creating and Editing Skills

Skills live in `.skillshare/skills/`. Always edit them there — never directly in other config directories, as those are targets that get overwritten on sync.

### Create a new skill

```bash
skillshare new <skill-name>
```

This scaffolds a new skill directory under `.skillshare/skills/<skill-name>/` with a `SKILL.md` template. Edit that file to define the skill's trigger, instructions, and behavior.

### Edit an existing skill

Open `.skillshare/skills/<skill-name>/SKILL.md` and make your changes.

### Sync to all agent configs

After creating or editing any skill, sync it to all targets (Claude, OpenCode, etc.):

```bash
skillshare sync
```

To check what's out of sync before committing:

```bash
skillshare diff
```

### Workflow summary

1. `skillshare new <name>` — scaffold (or just edit `.skillshare/skills/<name>/SKILL.md`)
2. Edit the skill in `.skillshare/skills/`
3. `skillshare sync` — push to all target configs
4. Test via the agent: `claude.sh` or `opencode.sh`

## Setup

The environment is automatically set up on container creation. Skills are pre-installed as symlinks from the skillshare registry and are ready to use through agent execution with `claude.sh` or `opencode.sh`.
