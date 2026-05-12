# Custom Agents Packaging

Store shared team agents under `.github/agents/`.

## Naming

Use lowercase, hyphenated filenames. Group workflow families by prefix rather than by subfolder:

- `requirements-analyst.agent.md`
- `stakeholder-impact.agent.md`
- `process-mapper.agent.md`
- `psd-orchestrator.agent.md`
- `psd-a-normalizer.agent.md`

Related prompts, instructions, and skills should reuse the same capability slug where that artifact type exists. For skills, keep the required package format and use the slug as the folder name, for example `git-operations\SKILL.md` or `workspace-setup\SKILL.md`.

## Expectations

- Keep single-role agents as top-level `.agent.md` files.
- Keep workflow families as top-level `.agent.md` files that share a workflow prefix.
- Keep each `.agent.md` file focused on one role or one PSD stage.
- Use minimal tools for the role.
- Include a keyword-rich `description` that starts with `Use when:` and keep it as a concise phrase in frontmatter.
- Keep frontmatter concise and consistent: `name`, `description`, `tools`, and `user-invocable` only.
- Add or update examples in `docs/examples/` when behavior changes.

## Workflow taxonomy

Use the convention in [docs/agent-taxonomy.md](agent-taxonomy.md) to connect:

- a workflow orchestrator
- its stage agents
- their shared workflow label
- their upstream and downstream handoffs

## Loader Note

Only agent spec markdown should live under `.github/agents/`. Keep supporting documentation in `docs/` so the custom agent loader does not try to parse non-agent markdown files as agent definitions.
