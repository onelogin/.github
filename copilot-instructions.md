# GitHub Copilot Instructions — OneLogin Org

These instructions apply to all repositories in the `onelogin` GitHub organization and provide context for AI-assisted development.

---

## Source Control

- All OneLogin source code repos are in **github.com/onelogin**
- Azure DevOps is used **only for work item tracking** (tickets) — not for source control

---

## Azure DevOps (ADO)

- **Organization URL:** https://dev.azure.com/1id/OID
- **Project:** OID
- **Area Path:** All OneLogin engineering tickets live under `OID\Engineering\OneLogin\*`

---

## ADO Work Item Types

### Bug
Used to track defects, regressions, and unintended behavior.

**Key fields:**
- **Title:** `[JIRA-KEY]` prefix if migrated from Jira, otherwise plain descriptive title
- **Description:** Describe actual vs expected behavior. Include tenant/account IDs, affected users, Datadog/log links where relevant
- **Repro Steps:** Step-by-step reproduction instructions
- **Acceptance Criteria:** What must be true for the bug to be considered fixed
- **Severity:** 1 (Critical) → 4 (Low)
- **Priority:** 1 (Highest) → 4 (Lowest)
- **Custom.FixedVersion:** Release version the fix ships in (e.g. `2026.02-core`, `2026.1.0`)
- **Custom.Components:** Affected service(s) and version (e.g. `core-api:4.49.2`)
- **Custom.SupportCaseId:** SF case number if customer-reported
- **Custom.CustomerReportedIncident:** `true` if originated from a customer support case
- **Tags:** Use `OL: <version>` for the release tag, plus any relevant labels (e.g. `OL: CRI`, `OL: Airbus`)

---

### User Story
Used to capture new features, improvements, and non-bug engineering work.

**Key fields:**
- **Title:** `[JIRA-KEY]` prefix if migrated, otherwise plain title
- **Description:** User story format preferred — *"As a [persona], I want [goal] so that [reason]"* — plus technical details, designs, or specs
- **Acceptance Criteria:** Measurable conditions that define "done"
- **Priority / Story Points:** Set by the team during refinement
- **Iteration Path:** Set to the sprint or quarter the work is planned for (e.g. `OID\2026\2026-Q1`)
- **Area Path:** `OID\Engineering\OneLogin\<Team>` (e.g. `OID\Engineering\OneLogin\Directory`)

---

### Task
Used for technical sub-tasks, investigation spikes, TechOps work, and operational items that don't fit Bug or User Story.

**Key fields:**
- **Title:** Prefix with `[TECHOPS]` for operational/infrastructure work
- **Description:** Clear scope of work, background context, and acceptance criteria
- **Area Path:** `OID\Engineering\OneLogin\<Team>`
- **Tags:** Use relevant labels like `security`, `WAF`, `offboarding`, etc.

---

### Epic
Used to group related User Stories and Bugs under a larger initiative or theme.

**Key fields:**
- **Title:** High-level initiative name
- **Description:** Goals, scope, and success metrics for the epic
- **Child items:** Link related User Stories and Bugs as children

---

### System Change (CAB)
Used **exclusively** for Change Advisory Board (CAB) entries. Represents a production change request that requires CAB review and approval before deployment.

**Key fields:**
- **Title:** Brief description of the change (e.g. `Deploying 2026.1.0 release to Prod`)
- **Description:** What is changing, which services/versions, deployment plan, rollback plan
- **Area Path:** Typically `OID\Engineering\OneLogin\CAB`
- **Risk:** Assess impact and risk level
- **Linked items:** Link to related Bugs/User Stories that are part of the release

> ⚠️ Only use the **System Change** work item type for CAB tickets. Do not use it for bugs, features, or tasks.

---

## Linking Work Items to Code

- When creating PRs that fix ADO tickets, include the ADO ticket ID in the PR title (e.g. `ADO-645196: Fix Ultipro overwriting Authenticated By`)
- Link PRs to ADO tickets using the artifact link feature in ADO or the `AB#<id>` syntax in PR descriptions
- Use **Related** links to connect tickets that are causally related (e.g. a regression bug linked to the fix that caused it)

---

## Release Versioning

- Releases follow the pattern `YYYY.N.0` (e.g. `2026.1.0`, `2026.2.0`)
- Internal release branch names follow `YYYY.NN-core` (e.g. `2026.02-core`)
- The `Custom.FixedVersion` field on bugs should reflect the release the fix ships in
