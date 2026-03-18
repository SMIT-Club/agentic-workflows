---
applyTo: "**"
---

# Git Operations Instruction

Use this instruction when the user asks an agent to perform Git operations for this repository.

## Operating Model

- Treat `origin/main` as the source of truth for the approved repository state.
- Inspect repository state before acting:
  - `git status --short --branch`
  - `git branch --list`
  - `git remote -v`
- Prefer safe, non-destructive commands first.
- Explain the intended Git operation briefly before executing it.

## Approved Agent Workflows

### 1. Start Work

- Sync local `main` from `origin/main` before branching.
- Create new work from updated `main`.
- Use descriptive branch names that match repo conventions.

### 2. Checkpoint Work

- Only checkpoint after a coherent unit of functionality or documentation is complete.
- Review changed files before staging.
- Stage only the files that belong to the checkpoint scope.
- Write a descriptive commit message that reflects the real change, not a placeholder.

### 3. Prepare a PR

- Sync the working branch with latest `main` before PR readiness.
- If history rewriting is appropriate for the branch workflow, prefer `rebase`.
- Surface conflicts clearly and stop for user direction if resolution is ambiguous.
- Push the updated branch after validation.

### 4. Post-Merge Cleanup

- Return local repo to `main`.
- Sync local `main` to `origin/main`.
- Delete merged local branches when safe.
- Prune deleted remote refs.

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
