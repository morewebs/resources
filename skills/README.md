# Skills

Agent skills following the [Agent Skills Standard](https://agentskills.io). Each subdirectory is one skill:

```
skills/<skill-name>/
├── SKILL.md        # required — YAML frontmatter (name, description) + instructions
├── scripts/        # optional — executable helpers
├── assets/         # optional — templates, schemas, reference files
└── evals.json      # optional — evaluation scenarios
```

## Rules

- Directory names: lowercase kebab-case (`[a-z0-9-]`).
- `SKILL.md` frontmatter requires `name` (matching the directory) and `description`.
- A skill must be self-contained: everything it needs lives inside its own directory. Repo-wide shared files belong in [`../assets/`](../assets/), not inside a skill.

## Install

Anyone can install skills from this repo into their agent with the [Vercel Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add morewebs/resources
```

The CLI scans this `skills/` directory (up to 3 levels deep) and links each skill into the agent directories it detects (`.claude/skills/`, `.agents/skills/`, etc.). Everything outside `skills/` is ignored by the CLI, so the rest of the repo is free to hold non-skill resources.

## Validate

Before pushing, check that skills still conform:

```bash
python tools/validate-skills.py
```
