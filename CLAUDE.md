# skills-authoring

This repo is for authoring and managing skills — slash commands available through AI agent tools like Claude Code, OpenCode, and others.

## Skill Authoring

**Always edit skills in `.skillshare/skills/` — never edit them in other config directories.**

### Create a new skill

```bash
skillshare new <skill-name>
```

This scaffolds a new skill directory under `.skillshare/skills/<skill-name>/` with a `SKILL.md` template. Edit that file to define the skill's trigger, instructions, and behavior.

### Edit an existing skill

Open `.skillshare/skills/<skill-name>/SKILL.md` and make your changes.

### Sync to all agent configs

After creating or editing any skill, sync it to all targets:

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

Changes made directly in target configs will be overwritten on the next sync.

## Setup

The environment is automatically set up on container creation. Skills are pre-installed and ready to use through agent execution with `claude.sh` or `opencode.sh`.
