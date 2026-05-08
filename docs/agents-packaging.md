# Custom Agents Packaging

Store shared team agents under `.github/agents/`.

## Naming

Use lowercase, hyphenated filenames for single-file agents, and package folders only when multiple related agents must stay together:

- `requirements-analyst.agent.md`
- `stakeholder-impact.agent.md`
- `process-mapper.agent.md`
- `problem-statement-decomposition/a-normalizer.agent.md`

## Expectations

- Keep single-role agents as top-level `.agent.md` files.
- Use a package folder only for one cohesive multi-agent workflow such as PSD.
- Keep each `.agent.md` file focused on one role or one PSD stage.
- Use minimal tools for the role.
- Include a keyword-rich `description` that starts with `Use when:`.
- Add or update examples in `docs/examples/` when behavior changes.

## Loader Note

Only agent spec markdown should live under `.github/agents/`. Keep supporting documentation in `docs/` so the custom agent loader does not try to parse non-agent markdown files as agent definitions.
