# GitHub Project CLI Operations Guide

Use this guide to get team members up and running with GitHub Project CLI workflows for the `SMIT-Club/agentic-workflows` repository.

## Purpose

Use this document as a practical starting point for:

- authenticating `gh` for project write access
- understanding the difference between issue properties and project fields
- creating and updating project items from the command line
- running an initial validation workflow
- maintaining and cleaning up project artifacts over time

## Prerequisites

Before running the workflows, make sure you have:

- GitHub CLI installed
- access to the `SMIT-Club` organization
- access to the `Agent Task Tracker` project
- access to the `SMIT-Club/agentic-workflows` repository

## 1. Start GitHub CLI access

Check whether `gh` is already authenticated:

```powershell
gh auth status
```

If you are not signed in, log in:

```powershell
gh auth login
```

Recommended answers:

1. GitHub.com
2. HTTPS
3. Login with a web browser

GitHub CLI may open a browser automatically, or it may show a device code and ask you to visit:

```text
https://github.com/login/device
```

Enter the one-time code shown by `gh`, complete the authorization in the browser, and return to the terminal.

## 2. Refresh the token for project write access

Standard GitHub authentication is often not enough for project edits. Creating or editing project items requires the `project` scope.

Check current scopes:

```powershell
gh auth status
```

If project edits fail with a message similar to:

```text
your authentication token is missing required scopes [project]
```

refresh authentication with the required scope:

```powershell
gh auth refresh -s project
```

You may be prompted to:

1. confirm Git authentication in the terminal
2. open the browser or device login page
3. approve the new scope in GitHub

After approval, verify again:

```powershell
gh auth status
```

## 3. Identify the project and available fields

List organization projects:

```powershell
gh project list --owner SMIT-Club
```

List fields for the `Agent Task Tracker` project:

```powershell
gh project field-list 2 --owner SMIT-Club
gh project field-list 2 --owner SMIT-Club --format json
```

Typical fields used in project operations:

- `Status`
- `Priority`
- `Size`
- `Estimate`
- `Iteration`

Mirrored issue-backed fields may also appear in the project:

- `Assignees`
- `Labels`
- `Milestone`
- `Repository`

## Workflow A: First-run draft item validation

Use this workflow as a low-risk first step to confirm basic project item creation and project field updates without creating a repository issue.

### Create the draft item

```powershell
gh project item-create 2 --owner SMIT-Club `
  --title "Test backlog item" `
  --body "Created by GitHub CLI to validate draft-item creation."
```

### Set the item back to Backlog

First capture the project field IDs and option IDs from `gh project field-list 2 --owner SMIT-Club --format json`, then edit the item:

```powershell
gh project item-edit `
  --id <item-id> `
  --project-id <project-id> `
  --field-id <status-field-id> `
  --single-select-option-id <backlog-option-id>
```

### Validate the result

```powershell
gh api graphql -f query='
query($id: ID!) {
  node(id: $id) {
    ... on ProjectV2Item {
      id
      project { title }
      content {
        ... on DraftIssue {
          title
          body
        }
      }
      fieldValues(first: 20) {
        nodes {
          ... on ProjectV2ItemFieldSingleSelectValue {
            field { ... on ProjectV2FieldCommon { name } }
            name
          }
        }
      }
    }
  }
}' -F id=<item-id>
```

## Workflow B: Issue-backed project property validation

Use this workflow when you want to confirm both:

- repository issue properties such as `Type`, labels, assignee, and milestone
- project-only properties such as `Status`, `Priority`, `Size`, `Estimate`, and `Iteration`

### Create a temporary milestone if needed

```powershell
gh api repos/SMIT-Club/agentic-workflows/milestones `
  -X POST `
  -f title="Smoke Test Milestone" `
  -f description="Temporary milestone for project property validation."
```

### Create the test issue

```powershell
gh issue create --repo SMIT-Club/agentic-workflows `
  --title "Project property sync smoke test" `
  --body "Created by GitHub CLI to validate issue-backed Project field updates." `
  --assignee "@me" `
  --label enhancement `
  --label question `
  --milestone "Smoke Test Milestone"
```

### Add the issue to the project

```powershell
gh project item-add 2 --owner SMIT-Club --url https://github.com/SMIT-Club/agentic-workflows/issues/<number>
```

### Set the repository issue Type

First query available issue types:

```powershell
gh api graphql -f query='
query {
  repository(owner: "SMIT-Club", name: "agentic-workflows") {
    issueTypes(first: 20) {
      nodes {
        id
        name
        isEnabled
      }
    }
  }
}'
```

Then update the issue type with GraphQL:

```powershell
gh api graphql -f query='
mutation($id: ID!, $issueTypeId: ID!) {
  updateIssue(input: {id: $id, issueTypeId: $issueTypeId}) {
    issue {
      number
      issueType { name }
    }
  }
}' -F id=<issue-node-id> -F issueTypeId=<issue-type-id>
```

### Set project-specific fields

Run one edit per field:

```powershell
gh project item-edit --id <item-id> --project-id <project-id> --field-id <status-field-id> --single-select-option-id <backlog-option-id>
gh project item-edit --id <item-id> --project-id <project-id> --field-id <priority-field-id> --single-select-option-id <priority-option-id>
gh project item-edit --id <item-id> --project-id <project-id> --field-id <size-field-id> --single-select-option-id <size-option-id>
gh project item-edit --id <item-id> --project-id <project-id> --field-id <estimate-field-id> --number 3
gh project item-edit --id <item-id> --project-id <project-id> --field-id <iteration-field-id> --iteration-id <iteration-id>
```

### Validate the final state

Check the issue-backed properties:

```powershell
gh issue view <number> --repo SMIT-Club/agentic-workflows --json number,title,issueType,assignees,labels,milestone,projectItems,url
```

Check the project item field values:

```powershell
gh api graphql -f query='
query {
  organization(login: "SMIT-Club") {
    projectV2(number: 2) {
      items(first: 100) {
        nodes {
          id
          content {
            __typename
            ... on Issue {
              number
              title
            }
          }
          fieldValues(first: 20) {
            nodes {
              ... on ProjectV2ItemFieldSingleSelectValue {
                field { ... on ProjectV2FieldCommon { name } }
                name
              }
              ... on ProjectV2ItemFieldNumberValue {
                field { ... on ProjectV2FieldCommon { name } }
                number
              }
              ... on ProjectV2ItemFieldIterationValue {
                field { ... on ProjectV2FieldCommon { name } }
                title
              }
            }
          }
        }
      }
    }
  }
}'
```

## Common cleanup workflows

### Remove the test items from the project only

Use this when you want to keep the repository issues but remove their project cards:

```powershell
gh api graphql -f query='
mutation($project: ID!, $item: ID!) {
  deleteProjectV2Item(input: {projectId: $project, itemId: $item}) {
    deletedItemId
  }
}' -F project=<project-id> -F item=<item-id>
```

### Remove the test issues completely

Use this when you want to delete the repository artifacts too:

```powershell
gh issue delete <number> --repo SMIT-Club/agentic-workflows --yes
```

If you created a temporary milestone, remove it too:

```powershell
gh api repos/SMIT-Club/agentic-workflows/milestones/<milestone-number> -X DELETE
```

## Operating notes

- `read:project` is not enough for edits; `project` scope is required.
- Draft items and issue-backed items are different workflows.
- `Type` is a repository issue property, not a project custom field.
- `Status`, `Priority`, `Size`, `Estimate`, and `Iteration` are project fields.
- `Assignees`, `Labels`, `Milestone`, and `Repository` can appear in the project as mirrored issue-backed properties.
- When troubleshooting, avoid re-running creation commands until you have confirmed whether the first item or issue already exists.
