# Agent Catalog

This catalog is the quick index for all shared BA agents and prompts.

> **Note:** This catalog is maintained by the designated integrator. Teams should NOT edit this file in their PRs — update your role documentation in `docs/roles/` instead.

## Agents

| Name | File | Use When | Role Docs | Owner |
|---|---|---|---|---|
| Requirements Analyst | [requirements-analyst.agent.md](../.github/agents/requirements-analyst.agent.md) | Elicitation, ambiguity cleanup, acceptance criteria | [Role Guide](roles/requirements-analyst.md) | Team A |
| Stakeholder Impact Analyzer | [stakeholder-impact.agent.md](../.github/agents/stakeholder-impact.agent.md) | Identifying stakeholders, change impact, communication planning | [Role Guide](roles/stakeholder-impact.md) | Team B |
| Process Mapper | [process-mapper.agent.md](../.github/agents/process-mapper.agent.md) | Current/future state workflows, gap analysis, bottlenecks | [Role Guide](roles/process-mapper.md) | Team C |
| BA Review Specialist | [ba-review.agent.md](../.github/agents/ba-review.agent.md) | Quality review, traceability validation, completeness checks | [Role Guide](roles/ba-review.md) | Team D |
| PSD A Normalizer | [psd-a-normalizer.agent.md](../.github/agents/psd-a-normalizer.agent.md) | Normalize raw source text into `A_OUT` with ordered content blocks | [Pipeline Guide](problem-statement-decomposition-pipeline.md#stage-order-a---f) | Integrator |
| PSD B Extractor | [psd-b-extractor.agent.md](../.github/agents/psd-b-extractor.agent.md) | Extract verbatim observations from `A_OUT` into `B_OUT` | [Pipeline Guide](problem-statement-decomposition-pipeline.md#stage-order-a---f) | Integrator |
| PSD C Classifier | [psd-c-classifier.agent.md](../.github/agents/psd-c-classifier.agent.md) | Classify observations from `B_OUT` into `C_OUT` categories | [Pipeline Guide](problem-statement-decomposition-pipeline.md#stage-order-a---f) | Integrator |
| PSD D Auditor | [psd-d-auditor.agent.md](../.github/agents/psd-d-auditor.agent.md) | Audit `B_OUT` and `C_OUT` into risk and gap output `D_OUT` | [Pipeline Guide](problem-statement-decomposition-pipeline.md#stage-order-a---f) | Integrator |
| PSD E Packager | [psd-e-packager.agent.md](../.github/agents/psd-e-packager.agent.md) | Package pipeline outputs into learner-facing `E_OUT` | [Pipeline Guide](problem-statement-decomposition-pipeline.md#stage-order-a---f) | Integrator |
| PSD F Excel Formatter | [psd-f-excel-formatter.agent.md](../.github/agents/psd-f-excel-formatter.agent.md) | Convert `E_OUT` into a formatted `.xlsx` workbook | [Pipeline Guide](problem-statement-decomposition-pipeline.md#stage-order-a---f) | Integrator |

## Prompts

| Name | File | Use When | Owner |
|---|---|---|---|
| BA Kickoff | [ba-kickoff.prompt.md](../.github/prompts/ba-kickoff.prompt.md) | New initiative kickoff and discovery planning | _TBD_ |

## Adding New Entries

**Process:**
1. Team creates agent/prompt in their branch
2. Team updates role documentation in `docs/roles/`
3. Team opens PR (does NOT edit this catalog)
4. After PR merges, integrator adds entry to this catalog
5. Integrator opens single consolidation PR

**Integrator:** `@maintainer` (update with GitHub username)
