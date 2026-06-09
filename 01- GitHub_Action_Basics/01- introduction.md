# GH-200 GitHub Actions Quick Notes

## 1. Workflow

A **workflow** is the complete automation process.

Example:

- Build application
- Run tests
- Deploy application

Stored in:

```text
.github/workflows/build.yml
```

Think: **Workflow = Entire pipeline**

---

## 2. Trigger

A trigger decides **when a workflow starts**.

### push

Runs when code is pushed.

```yaml
on:
  push:
```

---

### pull_request

Runs when a Pull Request is created or updated.

```yaml
on:
  pull_request:
```

---

### workflow_dispatch

Manual execution.

```yaml
on:
  workflow_dispatch:
```

Think: "Run Workflow" button.

---

### schedule

Runs on a schedule.

```yaml
on:
  schedule:
```

Think: Cron job.

---

### workflow_call

Allows one workflow to call another workflow.

Think: Reusable workflow.

---

## 3. Job

A workflow contains one or more jobs.

```text
Workflow
 ├── Build Job
 ├── Test Job
 └── Deploy Job
```

```yaml
jobs:
  build:
```

Think: **Job = Major phase of workflow**

---

## 4. Step

A job contains multiple steps.

```text
Build Job
 ├── Checkout Code
 ├── Install Dependencies
 └── Build Application
```

```yaml
steps:
```

Think: **Step = Single task**

---

## 5. Runner

A runner is the machine that executes the workflow.

```text
Workflow
    ↓
Runner
    ↓
Commands Execute
```

Think: **Runner = Machine**

---

## 6. GitHub-hosted Runner

GitHub provides the machine.

```yaml
runs-on: ubuntu-latest
```

Features:

- Automatically created
- Automatically deleted
- No maintenance required

Think: **Managed by GitHub**

---

## 7. Self-hosted Runner

You provide and manage the machine.

Examples:

- VM
- Physical Server
- Laptop

Benefits:

- Full control
- Access internal network

Think: **Managed by You**

---

## 8. Action

An action is reusable code.

Example:

```yaml
uses: actions/checkout@v4
```

Think: **Action = Reusable automation**

---

## 9. actions/checkout

Downloads repository code onto runner.

```yaml
uses: actions/checkout@v4
```

Without checkout:

- Source code is not available

Think: **Checkout = Download code**

---

## 10. needs

Creates dependency between jobs.

```yaml
test:
  needs: build
```

Meaning:

- Build runs first
- Test runs after Build succeeds

Think: **needs = Run after**

---

## 11. if Condition

Controls execution.

```yaml
if: github.ref == 'refs/heads/main'
```

Meaning:

- Run only on main branch

Think: **if = Conditional execution**

---

## 12. Context

GitHub-provided information available during workflow execution.

### github Context

```yaml
github.actor
github.repository
github.ref
```

Examples:

- User who triggered workflow
- Repository name
- Branch name

---

### runner Context

```yaml
runner.os
```

Returns:

```text
Linux
Windows
macOS
```

---

### env Context

```yaml
env.APP_NAME
```

Access environment variables.

---

### secrets Context

```yaml
secrets.API_KEY
```

Access secrets.

---

## 13. Environment Variable

Stores non-sensitive values.

```yaml
env:
  APP_NAME: MyApp
```

Examples:

- Application name
- Environment name
- Version number

Think: **Variable = Normal data**

---

## 14. Secret

Stores sensitive information.

Examples:

- Passwords
- Tokens
- API Keys

Usage:

```yaml
${{ secrets.DB_PASSWORD }}
```

Think: **Secret = Sensitive data**

---

## 15. GITHUB_TOKEN

Automatically generated authentication token.

Usage:

```yaml
${{ secrets.GITHUB_TOKEN }}
```

Uses:

- Access repository
- Create releases
- Update pull requests

Think: **Built-in authentication**

---

## 16. Artifact

Stores files after workflow execution.

Example:

```text
Build Application
      ↓
app.zip
      ↓
Store as Artifact
```

Uses:

- Build outputs
- Test reports
- Log files

Think: **Artifact = Saved output files**

---

## 17. Cache

Stores dependencies for future runs.

Without cache:

```text
npm install
3 minutes
```

With cache:

```text
npm install
15 seconds
```

Uses:

- npm packages
- Maven dependencies
- Gradle dependencies

Think: **Cache = Saved dependencies**

---

## Artifact vs Cache

| Artifact | Cache |
|-----------|--------|
| Stores outputs | Stores dependencies |
| Download later | Speeds future runs |
| app.zip | node_modules |

---

## 18. Matrix Strategy

Runs same job with multiple configurations.

Example:

```yaml
matrix:
  node-version: [18, 20, 22]
```

Creates:

```text
Job 1 → Node 18
Job 2 → Node 20
Job 3 → Node 22
```

Think: **Matrix = Parallel variations**

---

## 19. Reusable Workflow

Allows reuse of an entire workflow.

Called using:

```yaml
workflow_call
```

Think:

```text
Reuse Jobs
Reuse Workflow Logic
```

---

## 20. Composite Action

Allows reuse of multiple steps.

Example:

```text
Install Java
Build App
Run Tests
```

Bundle into one action.

Think:

```text
Reuse Steps
```

---

## Reusable Workflow vs Composite Action

| Reusable Workflow | Composite Action |
|-------------------|------------------|
| Reuse jobs | Reuse steps |
| Uses workflow_call | Uses action.yml |
| Full workflow reuse | Step reuse |

---

## 21. Docker Action

Action packaged inside a Docker container.

Benefits:

- Consistent environment
- Dependency isolation

Think:

```text
Action runs inside container
```

---

## 22. JavaScript Action

Action written in JavaScript.

Example:

```text
index.js
```

Runs directly on runner.

Think:

```text
Action written in JavaScript
```

---

## 23. OIDC (OpenID Connect)

Secure cloud authentication without storing passwords.

Old Method:

```text
Store AWS password in GitHub Secret
```

OIDC Method:

```text
GitHub proves identity
Cloud trusts GitHub
Temporary credentials issued
```

Benefits:

- No stored credentials
- Better security

Think:

```text
Login without storing secrets
```

---

## 24. Environment Protection

Protects environments like Production.

Example:

```text
Deploy to Production
      ↓
Approval Required
      ↓
Deployment Continues
```

Uses:

- Manual approval
- Protected deployments

Think:

```text
Approval before deployment
```

---

## 25. Concurrency

Prevents duplicate workflow executions.

Without concurrency:

```text
5 Commits
↓
5 Deployments
```

With concurrency:

```text
5 Commits
↓
Cancel old runs
↓
Keep latest run
```

Think:

```text
Only latest run matters
```

---
