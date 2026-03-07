# Workflows Directory Deprecation Notice

The `workflows/` runtime model is deprecated and no longer the canonical way to run agent pipelines in this repository.

## Use these canonical paths instead

- Pipeline orchestration guide: [`docs/problem-statement-decomposition-pipeline.md`](../docs/problem-statement-decomposition-pipeline.md)
- Pipeline stage agents:
  - [`../.github/agents/psd-a-normalizer.agent.md`](../.github/agents/psd-a-normalizer.agent.md)
  - [`../.github/agents/psd-b-extractor.agent.md`](../.github/agents/psd-b-extractor.agent.md)
  - [`../.github/agents/psd-c-classifier.agent.md`](../.github/agents/psd-c-classifier.agent.md)
  - [`../.github/agents/psd-d-auditor.agent.md`](../.github/agents/psd-d-auditor.agent.md)
  - [`../.github/agents/psd-e-packager.agent.md`](../.github/agents/psd-e-packager.agent.md)
  - [`../.github/agents/psd-f-excel-formatter.agent.md`](../.github/agents/psd-f-excel-formatter.agent.md)

Legacy workflow files were moved to `docs/archive/workflows/` and are frozen for historical reference only.
