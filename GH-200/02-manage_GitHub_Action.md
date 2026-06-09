## Q1) Your team manages its own infrastructure costs using a chargeback model and wants to ensure that development workflows do not utilize the runners paid for by your team. Which GitHub Actions feature can help achieve this goal?
Ans: runner groups : Runner groups in GitHub Actions allow you to organize and group runners based on specific criteria, such as availability, capacity, or cost. By assigning workflows to specific runner groups, you can ensure that development workflows do not utilize the runners paid for by your team, thus helping to manage infrastructure costs effectively.

Other Concepts:
runner environments : Runner environments in GitHub Actions are used to define the operating system, software, and tools available on the runner where a workflow will run.
runner labels : Runner labels in GitHub Actions are used to tag and categorize runners based on specific attributes. 

## Q2) Your organization uses GitHub Actions in Enterprise Cloud and wants to ensure automation is reused and maintained when creating new workflows in the organization's repositories. What feature should be used?
Ans : workflow templates : Workflow templates in GitHub Actions allow organizations to create standardized, reusable automation workflows that can be easily applied to multiple repositories.

Other Concepts:

GitHub wiki : GitHub wiki is a documentation feature that allows users to create and maintain project documentation.
naming conventions : Naming conventions are essential for maintaining consistency and clarity in project structures, file naming, and other aspects of development.

## Q3) Your organization uses a self-hosted runner deployed within a network that requires a proxy server for internet access. Which environment variable should you configure on the runner to ensure it can successfully communicate with GitHub?
Ans: https_proxy (The `https_proxy` environment variable should be configured on the self-hosted runner to specify the proxy server that should be used for HTTPS requests. This ensures that the runner can successfully communicate with GitHub over HTTPS through the proxy server.)

## Q4) How can encrypted secrets be accessed within actions and workflows for GitHub Actions?
Ans : using the secrets context within GitHub Actions, which allows encrypted secrets to be accessed as environment variables

## Q5) You want to limit the use of public actions and reusable workflows so that people can only use reusable workflows in your enterprise. Where would this be configured?
Ans : In the Policies section for the targeted enterprise for your organization

## Q6) Your organization requires IP allowlists to protect internal resources accessed by GitHub Actions workflows. Most of your workflows run on GitHub-hosted runners, with both Windows and macOS needs. How can you achieve this desired security while ensuring workflow reliability?
Ans : utilize large runners with static IP address ranges and add these ranges to the allowlist

## Q7) A new self-hosted runner was recently registered with your organization, but you don't see it in the runner group assigned to your team. Why can't you use the new runner?
Ans : new runners are automatically assigned to a default group, therefore it needs to be moved to the group used by your team

## Q8) April is in charge of auditing the operations team. While conducting a review, she noticed that many workflows are accessing secrets to carry out deployment and testing functions and is concerned that these secrets may appear in logs. What information can you provide to alleviate April's concerns about workflow logs?
Ans: GitHub automatically redacts secrets printed to workflow logs, replacing them with placeholders. This feature ensures that sensitive information such as secrets are not exposed in plain text within the logs, mitigating the risk of unauthorized access to confidential data.

## Q9) Your organization uses self-hosted runners for GitHub Actions and wants to implement security best practices. How can you control access to specific runners for different repositories across teams?
Ans: assign runners to groups and grant repository access permissions at the group level

## Q10) You need to monitor the status of the self-hosted runners that have been deployed in your organization. After logging into the GitHub UI, what valid status types can you expect to see? (select three)
Ans :offline, Active and Idle

## Q11) Your organization requires a runner to execute multiple GitHub Actions workflows that include CPU-intensive tasks and high-memory processes that access sensitive internal resources. Which runner type best aligns with these requirements?
Ans : self-hosted runner with dedicated hardware

## Q12) Your development team is troubleshooting connectivity issues with a self-hosted runner. What parameter can be used to validate that a self-hosted runner can access all required network services on GitHub?
Ans : --check

Other Concepts:
--diag : It is more commonly used for diagnostic purposes to identify and troubleshoot issues within the GitHub Actions environment.

## Q13) You're assisting a colleague who wants to understand the differences between GitHub-hosted runners and self-hosted runners. They must choose the best option for running their team's GitHub Actions workflows. What key points would you include in your explanation to differentiate these two runner types effectively? (select three)
Ans : Self-host runners often run on a persistent environment and can, if desired, retain custom configurations, software, and caching between jobs.
Self-hosted runners enable access to resources within your private network, unlike GitHub-hosted runners
Github-hosted runners use an ephemeral environment, which means each job typically runs on a fresh virtual machine, which means you start with a clean slate every time.

## Q14) As an enterprise owner, you want to restrict the use of GitHub Actions within your organization but still allow access to essential workflows. Which of the following configurations would achieve this goal?

Ans : enforce a policy to allow only local actions and reusable workflows

## Q15) What network requirement is necessary for self-hosted runners in GitHub Actions for connectivity to GitHub?
Ans : permitting outbound connectivity to GitHub hosts using long polling



# Concepts for the Manage GitHub Action workflow for enterprises


** Enterprise = org-level policies, runner groups, and governance.

## Runners
### GitHub-Hosted Runner
Virtual machine provided by GitHub; choose OS (`ubuntu-latest`, `windows-latest`, `macos-latest`), no setup needed, deleted after each job.

### Self-Hosted Runner
Your own machine connected to GitHub; used for custom software, private networks, special hardware, or cost control.

### Runner Group
An org/enterprise-level way to organize self-hosted runners. You assign runners to groups and control which repos can use which group. Prevents untrusted repos from accessing sensitive runners.

### Toolcache
Pre-installed tools on GitHub-hosted runners (Node.js, Python, Java, etc.) to speed up workflow execution.

## Secrets & Variables

### Secret
Encrypted value used for sensitive data (tokens, passwords); hidden in logs and accessed with `${{ secrets.NAME }}`.

### Variable (Non-Secret)
Plain-text configuration value for non-sensitive data; visible in logs and accessed with `${{ vars.NAME }}`.

### Environment Secret
A secret tied to a specific environment (e.g., Production); available only when a job uses that environment.

### Secret Scoping
Determines where a secret is defined and which value is used when the same secret exists at multiple levels.

## Environments & Policies

### Deployment Environment
A protected deployment target (e.g., Production) that can require approvals before deployment.

#### Example
```yaml
environment: production
```

A manager must approve before the deployment starts.

### GITHUB_TOKEN Permissions
Controls what the workflow token can do (read code, create PRs, etc.).

#### Example
```yaml
permissions:
  contents: read
```

The workflow can only read repository contents.

### Action Allow/Deny Policy
Controls which GitHub Actions repositories are allowed to be used in workflows.

### Workflow Permissions Policy
Forces workflows to explicitly declare required permissions.

#### Example
```yaml
permissions:
  contents: read
  issues: write
```

Without declaring permissions, the workflow may be blocked.

## REST API & Governance

### Workflow API
GitHub REST API used to manage workflows programmatically.

### Secrets API
Used to create, update, or delete secrets through automation.

### Audit Log
Records security-related activities performed by users and admins.

### GITHUB_TOKEN

An automatic token created for every workflow run to access the current repository.

#### Example

```yaml
run: gh issue list
env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Used for:
- Creating issues
- Creating PRs
- Accessing repository data

⚠️ Expires when the workflow finishes.

### Least Privilege Principle
Give workflows only the minimum permissions they need.

#### Good Example

```yaml
permissions:
  contents: read
```

Workflow only reads code.

### OIDC Federation
Allows GitHub Actions to access AWS, Azure, or GCP without storing cloud credentials as secrets.

#### Example

Workflow gets a temporary token from GitHub and exchanges it for AWS access.

```yaml
permissions:
  id-token: write
```

No AWS access key stored in GitHub.

### id-token Permission
Required permission for a workflow to request an OIDC token from GitHub.

#### Example

```yaml
permissions:
  id-token: write
  contents: read
```

Without `id-token: write`, OIDC authentication won't work.

### Why OIDC is Better than Secrets
OIDC uses short-lived tokens instead of long-lived cloud credentials.

#### Example

❌ Traditional Secret

```text
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
```

Valid until manually rotated.

✅ OIDC

```text
Temporary token
```

Expires automatically after a few minutes.

## Preventing Secret Leakage

### Script Injection
A security risk where untrusted input is executed as shell commands inside a `run:` step.

#### Unsafe Example

```yaml
run: echo ${{ github.event.issue.title }}
```

If the issue title contains malicious commands, they may execute.

### Safe Pattern
Store user input in an environment variable first, then use the variable.

#### Safe Example

```yaml
env:
  TITLE: ${{ github.event.issue.title }}

run: echo "$TITLE"
```

GitHub treats it as data instead of code.

## Artifact Attestations

### Artifact Attestation
A signed proof that shows exactly which workflow, code, and build created an artifact.

#### Example

```yaml
uses: actions/attest-build-provenance@v1
```

Verifies:
- Who built it
- When it was built
- Which commit/workflow created it

### Supply Chain Security
Protects software from tampering by verifying that artifacts come from trusted builds.

#### Example

Without Attestation:

```text
app.zip
```

No proof of origin.

With Attestation:

```text
app.zip + signed provenance
```

Users can verify it was built by your GitHub workflow.

## Performance Optimization

### Caching Strategy
Stores dependencies between workflow runs to avoid downloading them again.

### Concurrency Control
Prevents multiple runs of the same workflow from running simultaneously.

#### Example

```yaml
concurrency:
  group: ${{ github.ref }}
  cancel-in-progress: true
```

When a new commit is pushed, the old run is canceled.

### max-parallel
Limits how many matrix jobs can run at the same time.

#### Example

```yaml
strategy:
  matrix:
    os: [ubuntu, windows, macos]
  max-parallel: 2
```

Only 2 matrix jobs run simultaneously.
