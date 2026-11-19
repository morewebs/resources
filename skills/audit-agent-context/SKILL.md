---
name: audit-agent-context
description: Audit and trim an agent's live context, startup instructions, skill catalog, or tool descriptions.
disable-model-invocation: true
---

# Audit Agent Context

Find text that consumes recurring context without earning its place. For a live-context audit, start with what the current session actually received. For a file audit, start with the named files. Apply changes when the user asks for cleanup. For a review, report findings and proposed edits.

## Trace the input

Identify what the user means by context. Separate standing instructions, skill metadata, tool definitions, and environment messages from chat history, tool results, and files read on demand. A file on disk is only a candidate source until the current session or a runtime probe shows that it loads. Use [runtime checks](references/runtime-checks.md) to trace uncertain sources or validate edits.

Record a baseline when available. Use the runtime's token counts, or count characters and entries in named sections. Match the workspace, runtime version, and probe input for before-and-after comparisons.

## Decide what earns its place

Prioritize recurring cost and collisions between instructions. For each finding, identify the loaded source and choose the smallest change that addresses it.

- **Remove** stale rules, exact repeats, and information cheaply available from code, configuration, or tool help.
- **Shorten** repetitive instructions and skill descriptions. Give each skill a distinct trigger. Resolve same-name skills by checking their contents, helpers, and scope, then choose the intended variant for automatic discovery.
- **Move** tool manuals, specialist examples, and rare branches behind a clear pointer. Keep the trigger and essential constraints in the instructions that load first.
- **Keep** requirements that change behavior, including project conventions, permission checks, and verification criteria. Treat host- or administrator-managed material as a finding unless there is an authorized setting that changes it.

## Apply and verify

Prefer reversible, project-scoped edits. Treat home-wide changes and replacement of a bundled instruction set as separate scope decisions. Preserve useful specialist workflows and explicit invocation when the runtime supports it. Leave unrelated settings and existing work intact.

Recheck the assembled context or skill discovery in a fresh session or probe. Confirm that required guidance and an intended entry for each retained workflow still load. Test outside the project if the change might affect other workspaces.

Report the highest-impact cuts, actual edits, measured change, and what remains host-managed or unverified. Say which sections a measurement covers. Summarize private instructions or logs without reproducing sensitive content.
