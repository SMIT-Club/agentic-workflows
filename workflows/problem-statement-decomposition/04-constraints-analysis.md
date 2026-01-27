# Step 4: Constraints Analysis

## Objective
Identify and document all constraints, assumptions, dependencies, and limitations that affect the problem and potential solutions.

## Context
Understanding constraints is critical for developing realistic solutions. Constraints can be technical, financial, organizational, regulatory, or time-based.

## Instructions

### For AI Agents
1. Analyze the problem components from Step 3
2. Identify all relevant constraints and limitations
3. Document assumptions being made
4. Map dependencies between components and external factors
5. Assess the impact of each constraint on potential solutions

### For Human Analysts
1. Review the problem breakdown
2. For each component, ask:
   - What limits our ability to address this?
   - What assumptions are we making?
   - What depends on this or what does this depend on?
   - What external factors influence this?
3. Categorize and prioritize constraints

## Input Requirements
- **Problem Components** (from Step 3)
- **Stakeholder Information** (from Step 2)
- **Organizational Resources**: Budget, time, personnel
- **Technical Capabilities**: Systems, tools, infrastructure
- **Regulatory Requirements**: Laws, policies, standards

## Output Deliverables

### Constraints Inventory

#### Resource Constraints
| Type | Description | Impact Level | Flexibility |
|------|-------------|--------------|-------------|
| Budget | [Description] | High/Medium/Low | Fixed/Negotiable |
| Time | [Description] | High/Medium/Low | Fixed/Negotiable |
| Personnel | [Description] | High/Medium/Low | Fixed/Negotiable |

#### Technical Constraints
- **Technology**: [Existing systems, platforms, tools that must be used or avoided]
- **Integration**: [Systems that must integrate or interoperate]
- **Performance**: [Speed, capacity, or scalability requirements]
- **Security**: [Security and privacy requirements]

#### Organizational Constraints
- **Policies**: [Internal policies that must be followed]
- **Culture**: [Organizational norms and resistance points]
- **Processes**: [Existing processes that cannot be changed]
- **Politics**: [Political considerations and sensitivities]

#### External Constraints
- **Regulatory**: [Laws, regulations, compliance requirements]
- **Market**: [Market conditions, competition, customer expectations]
- **Environmental**: [Physical or environmental limitations]

### Assumptions
```
List all assumptions being made:
1. [Assumption 1] - Impact: [High/Medium/Low]
   Validation needed: [Yes/No] - How: [Method]
   
2. [Assumption 2] - Impact: [High/Medium/Low]
   Validation needed: [Yes/No] - How: [Method]
```

### Dependencies Map
```
Component/Solution Element -> Depends On -> External Factor

[Component 1] -> [Dependency 1] -> [Description]
[Component 2] -> [Dependency 2] -> [Description]
```

### Critical Path Items
```
[Identify items that must be addressed first due to dependencies]
1. [Item 1] - Reason: [Why this is critical]
2. [Item 2] - Reason: [Why this is critical]
```

## Risk Assessment
Document risks related to constraints:

| Risk | Likelihood | Impact | Mitigation Strategy |
|------|------------|--------|---------------------|
| [Risk 1] | High/Med/Low | High/Med/Low | [Strategy] |
| [Risk 2] | High/Med/Low | High/Med/Low | [Strategy] |

## Quality Checklist
- [ ] All major constraint categories addressed
- [ ] Assumptions explicitly stated and assessed
- [ ] Dependencies clearly mapped
- [ ] Critical path items identified
- [ ] Risks documented with mitigation strategies
- [ ] Constraints prioritized by impact

## Next Step
Proceed to `05-synthesis.md` to synthesize findings into actionable insights.
