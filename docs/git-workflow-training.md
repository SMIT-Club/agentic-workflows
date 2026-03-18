# Git Workflow Training Guide

This guide teaches the branch-based workflow for contributing BA agents and documentation to this repository.

## Learning Objectives

By the end of this guide, you will be able to:
- Create a feature branch from `main`
- Make atomic commits with clear messages
- Sync your branch with latest changes
- Open and update pull requests
- Resolve merge conflicts
- Complete the full contribution cycle

## Prerequisites

- Git installed and configured with your name and email
- Repository cloned locally: `git clone https://github.com/NAIT-ITBA/itba-agentic-workflows.git`
- VS Code or another editor

## Quick Reference Commands

```powershell
# Start new work
git checkout main
git pull origin main
git checkout -b feat/agent-<role>-<team>

# Make changes and commit
git add .github/agents/my-agent/my-agent.agent.md
git commit -m "Add stakeholder impact analyzer agent"

# Sync with latest main before PR
git checkout main
git pull origin main
git checkout feat/agent-<role>-<team>
git rebase main

# Push to remote
git push origin feat/agent-<role>-<team>

# After PR feedback
git add <files>
git commit -m "Address review feedback: clarify output format"
git push origin feat/agent-<role>-<team>
```

## Step-by-Step Workflow

### Step 1: Start From Latest Main

Always start your work from the latest `main` branch:

```powershell
cd C:\Users\<your-username>\itba-agentic-workflows
git checkout main
git pull origin main
```

**Why:** This ensures you're building on the most recent approved changes and reduces conflicts later.

### Step 2: Create Your Feature Branch

Use the standard naming pattern:

```powershell
git checkout -b feat/agent-stakeholder-impact-teamA
```

**Branch naming pattern:** `feat/agent-<role>-<team>`

Examples:
- `feat/agent-stakeholder-impact-teamA`
- `feat/agent-process-mapper-teamB`
- `feat/prompt-risk-workshop-teamC`
- `fix/agent-requirements-analyst-yaml-teamA`

**Why:** Clear names make it easy to see what each branch does and who owns it.

### Step 3: Make Small, Focused Commits

Edit your assigned files, then commit incrementally:

```powershell
# Edit .github/agents/stakeholder-impact/stakeholder-impact.agent.md
git add .github/agents/stakeholder-impact/stakeholder-impact.agent.md
git commit -m "Add stakeholder impact analyzer agent skeleton"

# Edit docs/roles/stakeholder-impact.md
git add docs/roles/stakeholder-impact.md
git commit -m "Add documentation for stakeholder impact role"
```

> Note: Teams do not update `docs/agent-catalog.md` in feature PRs unless explicitly assigned as integrator.

**Commit message guidelines:**
- Start with a verb: "Add", "Update", "Fix", "Remove"
- Be specific but concise
- One logical change per commit

**Why:** Small commits make it easier to review, revert, and understand changes.

### Step 4: Push Your Branch

```powershell
git push origin feat/agent-stakeholder-impact-teamA
```

If this is your first push on this branch:
```powershell
git push -u origin feat/agent-stakeholder-impact-teamA
```

**Why:** This backs up your work and makes it visible to your team.

### Step 5: Sync With Main Before Opening PR

Before opening your PR, sync with the latest `main`:

```powershell
git checkout main
git pull origin main
git checkout feat/agent-stakeholder-impact-teamA
git rebase main
```

**If conflicts occur:**
1. Git will pause and show conflicted files
2. Open each file and resolve conflicts (look for `<<<<<<<`, `=======`, `>>>>>>>`)
3. After fixing each file: `git add <filename>`
4. Continue: `git rebase --continue`
5. If you get stuck: `git rebase --abort` (starts over)

**Force push after rebase:**
```powershell
git push --force-with-lease origin feat/agent-stakeholder-impact-teamA
```

**Why:** Rebasing keeps history clean and catches conflicts early before review.

### Step 6: Open a Pull Request

1. Go to GitHub repository
2. Click "Pull requests" → "New pull request"
3. Select your branch as the source
4. Fill out the PR template (see `.github/pull_request_template.md`)
5. Assign a reviewer
6. Click "Create pull request"

**Why:** PRs enable code review and discussion before merging.

### Step 7: Address Review Feedback

When reviewers request changes:

```powershell
# Make the requested edits
git add <changed-files>
git commit -m "Address review: add missing acceptance criteria examples"
git push origin feat/agent-stakeholder-impact-teamA
```

**Why:** Iterative feedback improves quality and teaches best practices.

### Step 8: Final Sync and Merge

Before final approval, sync one more time:

```powershell
git checkout main
git pull origin main
git checkout feat/agent-stakeholder-impact-teamA
git rebase main
git push --force-with-lease origin feat/agent-stakeholder-impact-teamA
```

Once approved, the reviewer will **squash merge** your PR into `main`.

**After merge:** Delete your branch locally and remotely:
```powershell
git checkout main
git pull origin main
git branch -d feat/agent-stakeholder-impact-teamA
git push origin --delete feat/agent-stakeholder-impact-teamA
```

**Why:** Clean up keeps the repo tidy and signals completed work.

## Common Scenarios

### Scenario: Another Team Merged Changes While I Was Working

```powershell
git checkout main
git pull origin main
git checkout feat/agent-stakeholder-impact-teamA
git rebase main
# Resolve conflicts if any
git push --force-with-lease origin feat/agent-stakeholder-impact-teamA
```

### Scenario: I Made a Mistake in My Last Commit

**Amend the commit (if not yet pushed):**
```powershell
# Fix the files
git add <files>
git commit --amend --no-edit
```

**Amend and change the message:**
```powershell
git add <files>
git commit --amend -m "New commit message"
```

**If already pushed:**
```powershell
git add <files>
git commit --amend --no-edit
git push --force-with-lease origin feat/agent-stakeholder-impact-teamA
```

### Scenario: I Need to Undo My Last Commit

**Keep the changes but remove the commit:**
```powershell
git reset --soft HEAD~1
```

**Discard the changes completely:**
```powershell
git reset --hard HEAD~1
```

### Scenario: I Accidentally Committed to Main

```powershell
# Move your commit to a new branch
git branch feat/agent-my-work-teamA
git reset --hard origin/main
git checkout feat/agent-my-work-teamA
```

## Team Coordination Rules

1. **Never push directly to `main`** — always use a feature branch and PR.
2. **Sync frequently** — pull from `main` at least once per day.
3. **Keep PRs small** — one agent + related docs per PR.
4. **One team per agent file** — avoid editing another team's assigned agents.
5. **Communicate conflicts early** — if two teams need the same file, discuss in team channel.

## Merge Strategy

This repository uses **squash merge** for all PRs:
- All your commits are combined into one clean commit on `main`
- Commit history on `main` stays linear and readable
- Branch history is preserved in the PR for learning review

## Getting Help

- **Git commands:** Ask in team channel or review [Git documentation](https://git-scm.com/doc)
- **Merge conflicts:** Pair with a teammate or ask the designated reviewer
- **Process questions:** See [docs/contribution-guide.md](contribution-guide.md)
