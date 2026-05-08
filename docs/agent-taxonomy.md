# Agent Taxonomy and Associations

This document defines the naming and association convention for custom agents stored in `.github/agents/`.

## Why this exists

As the agent count grows, filenames alone are not enough to show which agents are standalone, which belong to a workflow, and which agent acts as the entrypoint. This convention keeps those relationships explicit without adding nonstandard YAML frontmatter that could break the loader.

## Taxonomy terms

| Term | Meaning | Example |
|---|---|---|
| Standalone agent | A self-contained agent with no stage dependencies | `requirements-analyst.agent.md` |
| Workflow orchestrator | The entrypoint agent for a multi-stage workflow | `psd-orchestrator.agent.md` |
| Workflow stage | A deterministic sub-agent in a labeled sequence | `psd-b-extractor.agent.md` |
| Workflow label | The shared short prefix that groups related agents | `psd` |
| Association block | A structured markdown section in the agent body that declares workflow relationships | `## Association` |

## Naming convention

### Standalone agents

- Format: `<capability>.agent.md`
- Example: `process-mapper.agent.md`

### Workflow orchestrators

- Format: `<workflow-label>-orchestrator.agent.md`
- Example: `psd-orchestrator.agent.md`

### Workflow stages

- Format: `<workflow-label>-<stage-letter>-<stage-name>.agent.md`
- Example: `psd-c-classifier.agent.md`
- Set `user-invocable: false` when the stage should remain hidden from the Copilot agent picker

## Association convention

Each workflow-related agent should include a structured `## Association` section in the body.

### Orchestrator example

```md
## Association

- Taxonomy: `workflow-orchestrator`
- Workflow label: `psd`
- Stages: `psd-a-normalizer.agent.md` -> `psd-b-extractor.agent.md` -> `psd-c-classifier.agent.md`
- Breakpoints: `A_OUT`, `B_OUT`, `C_OUT`
```

### Stage example

```md
## Association

- Taxonomy: `workflow-stage`
- Workflow label: `psd`
- Orchestrator: `psd-orchestrator.agent.md`
- Stage: `B`
- Stage output: `B_OUT`
- Upstream: `psd-a-normalizer.agent.md`
- Downstream: `psd-c-classifier.agent.md`
```

Workflow stages that are only meant to be invoked through their orchestrator should use `user-invocable: false`. Keep the orchestrator as the only picker-visible entrypoint.

## Loader guidance

- Keep required YAML frontmatter limited to supported fields such as `name`, `description`, `tools`, and `user-invocable`.
- Do not introduce custom YAML keys for associations until loader support is confirmed.
- Keep supporting documentation in `docs/`, not inside `.github/agents/`.
