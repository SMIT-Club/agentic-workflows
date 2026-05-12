# ITBA Agentic Workflows

Business analysis agents and pipeline specifications for structured analysis, decision support, problem solving, and ethical reasoning.

## Overview

This repository is now **agent-first**:

- Runtime behavior is defined in agent specs under `.github/agents/`
- Usage and orchestration guidance is defined in `docs/`
- Legacy `workflows/` assets are deprecated and archived for reference

## Project Structure

```text
itba-agentic-workflows/
|-- .github/
|   |-- agents/                   # Shared agent specs and the PSD workflow package
|   |-- skills/                   # Reusable procedural Copilot skills
|   |-- prompts/                  # Task-focused prompt templates
|   |-- instructions/             # Shared instruction files
|   |-- copilot-instructions.md   # Repository-wide Copilot behaviour rules
|   `-- pull_request_template.md
|-- docs/
|   |-- agent-catalog.md          # Index of agents and prompts
|   |-- problem-statement-decomposition-pipeline.md
|   |-- roles/                    # Role usage documentation
|   `-- archive/workflows/        # Frozen legacy workflow files
|-- workspace/
|   |-- inputs/                   # User-provided BA source material (folder tracked, contents ignored)
|   |-- outputs/                  # Agent-generated working artifacts (folder tracked, contents ignored)
|   |-- templates/                # Tracked starter templates for consistent inputs
|   `-- examples/                 # Tracked safe sample inputs for learning
|-- workflows/
|   `-- README.md                 # Deprecation notice + redirects
`-- README.md
```

## Business Analysis Agents

| Agent | Purpose | Documentation |
|---|---|---|
| Requirements Analyst | Elicit, clarify, and refine requirements with testable acceptance criteria | [Role Guide](docs/roles/requirements-analyst.md) |
| Stakeholder Impact Analyzer | Identify stakeholders, assess change impacts, develop communication plans | [Role Guide](docs/roles/stakeholder-impact.md) |
| Process Mapper | Document current/future state processes, identify gaps and bottlenecks | [Role Guide](docs/roles/process-mapper.md) |
| BA Review Specialist | Validate deliverable quality, traceability, and completeness | [Role Guide](docs/roles/ba-review.md) |

Quick links:
- [Agent Catalog](docs/agent-catalog.md)
- [Agent Taxonomy](docs/agent-taxonomy.md)
- [PSD Pipeline Guide](docs/problem-statement-decomposition-pipeline.md)
- [Contribution Guide](docs/contribution-guide.md)
- [GitHub Project CLI Operations Guide](docs/github-project-cli-operations-guide.md)
- [Quick Start](docs/quick-start.md)
- [Workspace Setup Prompt](.github/prompts/workspace-setup.prompt.md)
- [Git Operations Prompt](.github/prompts/git-operations.prompt.md)
- [BA Workspace Skill](.github/skills/ba-workspace/SKILL.md)
- [Git Operations Skill](.github/skills/git-operations/SKILL.md)

## Problem Statement Decomposition (PSD)

The PSD workflow family now uses a top-level `psd-` taxonomy:

0. `.github/agents/psd-orchestrator.agent.md`
1. `.github/agents/psd-a-normalizer.agent.md`
2. `.github/agents/psd-b-extractor.agent.md`
3. `.github/agents/psd-c-classifier.agent.md`
4. `.github/agents/psd-d-auditor.agent.md`
5. `.github/agents/psd-e-packager.agent.md`
6. `.github/agents/psd-f-excel-formatter.agent.md`

Use the orchestrator as the entrypoint for full runs, resume-from-breakpoint flows, and explicit A-F handoffs.

Canonical orchestration and handoff contracts are documented in:
- [docs/problem-statement-decomposition-pipeline.md](docs/problem-statement-decomposition-pipeline.md)
- [docs/agent-taxonomy.md](docs/agent-taxonomy.md)

Legacy workflow-stage markdown files were moved to:
- `docs/archive/workflows/problem-statement-decomposition/`

## Getting Started

### For teams

- Follow [docs/quick-start.md](docs/quick-start.md)
- Use branch-based contribution flow in [docs/git-workflow-training.md](docs/git-workflow-training.md)
- Check ownership in [docs/team-branch-matrix.md](docs/team-branch-matrix.md)

### For AI IDE agents

1. Select the relevant `.agent.md` spec under `.github/agents/`
2. Follow the specified constraints and output contract
3. For PSD, execute stages in A-F order using the pipeline guide
4. Pass outputs exactly as required between stages

## BA Workspace Convention

Use the `workspace/` directory to keep learner inputs and agent outputs predictable:

| Path | Purpose | Tracking |
|---|---|---|
| `workspace/inputs/` | Raw project text, notes, transcripts, drafts, and source material for analysis | Folder is committed; user files remain untracked |
| `workspace/outputs/` | Working deliverables produced during analysis | Folder is committed; generated files remain untracked |
| `workspace/templates/` | Starter templates that normalize how learners package inputs | Tracked |
| `workspace/examples/` | Safe sample materials for learning and walkthroughs | Tracked |

This keeps the workspace lightweight while still giving new users a ready-made place to put context before invoking agents.

## Contributing

- Add or update agent behavior in the appropriate agent file under `.github/agents/`
- Update matching documentation in `docs/`
- Do not use `workflows/` for new runtime assets

See [docs/contribution-guide.md](docs/contribution-guide.md) for standards and PR expectations.

## License

See [LICENSE](LICENSE).
