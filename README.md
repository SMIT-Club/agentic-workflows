# ITBA Agentic Workflows

Business analysis workflows strategically designed to enhance engagement, decision-making, problem-solving, and ethical reasoning.

## Overview

This project provides a structured framework for building and executing agentic workflows to support business analysis. Agentic workflows are sequenced markdown files that AI and agentic-enabled IDEs can execute sequentially on information sources or trigger based on conditions.

## Project Structure

```
itba-agentic-workflows/
├── .github/                      # GitHub and agent configuration
│   ├── agents/                   # Reusable BA agent definitions
│   ├── prompts/                  # Task-focused prompt templates
│   ├── instructions/             # Shared instruction files
│   └── pull_request_template.md  # PR template for contributions
├── workflows/                    # Main workflows directory
│   └── problem-statement-decomposition/   # Problem statement workflow
├── docs/                         # Documentation
│   ├── agent-catalog.md          # Index of all agents and prompts
│   ├── contribution-guide.md     # Contribution workflow guide
│   ├── git-workflow-training.md  # Git learning guide for teams
│   ├── team-branch-matrix.md     # Team ownership and branch mapping
│   └── roles/                    # Agent role documentation
├── README.md                     # This file
├── LICENSE                       # Project license
└── .gitignore                    # Git ignore patterns
```

## Business Analysis Agents

This repository includes a library of reusable BA agents designed for distributed team collaboration:

| Agent | Purpose | Documentation |
|-------|---------|---------------|
| **Requirements Analyst** | Elicit, clarify, and refine requirements with testable acceptance criteria | [Role Guide](docs/roles/requirements-analyst.md) |
| **Stakeholder Impact Analyzer** | Identify stakeholders, assess change impacts, develop communication plans | [Role Guide](docs/roles/stakeholder-impact.md) |
| **Process Mapper** | Document current/future state processes, identify gaps and bottlenecks | [Role Guide](docs/roles/process-mapper.md) |
| **BA Review Specialist** | Validate deliverable quality, traceability, and completeness | [Role Guide](docs/roles/ba-review.md) |

**Quick Links:**
- [Agent Catalog](docs/agent-catalog.md) — Full index of agents and prompts
- [Contribution Guide](docs/contribution-guide.md) — How to contribute agents
- [Git Workflow Training](docs/git-workflow-training.md) — Learn branch-based workflow

### Team Collaboration Model

This repository is designed for distributed teams learning Git while building BA agents:

- **Trunk-based workflow** with short-lived feature branches
- **Team ownership** — one team per agent file to minimize conflicts
- **Squash merge** strategy for clean history
- **Role-specific documentation** to avoid merge collisions
- **PR-based reviews** with structured templates

See [Team Branch Matrix](docs/team-branch-matrix.md) for current assignments and [Git Workflow Training](docs/git-workflow-training.md) for step-by-step learning guide.

## Workflows

### Problem Statement Decomposition

Located in `workflows/problem-statement-decomposition/`, this workflow helps break down complex problem statements into manageable components for analysis using a six-agent pipeline:

| Agent | Purpose |
|-------|---------|
| **A_Normalizer** | Converts raw text into standardized JSON with ordered content blocks |
| **B_Extractor** | Extracts verbatim observations into an ordered ledger |
| **C_Classifier** | Assigns strategic categories and core concept labels |
| **D_Auditor** | Identifies risks, policy violations, and elicitation gaps |
| **E_Packager** | Transforms outputs into a student-friendly review artifact |
| **F_ExcelFormatter** | Converts final JSON to structured Excel spreadsheet |

Designed for ITBA1002 learners, this workflow maintains full traceability from source text to final categorized output.

## Getting Started

### Quick Start for Teams

**New to this repository?** Follow the [Quick Start Guide](docs/quick-start.md) to set up your environment, check team assignments, and submit your first PR in ~1 hour.

**Key Resources:**
- [Quick Start Guide](docs/quick-start.md) — Get contributing in 5 steps
- [Git Workflow Training](docs/git-workflow-training.md) — Learn Git branch-based workflow
- [Team Branch Matrix](docs/team-branch-matrix.md) — See your team assignment
- [Contribution Guide](docs/contribution-guide.md) — PR requirements and review checklist

### For AI Agents

1. **Navigate to Workflows**: Access the `workflows/` directory to find available agentic workflows
2. **Select Workflow**: Choose the appropriate workflow for your task (e.g., problem-statement-decomposition)
3. **Execute Sequentially**: Process markdown files in numerical/alphabetical order
4. **Follow Instructions**: Each markdown file contains specific instructions and context
5. **Output Results**: Generate analysis outputs as specified in the workflow files

### For Humans

1. Clone this repository
2. Navigate to the desired workflow directory
3. Review the sequenced markdown files to understand the workflow
4. Execute workflows using AI-enabled IDEs or tools that support agentic operations

## Workflow File Conventions

- **Agent Naming**: Files are named with letter prefixes to indicate execution order (e.g., `A_Normalizer.md`, `B_Extractor.md`)
- **JSON I/O**: Each agent accepts and outputs structured JSON matching defined schemas
- **Self-Contained**: Each file contains all necessary context, instructions, and schema definitions
- **Markdown Format**: Standard markdown format for compatibility with AI tools
- **Deterministic Rules**: Agents follow explicit precedence rules for consistent behavior
- **Error Handling**: All agents return structured error objects when they cannot comply

## Adding New Workflows

1. Create a new directory under `workflows/`
2. Name it descriptively (use kebab-case)
3. Add sequenced markdown files with clear numbering
4. Include a README.md in the workflow directory explaining its purpose
5. Update this main README with the new workflow description

## Use Cases

- **Business Analysis**: Decompose complex business problems
- **Decision Support**: Structure decision-making processes
- **Problem Solving**: Systematic approach to problem resolution
- **Ethical Reasoning**: Framework for ethical analysis and considerations

## Contributing

Contributions are welcome! Please ensure:
- New workflows follow the sequential markdown file pattern
- Documentation is clear and comprehensive
- Files are well-organized and properly named

## License

See [LICENSE](LICENSE) file for details.
