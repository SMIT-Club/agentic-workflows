# BA Review Specialist Role

## Overview

The BA Review Specialist agent validates the quality and completeness of business analysis deliverables, checking for traceability, testability, and adherence to standards.

## When to Use

Invoke this agent when:
- Reviewing BA deliverables before stakeholder sign-off
- Auditing requirements documentation for gaps or inconsistencies
- Validating traceability from business need through acceptance criteria
- Preparing deliverables for development team handoff
- Conducting peer review or quality assurance on BA work

## Agent File

[`.github/agents/ba-review/ba-review.agent.md`](../.github/agents/ba-review/ba-review.agent.md)

## Input Expectations

The agent expects:
- BA deliverables to review (e.g., requirements document, user stories, BRD)
- Template or standard the deliverable should follow
- Traceability expectations (e.g., requirements linked to business objectives)
- Quality criteria or acceptance standards

## Output Format

The agent produces:

1. **Completeness Check**
   - Required sections marked present (✅) or missing (❌)
   - Specific gaps flagged

2. **Quality Assessment**
   - Ambiguous requirements with line/section references
   - Untestable acceptance criteria
   - Undefined terms or jargon
   - Formatting inconsistencies

3. **Traceability Validation**
   - Requirements without business justification
   - Acceptance criteria without linked requirements
   - Orphaned or duplicate items

4. **Improvement Recommendations**
   - Priority (High/Medium/Low)
   - Specific issue description
   - Recommended fix
   - Example of good practice

5. **Risk Summary**
   - High-risk gaps that could block delivery
   - Medium-risk quality issues
   - Low-risk polish items

## Example Interaction

**Input:**
```
Document: Requirements Specification for Invoice Processing System
Template: Standard BRD with sections: Business Objectives, Stakeholders, 
Requirements, Acceptance Criteria, Assumptions, Risks
```

**Output:**
```
Completeness Check:
✅ Business Objectives
✅ Stakeholders
✅ Requirements (15 items)
❌ Acceptance Criteria (missing for REQ-007, REQ-012)
✅ Assumptions
❌ Risks (section empty)

Quality Assessment:
1. REQ-003: "System should process invoices quickly"
   Issue: Ambiguous - "quickly" not defined
   Recommendation: Replace with measurable SLA (e.g., "<2 seconds per invoice")

2. REQ-007: No acceptance criteria
   Issue: Cannot test without clear success conditions
   Recommendation: Add Given/When/Then scenarios

3. Undefined terms: "legacy system" used 4 times without definition
   Recommendation: Add glossary or define on first use

Traceability Validation:
- REQ-009 and REQ-010 have no link to Business Objective
  → Are these requirements necessary?
- AC-003 references REQ-015, which doesn't exist
  → Likely typo, should be REQ-005

Improvement Recommendations:

HIGH PRIORITY:
- Add acceptance criteria for REQ-007 and REQ-012 (blocks testing)
- Populate Risks section (required for sign-off)
- Define "legacy system" or replace with specific system name

MEDIUM PRIORITY:
- Replace "quickly" in REQ-003 with measurable performance target
- Fix traceability link AC-003 → REQ-005
- Justify REQ-009 and REQ-010 by linking to business objectives

LOW PRIORITY:
- Standardize requirement numbering (currently mixed "REQ-01" and "REQ-001")
- Add version number and change log to document header

Risk Summary:
🔴 HIGH RISK: Missing acceptance criteria blocks test planning
🟡 MEDIUM RISK: Ambiguous performance requirements could cause scope disputes
🟢 LOW RISK: Formatting inconsistencies affect readability but not content
```

## Tips for Teams

- **Run early and often:** Don't wait until final review to check quality.
- **Use as learning tool:** Share findings with authors to teach best practices.
- **Prioritize feedback:** Fix high-risk issues first; defer polish items.
- **Automate where possible:** Use templates and checklists to catch common issues.

## Related Agents

- **Requirements Analyst:** Use this agent to write/refine requirements, then use BA Review to validate.
- **Stakeholder Impact Analyzer:** Ensure stakeholder section completeness.
- **Process Mapper:** Validate process documentation against standards.

## Owner

**Team D** (update with GitHub `@username` or team contact)
