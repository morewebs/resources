# Runtime checks

## Claude Code

- Use `/context` to see what fills the current window. Use `/memory` to locate loaded project instructions and memory. If these commands are only available to the user, work from the visible session and available files or use a summary the user shares.
- Check project `CLAUDE.md`, project `.claude/skills/`, personal `~/.claude/skills/`, and applicable managed settings. Confirm which same-name skill wins. To retain manual invocation while removing a skill from automatic discovery, verify `disable-model-invocation: true` or the corresponding skill visibility setting for the installed version.
- Verify changes with `/context` and the skill menu in a fresh session. See the [commands reference](https://code.claude.com/docs/en/commands) and [skill guide](https://code.claude.com/docs/en/skills).

## Codex

- Check applicable `AGENTS.md` files, repository `.agents/skills/`, personal `~/.agents/skills/`, and the applicable `config.toml` layers. Include plugin and system skills when they appear in the catalog.
- If the installed CLI supports it, use `codex debug prompt-input --help`, then run `codex debug prompt-input "Context audit probe"` in the target workspace. Filter the output locally for counts, skill names, and source markers. This describes the probed invocation. Desktop or cloud sessions may inject additional context.
- To retain explicit selection while removing automatic discovery, check `policy.allow_implicit_invocation: false` in the skill's `agents/openai.yaml`. A disabled skill and an explicit-only skill have different effects. Test a setting in isolation before persisting it.
- Use selective configuration or an on-demand reference before considering `model_instructions_file`. That setting replaces the bundled base instructions and prevents that base from updating automatically for the affected scope. See the [skill guide](https://learn.chatgpt.com/docs/build-skills) and [config reference](https://developers.openai.com/codex/config-reference/).
