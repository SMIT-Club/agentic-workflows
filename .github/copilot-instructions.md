# Repository Copilot Instructions

These instructions apply across this repository unless a more specific prompt, instruction, skill, or agent file provides narrower guidance.

## Operating Priorities

- Treat `origin/main` as the source of truth for the approved repository state.
- Inspect repository state before taking Git actions.
- Prefer safe, non-destructive commands first.
- Keep changes scoped, reviewable, and easy to explain.
- Preserve repository conventions before introducing new structure.

## Git Workflow Rules

- Branch from updated `main`.
- Use short-lived feature branches for changes.
- Checkpoint only after a coherent slice of functionality or documentation is complete.
- Write descriptive commit messages that reflect actual intent and scope.
- Sync with latest `main` before PR readiness.
- After merge, return the local repository to clean `main` and prune stale refs.

## Safety Rules

- Never discard user changes without explicit permission.
- Never push directly to `main` unless the user explicitly asks for it.
- Surface blockers before acting when the tree is dirty, the branch is wrong, or conflicts exist.
- Prefer explicit inspection over assumptions when repository state is unclear.

## Orchestration Guidance

- Use prompts for focused task entry points.
- Use instructions for broad behavioural rules.
- Use skills for detailed, reusable procedural workflows.
- Use agents for persistent specialist roles with narrower scope and defined constraints.

## Documentation Expectations

- Keep learner-facing Git guidance consistent across prompts, instructions, skills, and docs.
- Update discovery docs when repository workflows or folder conventions change.
- Prefer links to canonical files rather than duplicating long procedural text in multiple places.
