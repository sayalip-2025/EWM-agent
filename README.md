# EWM-agent

This repository hosts the **EWM Pro** custom GitHub Copilot agent — a SAP EWM / ABAP development assistant.

## About the EWM Pro Agent

**EWM Pro** is a custom GitHub Copilot agent configured in this repository. It acts as a peer SAP ABAP developer with expertise in:

- SAP Extended Warehouse Management (EWM) functionality and processes
- HANA-optimised ABAP development
- Solution Design documentation (using the "SD Template")
- Performance-oriented coding suggestions
- Code review with ABAP best-practice checks

### Code Review Rules

The agent enforces the following ABAP coding guidelines automatically:

| Rule | Description |
|------|-------------|
| No `SELECT *` | Always select only the columns you need |
| No `SELECT` inside `LOOP` | Avoid database calls within loops |
| No nested `LOOP` statements | Flatten loop logic where possible |
| No nested `SELECT` statements | Use JOINs or sub-queries instead |
| No direct `SELECT` on views | Select from base tables instead |
| `WHERE` clause required | All multi-row `SELECT` statements must have a `WHERE` clause (exceptions: `SELECT SINGLE` or `SELECT ... UP TO 1 ROWS`) |

## Using the Agent

The **EWM Pro** agent is available in GitHub Copilot Chat inside your IDE or on GitHub.com once this file is merged into the default branch.

To invoke the agent in Copilot Chat, use:

```
@my-agent <your question or task>
```

### Example prompts

```
@my-agent Review this ABAP class for EWM best practices.
@my-agent Create a Solution Design document for the goods receipt process.
@my-agent How does the EWM deconsolidation process work?
@my-agent Suggest a performant way to read warehouse orders in bulk.
```

## Agent Configuration

The agent is defined in [`.github/agents/my-agent.agent.md`](.github/agents/my-agent.agent.md).

To update the agent behaviour, edit that file and merge the changes into the `main` branch. GitHub Copilot picks up the latest configuration automatically once the file is on the default branch.

## References

- [GitHub Custom Copilot Agents documentation](https://gh.io/customagents/config)
- [Copilot CLI for local testing](https://gh.io/customagents/cli)
