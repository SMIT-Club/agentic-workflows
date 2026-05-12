# Workspace Setup Skill

Use this skill when an agent needs to help a learner prepare, inspect, or use the repository workspace for business analysis tasks.

This skill keeps the workflow lightweight by standardizing where inputs go, where generated artifacts belong, and what should remain untracked.
This is the canonical workspace procedure. Keep setup prompts thin and keep learner-oriented explanation in `docs/`.

## Goals

- Keep learner source material in `workspace/inputs/`
- Keep generated working artifacts in `workspace/outputs/`
- Use tracked starter material from `workspace/templates/`
- Use safe reference material from `workspace/examples/`
- Preserve the committed folder structure while leaving live inputs and outputs untracked

## When To Use

Use this skill for requests such as:

- set up my BA workspace
- where do I put my notes and transcripts
- prepare the repo for agent analysis
- check whether my inputs are ready
- help me choose the first agent from the files in the workspace

## Workspace Convention

| Path | Use |
|---|---|
| `workspace/inputs/` | Raw notes, transcripts, draft requirements, issue logs, or other source material |
| `workspace/outputs/` | Persisted working artifacts created during analysis |
| `workspace/templates/` | Tracked starter templates for consistent input packaging |
| `workspace/examples/` | Tracked safe examples for learning and walkthroughs |

## Required Checks

Before recommending a workflow:

1. Confirm the learner has placed source material in `workspace/inputs/<initiative-name>/`, or direct them to the template in `workspace/templates/`.
2. Inspect the available input files and identify whether they are structured or unstructured.
3. Recommend the best starting agent:
   - Use `PSD Orchestrator` for messy, mixed, or highly unstructured material.
   - Use `Requirements Analyst` for vague requirements or user stories.
   - Use `Process Mapper` for current/future state workflow analysis.
   - Use `Stakeholder Impact Analyzer` for change impact and communications planning.
   - Use `BA Review Specialist` for quality review of an existing BA deliverable.
4. Tell the learner where the resulting working artifact should be stored under `workspace/outputs/<initiative-name>/` if they want it persisted.

## Safety Rules

- Do not tell the learner to commit live files from `workspace/inputs/` or `workspace/outputs/` unless they explicitly choose to promote a sanitized artifact elsewhere.
- Keep examples and templates safe for tracking.
- Prefer reusing the tracked template rather than inventing a new ad hoc input format for each initiative.

## Output Expectations

When using this skill, report:

- workspace readiness
- missing inputs, if any
- recommended starting agent
- expected output type
- suggested `workspace/outputs/<initiative-name>/` destination
