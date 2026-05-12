# Copilot Guidance Architecture

This repository uses a layered guidance model so the same procedure does not get repeated across instructions, prompts, skills, and docs.

## Guidance layers

| Layer | Purpose | Canonical location | Keep here |
|---|---|---|---|
| Repository invariants | Stable repo-wide rules and safety expectations | [`.github/copilot-instructions.md`](../.github/copilot-instructions.md) | Only rules that should load broadly |
| Scoped guardrails | Narrow reusable rules for a defined scope | [`.github/instructions/`](../.github/instructions/) | Constraints, required checks, and blockers |
| Task entrypoints | Lightweight launch text for common requests | [`.github/prompts/`](../.github/prompts/) | Inputs, goal framing, output shape |
| Detailed procedures | Repeatable operational workflows | [`.github/skills/`](../.github/skills/) | Step-by-step task logic |
| Specialist roles | Persistent agent behavior and contracts | [`.github/agents/`](../.github/agents/) | Role scope, constraints, output contracts |
| Learner docs | Human-readable explanation and discovery | [`docs/`](./) | Explanations, onboarding, examples, links |

## Decision rules

1. If a rule should apply almost everywhere, keep it in `.github/copilot-instructions.md`.
2. If a rule only matters for a narrow class of work, keep it in `.github/instructions/`.
3. If the content explains how to carry out a repeatable workflow, keep it in a skill.
4. If the content only helps a user start that workflow, keep it in a prompt and point to the skill.
5. If the content is for learners reading the repository, keep it in `docs/` and link to the runtime files rather than duplicating them.

## Current canonical mappings

| Concern | Start here | Detailed procedure | Guardrails |
|---|---|---|---|
| Git operations | [`.github/prompts/git-operations.prompt.md`](../.github/prompts/git-operations.prompt.md) | [`.github/skills/git-operations/SKILL.md`](../.github/skills/git-operations/SKILL.md) | [`.github/instructions/git-operations.instructions.md`](../.github/instructions/git-operations.instructions.md) |
| Workspace setup and readiness | [`.github/prompts/workspace-setup.prompt.md`](../.github/prompts/workspace-setup.prompt.md) | [`.github/skills/ba-workspace/SKILL.md`](../.github/skills/ba-workspace/SKILL.md) | [`.github/copilot-instructions.md`](../.github/copilot-instructions.md) and workspace conventions in `docs/` |
| BA kickoff | [`.github/prompts/ba-kickoff.prompt.md`](../.github/prompts/ba-kickoff.prompt.md) | Use the relevant BA agent and role docs | Workspace conventions apply when persisting outputs |

## Maintenance rules

- Do not copy full procedures from a skill into a prompt.
- Do not move detailed workflow steps into `.github/copilot-instructions.md`.
- Prefer linking to canonical files from `README.md` and `docs/` instead of restating the same bullets.
- When a new workflow needs both a prompt and a skill, write the skill first and keep the prompt thin.
