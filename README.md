# EWM-agent

This is an EWM (Extended Warehouse Management) template-related GitHub Copilot Custom Agent. It acts as a SAP ABAP developer with expertise in HANA and EWM functionality, providing process knowledge, solution design documents, coding suggestions, and code reviews.

---

## Merging the Agent to the Default Branch

GitHub Copilot Custom Agents are **only active and discoverable when the agent definition file is present on the repository's default branch** (typically `main`). If the file exists only on a feature branch, the agent will not be available to any users. Follow the steps below to merge the agent to `main`.

---

### Why This Is Required

The GitHub Copilot platform scans the **default branch** of a repository to discover custom agent definitions stored in `.github/agents/`. Until the file `.github/agents/my-agent.agent.md` is merged into `main`, the EWM Pro agent will not appear in Copilot Chat for any user working in this repository.

---

### Step 1 – Confirm the Agent File Is on a Branch

Before opening a Pull Request, verify that the agent definition file exists on your feature branch:

1. On GitHub, navigate to this repository
2. Use the branch selector dropdown (top-left of the file list) to switch to the branch that contains the agent file (e.g., `feature/add-ewm-agent`)
3. Confirm that `.github/agents/my-agent.agent.md` is present

---

### Step 2 – Open a Pull Request

1. Go to the repository on GitHub
2. Click the **Pull requests** tab
3. Click **New pull request**
4. Set the **base** branch to `main` (the default branch)
5. Set the **compare** branch to the branch containing the agent file (e.g., `feature/add-ewm-agent`)
6. Click **Create pull request**
7. Add a clear title and description, for example:
   - **Title:** `Add EWM Pro Copilot agent configuration`
   - **Description:** `Adds the GitHub Copilot Custom Agent definition for EWM Pro to the default branch so it is available to all repository users.`
8. Click **Create pull request** to submit it

> **Tip:** If GitHub shows a banner saying *"This branch has recent pushes"*, you can click **Compare & pull request** directly to skip steps 2–5.

---

### Step 3 – Review and Merge the Pull Request

1. Request reviews from relevant team members if required by your repository's branch protection rules
2. Ensure all required status checks pass (CI workflows, if any)
3. Once approved, click **Merge pull request**
4. Choose a merge strategy:
   - **Create a merge commit** – preserves full history (recommended)
   - **Squash and merge** – combines all commits into one clean commit
   - **Rebase and merge** – replays commits on top of `main`
5. Click **Confirm merge**
6. Optionally click **Delete branch** to clean up the feature branch after merging

---

### Step 4 – Verify the Agent Is Active

After merging, confirm the agent is available:

1. Navigate to the repository on GitHub and switch to the `main` branch
2. Verify that `.github/agents/my-agent.agent.md` is present in the file tree
3. Open **GitHub Copilot Chat** (in the browser at [github.com](https://github.com) or in your IDE)
4. Type `@EWM-Pro` — the agent should appear as an autocomplete suggestion
5. Send a test message, for example: `@EWM-Pro What EWM processes do you support?`

---

### Troubleshooting Merge Issues

| Issue | Solution |
|---|---|
| **No "Merge pull request" button** | Branch protection rules may require approvals — ask a repository admin or a designated reviewer to approve the PR |
| **Merge conflicts** | Pull the latest `main` into your feature branch locally (`git fetch origin && git merge origin/main`), resolve conflicts, then push |
| **Agent still not appearing after merge** | Wait a few minutes for GitHub to re-index the repository; then refresh Copilot Chat |
| **Required status checks failing** | Fix any failing CI checks on the feature branch before merging |
| **No write access to `main`** | Ask a repository administrator to merge the PR or grant you the appropriate permissions |

---

## How to Use This Agent in Eclipse

The EWM agent is a **GitHub Copilot Custom Agent** available directly in your Eclipse IDE via the GitHub Copilot Chat panel. Follow the steps below to set it up and start using it.

---

### Prerequisites

Before using the EWM agent in Eclipse, make sure you have:

1. **Eclipse IDE** – Version 2023-09 (4.29) or later recommended  
   Download from: [https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)

2. **ABAP Development Tools (ADT)** – Eclipse plugin for SAP ABAP development  
   Install from the Eclipse Marketplace or via your SAP installation guide:  
   [https://tools.hana.ondemand.com/#abap](https://tools.hana.ondemand.com/#abap)

3. **GitHub Account** with an active **GitHub Copilot subscription** (Individual, Business, or Enterprise)  
   Sign up at: [https://github.com/features/copilot](https://github.com/features/copilot)

4. **GitHub Copilot Extension for Eclipse** – See installation steps below

---

### Step 1 – Install GitHub Copilot in Eclipse

1. Open Eclipse and go to **Help → Eclipse Marketplace**
2. In the search box, type **GitHub Copilot** and press **Enter**
3. Find **GitHub Copilot** in the results and click **Install**
4. Accept the license agreement and follow the prompts to complete the installation
5. Restart Eclipse when prompted

> **Alternative:** Install directly from the update site:  
> `https://marketplace.eclipse.org/content/github-copilot`

---

### Step 2 – Sign In to GitHub Copilot

1. After restarting Eclipse, go to **Window → Preferences → GitHub Copilot**
2. Click **Sign In** and follow the device-flow authentication:
   - A code will be displayed in Eclipse
   - Open [https://github.com/login/device](https://github.com/login/device) in your browser
   - Enter the code and authorize the Eclipse Copilot extension
3. Once authenticated, Copilot will show as **Connected** in Preferences

---

### Step 3 – Open the GitHub Copilot Chat Panel

1. In Eclipse, go to **Window → Show View → Other…**
2. Search for **Copilot Chat** or find it under the **GitHub** category
3. Click **Open** to display the Copilot Chat panel (usually docks at the bottom or side of your workspace)

---

### Step 4 – Use the EWM Agent in Copilot Chat

The EWM agent is available as a custom agent named **`@EWM-Pro`**. To invoke it, type `@EWM-Pro` at the start of your message in the Copilot Chat panel.

> **Note:** Custom agents are available when your repository contains the EWM agent definition file at `.github/agents/my-agent.agent.md` (this is the actual agent configuration file for the EWM Pro agent in this repository) and the agent is accessible from the repository context.

#### Example Prompts

| Task | Example Prompt |
|---|---|
| Code review | `@EWM-Pro Review my ABAP method for performance issues` |
| Coding suggestion | `@EWM-Pro Suggest an optimized way to read delivery items from LIPS` |
| Process knowledge | `@EWM-Pro Explain the EWM goods receipt process` |
| Solution design | `@EWM-Pro Create a solution design document for warehouse task creation` |
| ABAP best practices | `@EWM-Pro What are the best practices for SELECT statements in ABAP?` |

---

### Agent Capabilities

The EWM agent (**EWM Pro**) provides the following:

- 🔍 **Code Review** – Reviews your ABAP code against SAP EWM coding standards
- 💡 **Coding Suggestions** – Suggests performance-optimized ABAP code
- 📚 **EWM Process Knowledge** – Explains SAP EWM warehouse processes
- 📝 **Solution Design** – Generates solution design documents using the SD Template
- 🛡️ **Best Practice Enforcement** – Automatically checks for common ABAP anti-patterns

#### ABAP Coding Rules Enforced by the Agent

| Rule | Description |
|---|---|
| No `SELECT *` | Always specify required fields explicitly |
| No `SELECT` inside `LOOP` | Avoid database calls within loop iterations |
| No nested `LOOP` | Avoid loop-in-loop patterns |
| No nested `SELECT` | Avoid subquery-in-select patterns |
| No direct `SELECT` on Views | Use proper table access instead |
| `WHERE` clause required | All `SELECT` statements must have a `WHERE` clause (exception: `SELECT SINGLE` or `UP TO 1 ROWS`) |

---

### Tips for Working with the EWM Agent in Eclipse

- **Open your ABAP source file** in the Eclipse editor before asking for a code review — Copilot Chat can pick up the active editor context
- **Select a code block** and right-click to use **Copilot → Explain** or **Copilot → Fix** for quick inline suggestions
- **Provide context** in your prompts (e.g., table names, function module names, process steps) for more precise answers
- **Iterate** — if the first suggestion doesn't fit, ask the agent to refine it with additional constraints

---

### Troubleshooting

| Issue | Solution |
|---|---|
| Agent not found (`@EWM-Pro` not recognized) | Ensure you are working in the correct repository that contains `.github/agents/my-agent.agent.md` (the EWM Pro agent definition file) |
| Copilot Chat panel not visible | Go to **Window → Show View → Other → GitHub → Copilot Chat** |
| Authentication error | Go to **Window → Preferences → GitHub Copilot** and click **Sign Out**, then sign in again |
| Suggestions not appearing in editor | Ensure Copilot is enabled: **Window → Preferences → GitHub Copilot → Enable GitHub Copilot** |

---

### Additional Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [GitHub Copilot Custom Agents](https://gh.io/customagents/config)
- [ABAP Development Tools (ADT) Documentation](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide)
- [SAP EWM Documentation](https://help.sap.com/docs/SAP_EWMS)
