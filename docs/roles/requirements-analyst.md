# Requirements Analyst Role

## Overview

The Requirements Analyst agent specializes in eliciting, clarifying, and refining business requirements with a focus on eliminating ambiguity and ensuring testability.

## When to Use

Invoke this agent when:
- Starting requirements elicitation from business stakeholders
- Reviewing user stories or feature requests for clarity
- Identifying missing, conflicting, or ambiguous requirements
- Writing or refining acceptance criteria
- Preparing requirements for development handoff

## Agent File

[`.github/agents/requirements-analyst/requirements-analyst.agent.md`](../../.github/agents/requirements-analyst/requirements-analyst.agent.md)

## Input Expectations

The agent expects:
- Business objectives or problem statements
- Draft requirements, user stories, or feature descriptions
- Stakeholder inputs or interview notes
- Existing documentation to review

## Output Format

The agent produces:

1. **Findings**
   - Ambiguities flagged with specific language issues
   - Gaps where critical information is missing
   - Conflicts between stated requirements

2. **Rewritten Requirements**
   - Clear, actionable requirement statements
   - Consistent format and terminology
   - Numbered for traceability

3. **Acceptance Criteria**
   - Given/When/Then format where applicable
   - Measurable, testable outcomes
   - Edge cases and error conditions covered

4. **Open Questions**
   - Unresolved assumptions
   - Areas needing stakeholder clarification
   - Risks or dependencies

## Example Interaction

**Input:**
```
User story: "As a manager, I want to see reports so I can make decisions."
```

**Output:**
```
Findings:
- Ambiguous: "see reports" - what type of reports? frequency? format?
- Ambiguous: "make decisions" - what decisions? what data drives them?
- Missing: who else needs access? what time period should reports cover?

Rewritten Requirement:
REQ-001: The system shall generate weekly sales performance reports 
showing revenue by product line, displayed in HTML dashboard format, 
accessible to managers and executives.

Acceptance Criteria:
- Given I am a manager, when I navigate to Reports > Sales Performance, 
  then I see the current week's data by default
- Given the report is displayed, when I filter by product line, 
  then only selected product data appears
- Given no sales data exists for the period, when I load the report, 
  then I see a message "No data available for selected period"

Open Questions:
- Should historical trend data (6-month comparison) be included?
- What is the expected report load time SLA?
- Do we need export to Excel functionality?
```

## Tips for Teams

- **Start broad, then narrow:** Let the agent identify all ambiguities first, then refine incrementally.
- **Provide context:** Share relevant business objectives or constraints to get better results.
- **Iterate:** Use the "Open Questions" output to gather more stakeholder input, then re-run.
- **Review for domain fit:** Validate that rewritten requirements align with your project terminology.

## Related Agents

- **BA Review Specialist:** Use after Requirements Analyst to validate deliverable completeness.
- **Stakeholder Impact Analyzer:** Use to understand who will be affected by the requirements.
- **Process Mapper:** Use to see how requirements fit into current/future workflows.

## Owner

**Team A** (update with GitHub `@username` or team contact)
