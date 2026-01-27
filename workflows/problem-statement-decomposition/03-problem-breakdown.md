# Step 3: Problem Breakdown

## Objective
Decompose the complex problem into smaller, manageable components that can be analyzed and addressed individually.

## Context
Breaking down a complex problem into components makes it easier to understand, analyze, and solve. This step uses structured decomposition techniques.

## Instructions

### For AI Agents
1. Review the problem statement and stakeholder perspectives
2. Identify the core components of the problem
3. Use decomposition frameworks (e.g., 5 Whys, Issue Trees, MECE principle)
4. Create a hierarchical breakdown of the problem
5. Ensure components are actionable and measurable

### For Human Analysts
1. Start with the main problem statement
2. Ask "What are the key elements of this problem?"
3. For each element, ask "What contributes to this?"
4. Continue breaking down until you reach actionable components
5. Organize components hierarchically or by category

## Input Requirements
- **Validated Problem Statement** (from Step 1)
- **Stakeholder Perspectives** (from Step 2)
- **Domain Expertise**: Subject matter knowledge to inform decomposition

## Output Deliverables

### Problem Hierarchy
```
Main Problem: [Problem Statement]
├── Component 1: [Description]
│   ├── Sub-component 1.1: [Description]
│   ├── Sub-component 1.2: [Description]
│   └── Sub-component 1.3: [Description]
├── Component 2: [Description]
│   ├── Sub-component 2.1: [Description]
│   └── Sub-component 2.2: [Description]
└── Component 3: [Description]
    ├── Sub-component 3.1: [Description]
    └── Sub-component 3.2: [Description]
```

### Component Analysis

For each major component, document:

#### Component: [Name]
- **Description**: [What is this component?]
- **Contributing Factors**: [What causes or influences this?]
- **Impact**: [How does this affect the overall problem?]
- **Measurability**: [How can we measure this?]
- **Interdependencies**: [How does this relate to other components?]

### Root Causes
```
[Identify potential root causes using 5 Whys or similar analysis]

Problem: [Component]
Why? [Reason 1]
Why? [Reason 2]
Why? [Reason 3]
Why? [Reason 4]
Why? [Root Cause]
```

## Quality Checklist
- [ ] Problem broken into logical, manageable components
- [ ] Components are mutually exclusive and collectively exhaustive (MECE)
- [ ] Each component is clearly defined
- [ ] Relationships between components documented
- [ ] Root causes identified where applicable

## Next Step
Proceed to `04-constraints-analysis.md` to identify constraints, assumptions, and dependencies.
