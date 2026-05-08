# Problem Statement Decomposition Pipeline

This is the canonical orchestration guide for the Problem Statement Decomposition (PSD) workflow family.

## Entrypoint

- **PSD Orchestrator**: [`.github/agents/psd-orchestrator.agent.md`](../.github/agents/psd-orchestrator.agent.md)

Use the orchestrator when you want:

- the full A -> F workflow
- a checkpointed run with explicit breakpoints
- a resume point from an existing PSD artifact

The stage agents are internal workflow components and should not be selected directly from the Copilot agent picker.

## Stage order (A -> F)

1. **A_Normalizer** (internal): [`.github/agents/psd-a-normalizer.agent.md`](../.github/agents/psd-a-normalizer.agent.md)
2. **B_Extractor** (internal): [`.github/agents/psd-b-extractor.agent.md`](../.github/agents/psd-b-extractor.agent.md)
3. **C_Classifier** (internal): [`.github/agents/psd-c-classifier.agent.md`](../.github/agents/psd-c-classifier.agent.md)
4. **D_Auditor** (internal): [`.github/agents/psd-d-auditor.agent.md`](../.github/agents/psd-d-auditor.agent.md)
5. **E_Packager** (internal): [`.github/agents/psd-e-packager.agent.md`](../.github/agents/psd-e-packager.agent.md)
6. **F_ExcelFormatter** (internal): [`.github/agents/psd-f-excel-formatter.agent.md`](../.github/agents/psd-f-excel-formatter.agent.md)

## Input/output handoff

| Stage | Input | Output |
|---|---|---|
| A_Normalizer | Raw project text | `A_OUT` |
| B_Extractor | `A_OUT` | `B_OUT` |
| C_Classifier | `B_OUT` | `C_OUT` |
| D_Auditor | `B_OUT` + `C_OUT` | `D_OUT` |
| E_Packager | `B_OUT` + `C_OUT` + `D_OUT` | `E_OUT` |
| F_ExcelFormatter | `E_OUT` | `.xlsx` workbook |

## Invocation guidance

### For human users

1. Collect the raw source text (email, transcript, ticket, notes, or document excerpt).
2. Invoke `psd-orchestrator.agent.md` when you want coordinated stage execution or breakpoint handling.
3. If you are running manually, start with `psd-a-normalizer.agent.md` and pass each stage output to the next stage in strict order.
4. Use `E_OUT` for review and `psd-f-excel-formatter.agent.md` for spreadsheet delivery.
5. If a stage returns an error object, fix input validity and rerun that stage.

### For AI IDE agents

1. Prefer `psd-orchestrator.agent.md` as the PSD entrypoint.
2. Enforce exact schema handoffs between stages.
3. Do not skip deterministic validation rules defined in each agent spec.
4. Preserve traceability IDs (`source_id`, `block_id`, `obs_id`, `flag_id`, `gap_id`) across handoffs.
5. Stop at user-requested breakpoints rather than collapsing multiple stages into one opaque step.

## Legacy location

The old workflow markdown files are archived at:

- [`docs/archive/workflows/problem-statement-decomposition/`](archive/workflows/problem-statement-decomposition/README.md)

Archived content is frozen and retained for historical reference.
