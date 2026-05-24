# GitHub Actions Syntax

To create a GitHub Action, it’s important to understand the GitHub Actions syntax. In this section, you’ll learn some of the most common syntax used to create workflows.

We’ll work with the following example workflow and break it down step by step.

---

## Example GitHub Action Workflow

```yaml
# .github/workflows/demo.yml

name: Github Action Template

on:

  pull_request:
    branches: [ "main" ]

  schedule:
    - cron: '30 5,17 * * *'

  workflow_call:
    inputs:
      username:
        description: 'A username passed from the caller workflow'
        default: 'john-doe'
        required: false
        type: string

permissions:
  actions: read|write|none

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:

  # This workflow contains a single job called "build"
  build:

    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

      # Checks out your repository under $GITHUB_WORKSPACE
      - uses: actions/checkout@v4

        if: ${{ github.event_name == 'pull_request' && github.event.action == 'unassigned' }}

        shell: zsh

        name: NPM Install Package

        run: npm install

        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          first_name: Github
          last_name: Action
          args: The ${{ github.event_name }} event triggered this step.
          entrypoint: /bin/echo
```

---

# Understanding GitHub Actions Syntax

Now let’s understand each option used in the workflow above.

---

## `name`

The `name` field defines the name of the workflow.

```yaml
name: Github Action Template
```

This name appears in the GitHub Actions UI.

---

## `on`

The `on` keyword defines the events that trigger the workflow.

### Example

```yaml
on:
  pull_request:
    branches: ["main"]
```

This workflow runs whenever a pull request is created for the `main` branch.

---

# Event Types

## `pull_request`

The `pull_request` event is triggered whenever someone creates or updates a pull request in the repository.

---

## `schedule`

The `schedule` event allows workflows to run automatically at specified times using cron syntax.

### Example

```yaml
schedule:
  - cron: '30 5,17 * * *'
```

This workflow runs at:

- 5:30 UTC
- 17:30 UTC

every day.

You can schedule workflows:

- Every few minutes
- Daily
- Weekly
- Monthly

---

## `workflow_call`

The `workflow_call` keyword is used to create reusable workflows.

### Example

```yaml
workflow_call:
  inputs:
    username:
      description: 'A username passed from the caller workflow'
      default: 'john-doe'
      required: false
      type: string
```

This defines an input variable named `username` that can be passed from another workflow.

---

## `permissions`

Some GitHub Actions require specific permissions to interact with:

- GitHub APIs
- Issues
- Pull requests
- Repository contents

### Example

```yaml
permissions:
  actions: read|write|none
```

For example:

- `write` permission allows creating comments or modifying resources.
- `read` permission only allows viewing data.

---

# Jobs

The `jobs` section defines one or more jobs in the workflow.

Each job contains:

- A runner
- Steps
- Commands or actions

### Example

```yaml
jobs:
```

---

## `runs-on`

The `runs-on` option defines the operating system or machine where the job executes.

### Example

```yaml
runs-on: ubuntu-latest
```

This runs the workflow on the latest Ubuntu virtual machine provided by GitHub.

---

# Steps

The `steps` section contains a sequence of tasks executed inside the job.

Steps can:

- Run commands
- Execute scripts
- Use external GitHub Actions

### Example

```yaml
steps:
```

---

## `uses`

The `uses` keyword allows you to use reusable GitHub Actions.

### Example

```yaml
uses: actions/checkout@v4
```

This action checks out your repository code into the runner environment.

Developers commonly publish reusable actions in the GitHub Marketplace.

These actions are usually built using:

- JavaScript
- Docker containers

---

## `if`

The `if` condition works similarly to a programming conditional statement.

It prevents a step from running unless the condition is true.

### Example

```yaml
if: ${{ github.event_name == 'pull_request' && github.event.action == 'unassigned' }}
```

This step only runs when:

- The event is a pull request
- The action is `unassigned`

---

## `shell`

The `shell` option allows you to define a custom shell.

### Example

```yaml
shell: zsh
```

You can use shells like:

- bash
- sh
- zsh
- powershell

---

## `run`

The `run` keyword executes commands in the operating system shell.

### Example

```yaml
run: npm install
```

Other examples:

```yaml
run: ls
run: pwd
```

---

## `with`

The `with` keyword passes input parameters to an action.

### Example

```yaml
with:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  first_name: Github
  last_name: Action
```

The `with` block commonly contains:

- Environment variables
- Input arguments
- Configuration values

---

## `args`

The `args` option passes arguments to the container entrypoint.

### Example

```yaml
args: The ${{ github.event_name }} event triggered this step.
```

---

## `entrypoint`

The `entrypoint` defines the executable file for a Docker container.

### Example

```yaml
entrypoint: /bin/echo
```

---

# Summary

You’ll use these syntax elements frequently when building GitHub Actions workflows.

The most important components include:

- `name`
- `on`
- `jobs`
- `runs-on`
- `steps`
- `uses`
- `run`
- `if`
- `with`

Understanding these concepts makes it much easier to automate testing, deployment, and CI/CD workflows.

---
