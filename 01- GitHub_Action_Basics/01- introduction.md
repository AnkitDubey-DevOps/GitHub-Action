# Introduction to GitHub Actions

GitHub Actions are one of the most powerful and helpful features of GitHub. They allow developers to automate workflows directly from their repositories. With GitHub Actions, you can build, test, and deploy applications automatically whenever changes are pushed to your codebase.

In addition to automation, GitHub Actions can also help with:

- Performing code reviews and automated testing
- Managing branches and pull requests
- Triaging issues
- Running scheduled tasks
- Deploying applications to cloud platforms

## How GitHub Actions Work

In simple terms, a GitHub workflow creates an environment using a virtual machine (called a **runner**) to test, build, and deploy your code. The workflow follows instructions defined inside a GitHub Actions workflow file.

These workflow files are written in YAML format and stored inside the repository under:

```bash
.github/workflows/


# Key GitHub Actions Concepts

Before creating GitHub Actions workflows, it’s important to understand the core concepts that power GitHub Actions.

---

# Workflows

A **workflow** is a configurable automated process that runs one or more jobs. Workflows are defined using YAML files inside your repository and are triggered by events.

You can also trigger workflows:

- Manually
- On a schedule
- Through repository events

Workflow files are stored in the following directory:

```bash
.github/workflows/
```

A repository can contain multiple workflows, each handling different tasks such as:

- Building and testing pull requests
- Deploying applications to the cloud
- Running tests on every pull request
- Automating issue management

---

# Events

An **event** is a specific activity in a repository that triggers a workflow.

For example:

- Pushing code triggers the `push` event
- Creating an issue triggers the `issues` event
- Opening a pull request triggers the `pull_request` event

## Common GitHub Action Events

Some frequently used GitHub Action events include:

- `push`
- `pull_request`
- `release`
- `issues`
- `milestone`
- `label`

The most commonly used events are:

- `push`
- `release`
- `pull_request`

You can learn more about events in the official GitHub documentation.

---

## Example: Defining Events in a Workflow

```yaml
# .github/workflows/demo.yml

on:
  issues:
    types: [opened, edited, milestoned]

  pull_request:
    types:
      - opened
    branches:
      - 'releases/**'
```

## Why Specify Event Types?

It is considered a best practice to specify event activity types. If you don’t define them, GitHub Actions may run more frequently than necessary, consuming additional resources.

For example:

- Defining the `pull_request` event with `opened` ensures the workflow only runs when a pull request is created.
- Without specifying the type, the workflow could run on every pull request activity.

---

# Jobs

A workflow contains one or more **jobs**.

Each job:

- Runs in a runner environment
- Contains multiple steps
- Executes commands or actions

By default, GitHub Actions jobs run **in parallel** unless dependencies are specified.

---

## Example: Workflow Structure

```yaml
# .github/workflows/demo.yml

name: Demo Workflows

on:
  push:

jobs:
```

---

## Job Dependencies

You can make one job depend on another using the `needs` keyword.

If jobs have no dependencies, they run in parallel.

If a job depends on another job, it waits until the dependent job completes successfully.

---

## Example: Job Dependencies

```yaml
# .github/workflows/demo.yml

jobs:
  build:
    name: Build
    needs: [Development]
    steps:
      - name: Build and deploy on Cloud

  dev:
    name: Development
    steps:
      - name: Run the developer

  Test:
    needs: [build, dev]
    name: Testing
    steps:
      - name: Testing the application
```

In this example:

- `build` depends on `Development`
- `Test` depends on both `build` and `dev`

---

# Runners

**Runners** are servers that execute workflows when they are triggered.

Each runner can handle only one job at a time.

GitHub provides hosted runners for:

- Ubuntu Linux
- Windows
- macOS

---

## Example: Using a Runner

```yaml
# .github/workflows/demo.yml

name: Demo workflows

on:
  push:
    branches: ["main"]

jobs:
  build:
    runs-on: ubuntu-latest
```

Here:

```yaml
runs-on: ubuntu-latest
```

specifies that the workflow should run on the latest Ubuntu runner.

---

## Runner Syntax

You can define runners as:

### Single String

```yaml
runs-on: ubuntu-latest
```

### Array of Strings

```yaml
runs-on: [ubuntu-latest, windows-latest, macos-latest]
```

---

# How to Create a GitHub Action in Your Repository

You can create a GitHub Action in two main ways:

1. Using the GitHub UI
2. Using your local IDE

---

## Using the GitHub UI

Many developers use the GitHub interface to create workflows because it is simple and beginner-friendly.

### Advantages

- No need to manually create the `.github/workflows` directory
- GitHub automatically generates the required folder structure
- Easy setup for basic workflows

---

## Using a Local IDE

For more advanced or complex workflows, developers typically use an IDE locally.

### Advantages

- Better control over workflow files
- Easier debugging and version management
- Suitable for larger projects and custom automation

---

Now that you understand the key components of GitHub Actions, the next step is learning how to create workflows in practice.
