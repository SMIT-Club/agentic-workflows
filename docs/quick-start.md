# Quick Start Guide

Get started contributing BA agents to this repository in 5 steps.

## Step 1: Set Up Your Environment

```powershell
# Clone repository (if not already done)
git clone https://github.com/NAIT-ITBA/itba-agentic-workflows.git
cd itba-agentic-workflows

# Verify git is configured
git config user.name
git config user.email

# If not configured, set them:
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Open in VS Code
code .
```

## Step 2: Check Your Team Assignment

Open [docs/team-branch-matrix.md](team-branch-matrix.md) and find:
- Your team name (e.g., Team B)
- Your assigned agent role (e.g., Stakeholder Impact Analyzer)
- Your branch name (e.g., `feat/agent-stakeholder-impact-teamB`)
- Your owned files (agent + role doc)

## Step 3: Read the Docs

Before writing code, review these essential guides:

| Doc | Purpose | Time |
|-----|---------|------|
| [Git Workflow Training](git-workflow-training.md) | Learn branch, commit, sync, PR workflow | 15 min |
| [Contribution Guide](contribution-guide.md) | Understand PR requirements and review checklist | 10 min |
| [Agent Catalog](agent-catalog.md) | See existing agents to avoid overlap | 5 min |
| [Role Doc Template](roles/requirements-analyst.md) | Example of what your role doc should contain | 5 min |

**Total reading time: ~35 minutes**

## Step 4: Create Your Branch and Start Work

```powershell
# Get latest main
git checkout main
git pull origin main

# Create your feature branch (use your team's branch name from matrix)
git checkout -b feat/agent-stakeholder-impact-teamB

# Verify you're on the right branch
git branch
```

**Edit your agent file:**
- Open your assigned file in its package under `.github/agents/` (or create the package if new)
- Use an existing agent as a template (e.g., `requirements-analyst/requirements-analyst.agent.md`)
- Include YAML frontmatter: `name`, `description`, `tools`, `user-invocable`
- Write clear constraints, approach, and output format
- Do not add new runtime assets under `workflows/` (deprecated; use `.github/agents/` + `docs/`)

**Document your agent:**
- Open your role doc in `docs/roles/` (or create if new)
- Include: overview, when to use, input expectations, output format, examples, tips
- Use `requirements-analyst.md` as a template

**Commit incrementally:**
```powershell
# After agent skeleton
git add .github/agents/your-agent/your-agent.agent.md
git commit -m "Add stakeholder impact agent skeleton"

# After role doc
git add docs/roles/your-role.md
git commit -m "Add stakeholder impact role documentation"

# Push to backup your work
git push -u origin feat/agent-stakeholder-impact-teamB
```

## Step 5: Open a Pull Request

**Before opening PR:**
```powershell
# Sync with latest main
git checkout main
git pull origin main
git checkout feat/agent-stakeholder-impact-teamB
git rebase main

# If conflicts, resolve them, then:
git add <resolved-files>
git rebase --continue

# Force push after rebase
git push --force-with-lease origin feat/agent-stakeholder-impact-teamB
```

**Open PR on GitHub:**
1. Go to repository on GitHub
2. Click "Pull requests" → "New pull request"
3. Select your branch
4. Fill out the PR template (auto-loaded)
5. Add example interaction showing your agent works
6. Assign reviewer (see team matrix for reviewer assignments)
7. Submit

**After PR is open:**
- Respond to review feedback within 24 hours
- Make requested changes and push to same branch
- Re-sync with main if other PRs merge before yours

## Common Commands Reference

```powershell
# Check current branch
git branch

# Check status of changes
git status

# See what changed in a file
git diff path/to/file

# Undo uncommitted changes
git checkout -- path/to/file

# Amend last commit
git add <files>
git commit --amend --no-edit

# Sync with main
git checkout main
git pull origin main
git checkout your-branch
git rebase main

# Push after rebase
git push --force-with-lease origin your-branch
```

## Getting Help

| Question | Resource |
|----------|----------|
| Git commands or workflow | [git-workflow-training.md](git-workflow-training.md) |
| Merge conflicts | Ask teammate for pair programming |
| Agent design patterns | Review existing agents in `.github/agents/` |
| PR requirements | [contribution-guide.md](contribution-guide.md) |
| Team assignments | [team-branch-matrix.md](team-branch-matrix.md) |
| General questions | Team channel or tag `@maintainer` |

## What NOT To Do

❌ Push directly to `main` (always use feature branch + PR)  
❌ Edit another team's agent file (avoid conflicts)  
❌ Edit `docs/agent-catalog.md` in your PR (integrator handles this)  
❌ Make mega-PRs with many agents (keep scope small)  
❌ Forget to sync with main before opening PR (causes conflicts)  

## Success Checklist

Before submitting your PR, verify:

- [ ] YAML frontmatter is valid (test in YAML validator)
- [ ] `description` starts with "Use when:" and has trigger phrases
- [ ] Tools list is minimal (2-3 tools max)
- [ ] Constraints include clear "DO NOT" boundaries
- [ ] Output format is explicit and testable
- [ ] Role documentation includes examples
- [ ] Tested with 2+ realistic scenarios
- [ ] Synced with latest `main` via rebase
- [ ] PR description includes example interaction
- [ ] Did NOT edit `docs/agent-catalog.md`

## Next Steps After First PR

1. **Respond to review:** Address feedback and iterate
2. **Learn from others:** Review other teams' PRs to see different approaches
3. **Rotate roles:** After this cohort, try a different agent role
4. **Improve docs:** Suggest enhancements to training guides based on your experience

---

**Ready to start?** Go to [Step 1](#step-1-set-up-your-environment) and begin!
