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
- [PSD Pipeline Guide](docs/problem-statement-decomposition-pipeline.md)
- [Contribution Guide](docs/contribution-guide.md)
- [Quick Start](docs/quick-start.md)
- [Git Operations Prompt](.github/prompts/git-operations.prompt.md)
- [Git Operations Skill](.github/skills/git-operations/SKILL.md)

## Problem Statement Decomposition (PSD)

The PSD pipeline is defined by six dedicated agents in one package:

Keep this package together when you want the full PSD workflow to remain co-located under a single agent package.

1. `.github/agents/problem-statement-decomposition/a-normalizer.agent.md`
2. `.github/agents/problem-statement-decomposition/b-extractor.agent.md`
3. `.github/agents/problem-statement-decomposition/c-classifier.agent.md`
4. `.github/agents/problem-statement-decomposition/d-auditor.agent.md`
5. `.github/agents/problem-statement-decomposition/e-packager.agent.md`
6. `.github/agents/problem-statement-decomposition/f-excel-formatter.agent.md`

Canonical orchestration and handoff contracts are documented in:
- [docs/problem-statement-decomposition-pipeline.md](docs/problem-statement-decomposition-pipeline.md)

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

## Contributing

- Add or update agent behavior in the appropriate file or package under `.github/agents/`
- Update matching documentation in `docs/`
- Do not use `workflows/` for new runtime assets

See [docs/contribution-guide.md](docs/contribution-guide.md) for standards and PR expectations.

## License

See [LICENSE](LICENSE).
