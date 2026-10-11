# morewebs/resources

Shared resources for AI agents and humans: installable [agent skills](https://agentskills.io), plus prompts and reusable assets that don't fit the skill format.

## Layout

| Directory | Contents |
| :--- | :--- |
| [`skills/`](skills/) | Agent skills — one self-contained directory per skill, each with a `SKILL.md` |
| [`prompts/`](prompts/) | Standalone prompt templates and snippets |
| [`assets/`](assets/) | Shared static resources: datasets, schemas, config templates |
| [`tools/`](tools/) | Repo maintenance scripts (skill validation) |

Only `skills/` is consumed by agent tooling; everything else is ordinary repo content.

## Installing skills

Install skills from this repo into any supported agent (Claude Code, Cursor, Codex, Cline, Copilot, Gemini CLI, …) with the [Vercel Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add morewebs/resources                 # interactive picker
npx skills add morewebs/resources --list         # see what's available
npx skills add morewebs/resources --skill <name> # install a specific skill
```

## Adding a skill

1. Create `skills/<skill-name>/` (lowercase kebab-case) with a `SKILL.md` containing `name` and `description` frontmatter, plus optional `scripts/`, `assets/`, and `evals.json`.
2. Validate it: `python tools/validate-skills.py`
3. Push — the skill is immediately installable via `npx skills add morewebs/resources`.

Reference: [Agent Skills Standard](https://agentskills.io) · [Vercel Skills CLI](https://github.com/vercel-labs/skills)

## License

[MIT](LICENSE)
