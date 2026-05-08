# Role Documentation

This folder contains detailed documentation for each BA agent role.

## Purpose

Role documentation provides:
- **Overview** of the agent's specialty and purpose
- **When to use** guidelines with specific scenarios
- **Input expectations** so users know what to provide
- **Output format** specifications showing what the agent returns
- **Example interactions** demonstrating real usage
- **Tips** for getting the best results
- **Related agents** for workflow orchestration

## One Role = One Doc

Each agent has a dedicated role doc to:
- Avoid merge conflicts (one team per file)
- Enable deep examples without cluttering agent spec
- Provide user-facing "how to use this" guidance separate from agent instructions

## Contents

| Role Doc | Agent File | Team Owner |
|----------|------------|------------|
| [requirements-analyst.md](requirements-analyst.md) | `.github/agents/requirements-analyst.agent.md` | Team A |
| [stakeholder-impact.md](stakeholder-impact.md) | `.github/agents/stakeholder-impact.agent.md` | Team B |
| [process-mapper.md](process-mapper.md) | `.github/agents/process-mapper.agent.md` | Team C |
| [ba-review.md](ba-review.md) | `.github/agents/ba-review.agent.md` | Team D |

## Contribution

When you update an agent:
1. Update the agent file under `.github/agents/`
2. Update the matching role doc in `docs/roles/`
3. Do NOT edit `docs/agent-catalog.md` (integrator handles this)
4. Include examples in your PR showing the change impact
