## Description

One sentence: What agent/prompt/instruction is changed and why?

## Type of Change

- [ ] New agent/prompt/instruction
- [ ] Update existing agent/prompt/instruction
- [ ] Bug fix (YAML, formatting, or logic error)
- [ ] Documentation only
- [ ] Workflow or process change

## What Changed

List files modified and summarize changes in 3-4 bullets:

- `.github/agents/my-agent.agent.md` - Added stakeholder impact analysis agent
- `docs/roles/stakeholder-impact.md` - Added role documentation and examples
- `docs/agent-catalog.md` - Added catalog entry

## Testing / Validation

Describe how you tested the agent/prompt behavior:

- [ ] Tested agent invocation in VS Code with 2+ realistic scenarios
- [ ] Validated YAML frontmatter syntax (copy-paste into YAML validator)
- [ ] Reviewed output format against documented schema
- [ ] Checked for tool list justification

**Example interaction:**

```
Input: <describe test input>
Output: <describe result or attach screenshot>
```

## Catalog Update

- [ ] `docs/agent-catalog.md` updated with new entry
- [ ] Owner assigned (GitHub `@username` or team role)
- [ ] Use case documented with trigger phrases

## Review Checklist

- [ ] Frontmatter is valid YAML (`name`, `description`, `tools`, `user-invocable`)
- [ ] `description` field starts with "Use when:" and includes trigger keywords
- [ ] Scope is narrow and does not overlap with existing agents
- [ ] Output format is explicit and testable
- [ ] Tool list is minimal for the task (justify if more than 3 tools)
- [ ] No implementation code in agent instructions
- [ ] Constraints section includes clear "DO NOT" boundaries
- [ ] Examples or walkthroughs included in PR description

## Related Issues

Closes #___ (if applicable)

## Notes for Reviewers

Any specific areas needing attention? Expected behavior changes?
