# Stakeholder Impact Analyzer Role

## Overview

The Stakeholder Impact Analyzer agent identifies stakeholders, assesses change impacts, and develops communication strategies for business initiatives.

## When to Use

Invoke this agent when:
- Starting a new project or initiative
- Planning organizational change
- Preparing change management or communication plans
- Identifying resistance risks
- Mapping stakeholder groups and their concerns

## Agent File

[`.github/agents/stakeholder-impact/stakeholder-impact.agent.md`](../../.github/agents/stakeholder-impact/stakeholder-impact.agent.md)

## Input Expectations

The agent expects:
- Description of the proposed change or initiative
- Known stakeholder groups or organizational chart
- Business objectives and success criteria
- Risks or concerns already identified

## Output Format

The agent produces:

1. **Stakeholder Matrix**
   - Complete list of affected stakeholder groups
   - Impact rating (High/Medium/Low)
   - Influence rating (High/Medium/Low)
   - Likely position (Support/Neutral/Resist)

2. **Impact Analysis per Stakeholder**
   - Positive impacts (benefits they will experience)
   - Negative impacts (disruptions or losses)
   - Key concerns and risks

3. **Communication Plan**
   - Tailored key messages per group
   - Preferred communication channels
   - Timing and frequency recommendations

4. **Risk Mitigation**
   - Resistance points and sources
   - Recommended actions to address concerns
   - Success criteria for change adoption

## Example Interaction

**Input:**
```
Initiative: Migrate from manual timesheet entry to automated time tracking system.
```

**Output:**
```
Stakeholder Matrix:
| Group | Impact | Influence | Position |
|-------|--------|-----------|----------|
| Employees | High | Medium | Resist |
| Managers | Medium | High | Neutral |
| Payroll Team | High | Medium | Support |
| IT Support | Medium | Low | Neutral |

Impact Analysis:
- Employees: 
  - Negative: Loss of control over time entry, learning curve
  - Positive: Less time spent on manual entry
  - Concerns: Privacy, accuracy of automated tracking
  
- Managers:
  - Positive: Real-time visibility into team hours
  - Negative: Initial setup and training time
  - Concerns: Adoption rate, accuracy validation

Communication Plan:
- Employees: Town halls + FAQs, emphasize privacy protections and time savings
- Managers: Email update + demo sessions, highlight reporting features
- Payroll: Direct training, emphasize integration and error reduction

Risk Mitigation:
- Resistance from employees due to privacy concerns
  → Action: Publish transparent data usage policy, offer opt-out for certain roles
  → Success: >80% adoption within 60 days
```

## Tips for Teams

- **Cast a wide net:** Include indirect stakeholders (e.g., external partners, customers).
- **Be realistic about resistance:** Don't assume all groups will support the change.
- **Tailor messages:** Generic communication plans fail; customize per group.
- **Link to business value:** Show stakeholders how the change benefits them specifically.

## Related Agents

- **Requirements Analyst:** Use to clarify functional requirements driven by stakeholder needs.
- **Process Mapper:** Use to understand current workflows affected by stakeholder groups.
- **BA Review Specialist:** Use to validate stakeholder analysis completeness.

## Owner

**Team B** (update with GitHub `@username` or team contact)
