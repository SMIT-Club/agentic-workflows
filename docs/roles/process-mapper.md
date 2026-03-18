# Process Mapper Role

## Overview

The Process Mapper agent documents current state processes, designs future state workflows, and identifies gaps, bottlenecks, and improvement opportunities.

## When to Use

Invoke this agent when:
- Documenting existing business processes
- Designing future state workflows for process improvement initiatives
- Analyzing handoffs, decision points, and bottlenecks
- Preparing process documentation for automation or system implementation
- Conducting gap analysis between current and desired states

## Agent File

[`.github/agents/process-mapper/process-mapper.agent.md`](../../.github/agents/process-mapper/process-mapper.agent.md)

## Input Expectations

The agent expects:
- Description of the process to analyze (e.g., "customer onboarding")
- Known process steps, roles, and systems involved
- Pain points or improvement goals
- Future state vision or objectives

## Output Format

The agent produces:

1. **Current State Process**
   - Sequential or parallel steps with clear names
   - Roles or actors responsible for each step
   - Inputs required and outputs produced
   - Decision points and branching logic
   - Identified bottlenecks or delays

2. **Future State Process**
   - Redesigned workflow steps
   - Role changes or consolidations
   - Eliminated, automated, or streamlined steps
   - New decision rules or triggers

3. **Gap Analysis**
   - Steps to add, remove, or modify
   - Training needs for role changes
   - System or tool requirements
   - Timeline and sequencing considerations

4. **Risks and Dependencies**
   - Upstream dependencies (what must happen first)
   - Downstream impacts (who/what is affected)
   - Transition risks during implementation

5. **Success Metrics**
   - Measurable improvements (e.g., cycle time reduction, error rate decrease)
   - Key performance indicators (KPIs)
   - Monitoring and reporting approach

## Example Interaction

**Input:**
```
Process: Customer onboarding for new accounts
Goal: Reduce onboarding time from 5 days to 2 days
```

**Output:**
```
Current State Process:
1. Sales submits paper form to Operations (manual handoff)
2. Operations Manager reviews and approves (1-day delay)
3. Data entry clerk enters info into CRM (30 min, error-prone)
4. IT provisions accounts (2 days, manual ticket)
5. Training team schedules onboarding call (2 days)
   Decision: If enterprise customer → escalate to Account Manager

Bottlenecks:
- Step 2: Manual approval creates 1-day delay
- Step 4: IT provisioning requires manual ticket and has 2-day SLA

Future State Process:
1. Sales submits digital form with auto-validation (instant)
2. Auto-approval for standard accounts; Manager review only for exceptions (<1 hour)
3. CRM auto-populated from form (instant, no errors)
4. IT accounts auto-provisioned via API (1 hour)
5. Training invitation auto-sent with calendar link (instant)

Eliminated Steps:
- Manual data entry (replaced by form integration)
- Manual IT ticket (replaced by API automation)

Gap Analysis:
- Need: Digital form builder integrated with CRM
- Need: API between CRM and IT provisioning system
- Training: Sales team on new digital form process (1-hour session)
- Timeline: 3-month implementation (form = 1 month, API = 2 months)

Risks:
- Dependency: IT API availability depends on infrastructure upgrade project
- Risk: Auto-approval may miss edge cases → Mitigation: Exception handling rules + Manager alerts

Success Metrics:
- Onboarding cycle time: Target <2 days (current: 5 days)
- Error rate: Target <2% (current: ~15% due to manual entry)
- Customer satisfaction: Target >90% (current: 75%)
```

## Tips for Teams

- **Walk the process:** Interview people who actually do the work, not just managers.
- **Focus on handoffs:** Most bottlenecks occur at transitions between roles or systems.
- **Be realistic about automation:** Not every step should or can be automated.
- **Include exception paths:** Document what happens when things go wrong.

## Related Agents

- **Requirements Analyst:** Use to define system requirements from process gaps.
- **Stakeholder Impact Analyzer:** Use to understand which roles are affected by process changes.
- **BA Review Specialist:** Use to validate process documentation completeness.

## Owner

**Team C** (update with GitHub `@username` or team contact)
