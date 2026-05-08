# Team Branch Matrix

This document maps teams to their assigned agent roles, branch names, and owned files.

## Purpose

- Avoid work conflicts by clearly assigning ownership
- Simplify merge coordination with dedicated file boundaries
- Track progress across parallel team branches

## Team Assignments

| Team | Agent Role | Branch Name | Owned Files | Status |
|------|------------|-------------|-------------|--------|
| Team A | Requirements Analyst | `feat/agent-requirements-analyst-teamA` | `.github/agents/requirements-analyst.agent.md`<br>`docs/roles/requirements-analyst.md` | ✅ Complete |
| Team B | Stakeholder Impact | `feat/agent-stakeholder-impact-teamB` | `.github/agents/stakeholder-impact.agent.md`<br>`docs/roles/stakeholder-impact.md` | 🔄 In Progress |
| Team C | Process Mapper | `feat/agent-process-mapper-teamC` | `.github/agents/process-mapper.agent.md`<br>`docs/roles/process-mapper.md` | 📝 Not Started |
| Team D | BA Review | `feat/agent-ba-review-teamD` | `.github/agents/ba-review.agent.md`<br>`docs/roles/ba-review.md` | 📝 Not Started |
| Team E | Acceptance Criteria | `feat/agent-acceptance-criteria-teamE` | `.github/agents/acceptance-criteria.agent.md`<br>`docs/roles/acceptance-criteria.md` | 📝 Not Started |

## Branch Status Legend

- 📝 **Not Started** — Team has not created branch yet
- 🔄 **In Progress** — Branch exists, commits are being made
- 👀 **In Review** — PR is open and under review
- ✅ **Complete** — PR merged to `main`, branch deleted

## Ownership Rules

1. **One team per agent file** — Teams only edit their assigned agent and role doc.
2. **Catalog updates deferred** — Teams do NOT edit `docs/agent-catalog.md` during development. The integrator will consolidate all entries after individual PRs merge.
3. **Shared files** — If a team needs to edit a shared file (e.g., `.github/instructions/`), coordinate in team channel first.

## Merge Order

To minimize conflicts, merge in this sequence:

1. **Phase 1:** Requirements Analyst (Team A) — foundational patterns
2. **Phase 2:** Stakeholder Impact (Team B) + Process Mapper (Team C) — parallel
3. **Phase 3:** BA Review (Team D) + Acceptance Criteria (Team E) — parallel
4. **Phase 4:** Integrator consolidates `docs/agent-catalog.md`

## Integrator Role

**Assigned to:** `@maintainer` (update with GitHub username)

**Responsibilities:**
- Review all merged agent PRs
- Create single consolidation PR for `docs/agent-catalog.md`
- Validate cross-agent consistency (e.g., no overlapping scopes)
- Update this matrix with final merged status

## Rotation Plan

After this cohort completes:
- Teams rotate to new roles
- Update this matrix with new assignments
- Archive this version as `team-branch-matrix-cohort1.md`
