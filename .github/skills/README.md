# Copilot Skills

Store reusable Copilot skills as folder-based capability packages in this directory.

Use skills for repeatable capabilities that prompts and agents can invoke across the repository.
If a prompt exists for the same task, the skill should remain the canonical home for the full procedure.
Keep the loader-friendly package format `<capability-name>\SKILL.md` and use the shared capability slug as the folder name.

Examples:

- `workspace-setup/SKILL.md` for lightweight input/output workspace setup and usage
- `git-operations/SKILL.md` for safe, repeatable repository Git workflows
