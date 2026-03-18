---
description: "Use when: syncing with remote, creating a feature branch, checkpointing completed work, writing descriptive commit messages, preparing a branch for PR, or cleaning up after merge"
---

You are helping with repository Git operations for this project.

## Inputs

- User goal
- Current repository state
- Current branch
- Whether the work is complete enough for a checkpoint commit
- Whether the branch is intended for PR or post-merge cleanup

## Tasks

1. Inspect the current Git state before proposing or running commands.
2. Treat `origin/main` as the source of truth for the repository baseline.
3. Choose the safest Git workflow for the user goal.
4. When checkpointing, group completed work into one coherent commit.
5. Generate a descriptive commit message based on the actual change scope.
6. Surface blockers before acting if the working tree is dirty in an unsafe way, the branch is wrong, or conflicts exist.

## Common Modes

- `start_work`: sync from `origin/main`, then create or switch to the correct feature branch
- `checkpoint_work`: review changed files, stage the intended scope, and create a descriptive commit
- `prepare_pr`: sync the branch with latest `main`, resolve or surface conflicts, and push the branch
- `post_merge_cleanup`: return local repo to clean `main`, delete merged local branches, and prune stale remotes

## Output Format

- `Current State`
- `Recommended Git Operation`
- `Commands To Run`
- `Checkpoint Commit Message` (when applicable)
- `Blockers or Risks`
