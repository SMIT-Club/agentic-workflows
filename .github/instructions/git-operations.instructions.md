---
applyTo: "**"
---

# Git Operations Guardrails

Use this instruction when the user asks an agent to perform Git operations for this repository.

This file owns the repository-specific Git guardrails. Keep detailed step-by-step procedures in `.github/skills/git-operations/SKILL.md` and use prompts only as thin task entrypoints.

## Required Inspection

- `git status --short --branch`
- `git branch --list`
- `git remote -v`

## Repository Rules

- Treat `origin/main` as the source of truth for the approved repository state.
- Prefer safe, non-destructive commands first.
- Explain the intended Git operation briefly before executing it.
- Sync local `main` from `origin/main` before branching.
- Review changed files before staging and stage only the files that belong to the checkpoint scope.
- Sync the working branch with latest `main` before PR readiness and prefer `rebase` when history rewriting fits the workflow.
- Return local repo to `main`, sync it, and prune merged branches only when cleanup is safe.

## Safety Rules

- Never push directly to `main` unless the user explicitly asks for it.
- Never discard user changes without explicit permission.
- Never use destructive commands such as `git reset --hard`, `git checkout --`, or branch deletion unless:
  - the user explicitly asked for the cleanup, or
  - the action is required to complete a requested cleanup after merge, and
  - the agent has already verified there is no user work to preserve.
- If the working tree is dirty, determine whether those changes are intentional before syncing, rebasing, or cleaning.
- If the current branch is not appropriate for the requested action, explain the correction and switch only when safe.

## Commit Message Standard

- Start with a verb or conventional prefix that matches the change.
- Describe intent and scope, not the tool used.
- Use the changed files and repository context to infer the message.
- Avoid vague messages such as `update files`, `changes`, or `checkpoint`.

## Blockers To Surface

- Dirty working tree that would be overwritten
- Detached HEAD
- Missing upstream tracking branch
- Merge or rebase conflicts
- Branch created from stale `main`
- Remote branch already deleted or superseded
