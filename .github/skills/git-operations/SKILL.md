# Git Operations Skill

Use this skill when an agent needs to carry out repository Git workflows on behalf of a learner.

This skill assumes the learner is delegating the Git operations to the agent rather than typing commands manually.
This is the canonical step-by-step Git workflow for the repository. Keep repository-wide invariants in `.github/copilot-instructions.md`, narrow guardrails in `.github/instructions/git-operations.instructions.md`, and prompts as thin task launchers.

## Goals

- Keep the repository aligned with `origin/main` as the source of truth.
- Help the agent choose the right Git workflow for the learner's current stage of work.
- Ensure commits happen at meaningful checkpoints with descriptive messages.
- Support safe branching, rebasing, PR preparation, and post-merge cleanup.

## When To Use

Use this skill for requests such as:

- sync my repo with remote
- create a branch for this task
- checkpoint what I built
- commit all completed changes with a good message
- prepare this branch for PR
- clean up after merge

## Required Inspection

Before acting, inspect:

```powershell
git status --short --branch
git branch --list
git remote -v
```

If the next step depends on branch ancestry or remote divergence, also inspect:

```powershell
git fetch --prune
git log --oneline --decorate --max-count=10 --all
```

## Workflow Modes

### 1. Start Work

1. Ensure local `main` exists and is clean enough to sync safely.
2. Update local `main` from `origin/main`.
3. Create or switch to the correct feature branch.
4. Confirm the branch name and upstream plan to the learner.

Preferred pattern:

```powershell
git checkout main
git pull origin main
git checkout -b <feature-branch>
```

### 2. Checkpoint Work

Use this only after a coherent unit of work is complete.

1. Review changed files.
2. Decide whether the scope represents one meaningful checkpoint.
3. Stage the intended files only.
4. Write a descriptive commit message.
5. Push if the learner asked for remote backup or PR progress.

Commit message pattern:

- `feat(<area>): <outcome>`
- `fix(<area>): <problem solved>`
- `docs(<area>): <documentation outcome>`
- `refactor(<area>): <structural improvement>`

Avoid:

- `update files`
- `changes`
- `checkpoint`
- `misc fixes`

### 3. Prepare PR

1. Sync with latest `main`.
2. Rebase the feature branch when appropriate for the repo workflow.
3. Surface conflicts clearly if they require judgment.
4. Push the branch.
5. Summarize what changed and whether the branch is ready for review.

Preferred pattern:

```powershell
git checkout main
git pull origin main
git checkout <feature-branch>
git rebase main
git push --force-with-lease origin <feature-branch>
```

### 4. Post-Merge Cleanup

1. Return to `main`.
2. Sync local `main` with `origin/main`.
3. Delete merged local branches when safe.
4. Prune stale remote refs.
5. Confirm the repository is clean.

Preferred pattern:

```powershell
git checkout main
git pull origin main
git branch -d <merged-branch>
git fetch --prune
```

## Safety Rules

- Never discard learner work without explicit permission.
- Never use destructive commands unless the learner asked for cleanup and the agent has verified there is no work to preserve.
- Stop and surface the issue if:
  - the working tree is dirty in a way that blocks sync or rebase
  - the learner is on the wrong branch
  - conflicts exist and the correct resolution is not obvious
  - the remote branch has already been deleted or superseded

## Output Expectations

When using this skill, report:

- current Git state
- intended workflow mode
- commands run or to run
- descriptive commit message, when applicable
- blockers, risks, or cleanup steps
