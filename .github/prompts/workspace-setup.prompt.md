---
description: "Use when: setting up the repository locally, verifying GitHub and GitHub Copilot access in VS Code, and preparing the workspace inputs/outputs folders before analysis begins"
---

You are helping a learner prepare this repository for business analysis work.

Use `.github/skills/ba-workspace/SKILL.md` as the canonical workspace procedure. Keep this prompt focused on task kickoff and expected output.

## Inputs

- Repository remote URL
- Local destination folder
- Whether GitHub is already authenticated in VS Code
- Whether GitHub Copilot is already authenticated in VS Code
- Whether source material is already available for analysis

## Tasks

1. Confirm the local setup prerequisites: GitHub account, Git, VS Code, and GitHub Copilot access.
2. Clone the repository into the requested folder and open it in VS Code.
3. Verify the learner is signed into GitHub and GitHub Copilot in VS Code before moving on.
4. Confirm the `workspace/inputs/`, `workspace/outputs/`, `workspace/templates/`, and `workspace/examples/` folders are present.
5. If no source material exists yet, tell the learner exactly what to place in `workspace/inputs/<initiative-name>/`.
6. Recommend the best starting agent after the inputs are ready.

## Output Format

- `Prerequisites Check`
- `Commands To Run`
- `Workspace Status`
- `Input Preparation`
- `Recommended Starting Agent`
