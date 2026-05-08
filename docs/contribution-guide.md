# Agent Contribution Guide

This guide provides the workflow for contributing BA agents, prompts, and documentation to this repository.

## Quick Links

- **Full Git workflow training:** See [docs/git-workflow-training.md](git-workflow-training.md)
- **Team assignments:** See [docs/team-branch-matrix.md](team-branch-matrix.md)
- **Agent packaging:** See [docs/agents-packaging.md](agents-packaging.md)
- **Agent taxonomy:** See [docs/agent-taxonomy.md](agent-taxonomy.md)
- **PR template:** Auto-loaded when you create a PR

## Overview

This repository uses a trunk-based workflow with:
- **Protected `main` branch** — all changes via pull requests
- **Feature branches** — short-lived, one agent/prompt per branch
- **Squash merge** — clean linear history on `main`
- **Team ownership** — one team per agent file to minimize conflicts
- **Remote-first sync** — treat `origin/main` as the source of truth before branching, rebasing, or cleanup

## Branching

Create a feature branch per change using this naming pattern:

```
feat/agent-<role>-<team>
feat/prompt-<name>-<team>
fix/agent-<role>-<issue>-<team>
docs/<topic>
```

**Examples:**
- `feat/agent-stakeholder-impact-teamB`
- `feat/prompt-risk-workshop-teamC`
- `fix/agent-requirements-analyst-yaml-teamA`
- `docs/add-glossary`

**Always branch from latest `main`:**
```powershell
git checkout main
git pull origin main
git checkout -b feat/agent-your-role-teamX
```

If an IDE agent is performing Git operations, use:

- [`.github/prompts/git-operations.prompt.md`](../.github/prompts/git-operations.prompt.md)
- [`.github/instructions/git-operations.instructions.md`](../.github/instructions/git-operations.instructions.md)
- [`.github/skills/git-operations/SKILL.md`](../.github/skills/git-operations/SKILL.md)

## Pull Request Requirements

### Before Opening PR

- [ ] Sync with latest `main` via rebase
- [ ] All commits have clear messages
- [ ] Work was checkpointed after coherent completed slices, not partial fragments
- [ ] Frontmatter validated (YAML syntax)
- [ ] Tested with 2+ realistic scenarios
- [ ] PR scope is small (one agent + related docs)

### PR Must Include

- Updated `*.agent.md`, `*.prompt.md`, or `*.instructions.md`
- Updated role documentation in `docs/roles/*.md` (for agent changes)
- **Do NOT update `docs/agent-catalog.md`** — integrator will handle this after merge
- Do not create new runtime workflow assets under `workflows/` (use `.github/agents/` + `docs/` orchestration docs)
- Do not place non-agent markdown files directly under `.github/agents/`; keep supporting docs in `docs/`
- At least one usage example in PR description
- Reviewer notes describing expected behavior changes

### PR Size Limits

Keep PRs focused and reviewable:
- **Ideal:** 1 agent file + 1 role doc + examples
- **Maximum:** 3 files changed (excluding auto-generated)
- **Split if larger:** Break into sequential PRs

## Merge Strategy

All PRs use **squash merge**:
- Your commits are combined into one clean commit on `main`
- Commit history on `main` stays linear
- Branch history is preserved in the PR for review

**After your PR merges:**
```powershell
git checkout main
git pull origin main
git branch -d feat/agent-your-role-teamX
git push origin --delete feat/agent-your-role-teamX
```

## Team Coordination Rules

1. **Never push directly to `main`** — always use feature branch + PR
2. **One team per agent file** — see [team-branch-matrix.md](team-branch-matrix.md) for assignments
3. **Sync daily** — pull latest `main` and rebase your branch
4. **Communicate overlaps** — if two teams need the same file, coordinate in team channel
5. **Review responsibly** — assigned reviewers respond within 24 hours

## Review Checklist

Reviewers validate:

- [ ] Frontmatter is valid YAML (`name`, `description`, `tools`, `user-invocable`)
- [ ] `description` starts with "Use when:" and includes trigger phrases
- [ ] Scope is narrow and not overlapping with existing agents
- [ ] Output format is explicit and testable
- [ ] Tool list is minimal for the role (justify if >3 tools)
- [ ] No implementation code in agent instructions
- [ ] Constraints section includes clear "DO NOT" boundaries
- [ ] Examples or walkthroughs are realistic and complete
- [ ] Role documentation updated in `docs/roles/`

## Merge Order

To minimize conflicts, merge in this sequence:

1. **Foundation PRs** — shared instructions, glossary, standards
2. **Agent PRs** — individual role agents in any order
3. **Integration PR** — integrator updates catalog with all merged agents

## Getting Help

- **Git questions:** See [git-workflow-training.md](git-workflow-training.md)
- **Merge conflicts:** Pair with teammate or ask designated reviewer
- **Agent design:** Review existing agents in `.github/agents/` for patterns
- **Process questions:** Ask in team channel or tag repository maintainer
