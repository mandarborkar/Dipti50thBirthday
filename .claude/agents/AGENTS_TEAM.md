# Agent team

A coordinator agent plus specialist subagents, built on Claude Code subagents (`.claude/agents/`).

## Run it
```bash
claude --agent orchestrator
```
The orchestrator only coordinates: it has no Edit/Write/Bash tools, so all work goes to specialists. Then just describe the service you want built.

## Roster
`product-manager` -> `architect` -> `backend-dev` / `frontend-dev` -> `qa-engineer` + `security-reviewer` -> `devops-engineer` -> `tech-writer`

## Notes
- Subagents cannot spawn other subagents, so the hierarchy is flat: the orchestrator is the only router.
- Subagents start with no conversation memory; the orchestrator passes briefs and file paths (specs in `docs/`).
- Edit any `.claude/agents/*.md` to change a role, tools, or model (e.g. `model: sonnet` for cheaper workers).
- Add roles (data-engineer, ml-engineer, ...) by adding a file and listing it in the orchestrator's `Agent(...)` tool allowlist.
