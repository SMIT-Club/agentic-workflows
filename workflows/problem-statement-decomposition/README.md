# Problem Statement Decomposition Workflow

## Purpose

This workflow helps break down complex problem statements into manageable, analyzable components. It guides AI agents and business analysts through a systematic decomposition process using a deterministic, JSON-based agent pipeline designed for ITBA1002 learners.

## Workflow Steps

The workflow consists of six sequential agents that process information through a structured pipeline:

| Step | Agent | Input | Output | Description |
|------|-------|-------|--------|-------------|
| 1 | **A_Normalizer** | Raw text (email, ticket, transcript, notes, etc.) | A_OUT | Converts unstructured text into standardized JSON with ordered content blocks |
| 2 | **B_Extractor** | A_OUT | B_OUT | Extracts verbatim observations from content blocks into an ordered ledger |
| 3 | **C_Classifier** | B_OUT | C_OUT | Assigns strategic categories and core concept labels to each observation |
| 4 | **D_Auditor** | B_OUT + C_OUT | D_OUT | Identifies risks, policy violations, and elicitation gaps |
| 5 | **E_Packager** | B_OUT + C_OUT + D_OUT | E_OUT | Transforms outputs into a student-friendly review artifact |
| 6 | **F_ExcelFormatter** | E_OUT | Excel file | Converts final JSON to structured Excel spreadsheet |

## Agent Files

- `A_Normalizer.md` - Text normalization agent
- `B_Extractor.md` - Observation extraction agent
- `C_Classifier.md` - Category classification agent
- `D_Auditor.md` - Risk and gap auditing agent
- `E_Packager.md` - Review artifact packaging agent
- `F_ExcelFormatter.md` - Excel output formatting agent

## Data Flow

```
Raw Text → A_Normalizer → A_OUT
                           ↓
                      B_Extractor → B_OUT
                                      ↓
                                 C_Classifier → C_OUT
                                                  ↓
                      B_OUT + C_OUT → D_Auditor → D_OUT
                                                    ↓
              B_OUT + C_OUT + D_OUT → E_Packager → E_OUT
                                                     ↓
                                          F_ExcelFormatter → Excel File
```

## How to Use

### For AI Agents
Execute each agent sequentially, passing the JSON output from one agent as input to the next. Each agent:
- Accepts ONLY valid JSON input (or raw text for A_Normalizer)
- Outputs ONLY valid JSON matching its schema
- Returns an error object if it cannot comply

### For Human Analysts
1. Gather your problem statement source material (emails, tickets, transcripts, notes)
2. Feed the raw text to A_Normalizer
3. Pass outputs through each subsequent agent in order
4. Review the final E_OUT artifact and Excel spreadsheet
5. Use elicitation gaps to guide follow-up questions

## Output Schemas

| Agent | Output Key | Description |
|-------|------------|-------------|
| A_Normalizer | `A_OUT` | Source metadata + ordered content blocks |
| B_Extractor | `B_OUT` | Observation ledger with verbatim quotes |
| C_Classifier | `C_OUT` | Classified observations with categories |
| D_Auditor | `D_OUT` | Flags and elicitation gaps |
| E_Packager | `E_OUT` | Table rows, flags summary, and gaps |
| F_ExcelFormatter | `.xlsx` | Formatted Excel spreadsheet |

## Categories

### Strategic Analysis Categories
- Business analysis approach
- Enterprise limitation
- Organizational strategy
- Solution limitation
- Solution performance goals
- Solution performance measures
- Stakeholder analysis results
- Needs
- Elicitation results

### Core Concept Labels
- Need
- Value
- Solution
- Stakeholder
- Change
- Context

## Customization

You can adapt this workflow by:
- Adding additional agents for domain-specific analysis
- Modifying category lists to fit your context
- Extending the flag types in D_Auditor
- Customizing the Excel output format in F_ExcelFormatter
