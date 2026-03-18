# EWM-agent

This repository contains a custom GitHub Copilot agent for SAP Extended Warehouse Management (EWM) development.

## What this agent does

The **EWM Agent** acts as a SAP ABAP developer with expertise in SAP HANA and SAP EWM functionality and processes. It:

- Provides EWM/ABAP process knowledge based on repository files
- Creates Solution Design documents using the "SD Template"
- Acts as a peer developer with performance-enhancing coding suggestions
- Performs ABAP code reviews and flags common anti-patterns

## Using the agent in GitHub Copilot (Eclipse IDE)

### Prerequisites
- GitHub Copilot subscription (Individual, Business, or Enterprise)
- [GitHub Copilot for Eclipse](https://marketplace.eclipse.org/content/github-copilot) plugin installed and signed in

### How to activate in Eclipse

1. Open Eclipse and ensure the **GitHub Copilot** plugin is installed (via *Help → Eclipse Marketplace → search "GitHub Copilot"*).
2. Sign in to GitHub Copilot via *Window → Preferences → GitHub Copilot*.
3. Open a project or file from this repository in Eclipse.
4. Open the **Copilot Chat** view (*Window → Show View → Other → GitHub Copilot → Copilot Chat*).
5. The agent's instructions from `.github/copilot-instructions.md` are automatically applied to all Copilot interactions within this workspace.
6. To use the coding agent for automated tasks, assign a GitHub Issue to **Copilot** on the repository's Issues page — the `my-agent` configuration in `.github/agents/` will be used automatically.

### Coding guidelines enforced by this agent

| Rule | Description |
|------|-------------|
| No `SELECT *` | Always specify required fields |
| No SELECT inside LOOP | Fetch all data before loops |
| No nested LOOP | Avoid LOOP inside LOOP |
| No nested SELECT | Use JOINs or `FOR ALL ENTRIES` |
| No direct SELECT on views | Use base tables |
| WHERE clause required | Every multi-row SELECT must have a WHERE condition |

## Repository structure

```
.github/
  agents/
    my-agent.agent.md        # Copilot coding agent definition
  copilot-instructions.md    # Workspace-level Copilot instructions (used by Eclipse plugin)
README.md
```
