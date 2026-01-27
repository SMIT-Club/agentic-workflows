# ITBA Agentic Workflows

Business analysis workflows strategically designed to enhance engagement, decision-making, problem-solving, and ethical reasoning.

## Overview

This project provides a structured framework for building and executing agentic workflows to support business analysis. Agentic workflows are sequenced markdown files that AI and agentic-enabled IDEs can execute sequentially on information sources or trigger based on conditions.

## Project Structure

```
itba-agentic-workflows/
├── workflows/                    # Main workflows directory
│   └── problem-statement-decomposition/   # Problem statement decomposition workflow
├── README.md                     # This file
├── LICENSE                       # Project license
└── .gitignore                    # Git ignore patterns
```

## Workflows

### Problem Statement Decomposition

Located in `workflows/problem-statement-decomposition/`, this workflow helps break down complex problem statements into manageable components for analysis.

## Getting Started

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

- **Sequential Naming**: Files are named to indicate execution order (e.g., `01-step.md`, `02-step.md`)
- **Self-Contained**: Each file contains all necessary context and instructions
- **Markdown Format**: Standard markdown format for compatibility with AI tools
- **Clear Objectives**: Each step has clearly defined inputs, processes, and outputs

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
