## Q1) Which variable would you set to true in order to enable step debug logging?
Ans : ACTIONS_STEP_DEBUG : Shows detailed logs for each workflow step.
      Concepts : ACTIONS_RUNNER_DEBUG : Shows detailed logs from the runner machine itself.

## Q2) Tom has built a workflow that sends requests to a service that is currently unavailable.  What is an appropriate action for Tom to take so that his workflow doesn't log errors until the service is restored?
Ans : Disable the workflow until service has been restored

## Q3) How many required inputs are declared in the metadata of this actions example?
```
inputs:
  num-servers:
    description: 'Number of Servers'
    required: false
    default: '3'
  server-cpu-count:
    description: 'CPU count of the Servers'
    required: true
 ```
Ans : 1 : only one input is required : true

## Q4) Dan would like Drew's input on a particular line in the logs of a recently run workflow.  What is an efficient way to provide Drew access to the line in the logs?
Ans: Click on the step's line number to get a link to the specific line and share the link with Drew.
Tips: Need to share one log line? → Click the line number → Copy link → Share

## Q5) Which key in a workflow file is used to set a custom environment variable for a single workflow?
Ans : env : Stores custom environment variables that can be used in a workflow, job, or step.
Other Concept:
job : A group of steps that run together on the same runner.
variable : A named value used to store and reuse data in workflows.
steps : Individual tasks or commands executed inside a job.

## Q6) What will occur if the .github/workflows directory contains an invalid workflow file?
Ans: GitHub Actions generates a failed workflow run for every new commit

## Q7) Phil would like to filter all workflow runs triggered by a pull request.  Which filter can Phil use to achieve this in the GitHub Actions tab of his repository?
Ans : Event : Filters workflow runs by the trigger type (push, pull_request, workflow_dispatch, etc.).
Other Concept:
Branch : Filters runs from a specific branch.
Actor : Filters runs started by a specific user.
Status : Filters runs by result (success, failure, cancelled, etc.).

## Q8) How long does GitHub store logs and artifacts by default?
Ans: 90 days

## Q9) What are the benefits of using organization-templated workflows?  (select three)
Ans : Promote consistency across repositories, Reduce duplication and save time and Enforce organizational best practices and standards.

## Q10) Sam would like to trigger a workflow when a push is made to any branch in the repository, or somebody creates a tag. How can Sam specify these events within the GitHub workflow configuration?
Ans : on: [push, create]

## Q11) Which version of the actions/checkout action will be used for the following workflow configuration?
Ans: actions/checkout@v4 : Specific stable version 
actions/checkout@main : Latest code from main branch
- uses: actions/checkout : Invalid Syntax

## Q12) What does this ✅ badge indicate about a GitHub Action within the Marketplace?
Ans: verified creator badge

## Q13) What metadata keywords within an action.yml file is used to indicate the type of action being executed?
Ans : 
```
runs:
  using:
  ```
Use Cases: The "runs" keyword within an action.yml file is used to define the script or executable that will be run when the action is executed. The "using" keyword within the "runs" section is used to specify the type of action being executed, whether it is a JavaScript action, Docker container action, or composite run steps action.

Other Concept:

inputs: : The "inputs" keyword within an action.yml file is used to define the inputs that the action expects from the user.
name: : The "name" keyword within an action.yml file is used to specify the display name of the action.

## Q14) Dani wants to be notified when a comment is created on an issue within a GitHub repository. Which event should be used within the configuration?
Ans: issue_comment : This specifies that the workflow should be triggered when an issue comment event occurs.

## Q15) Which action can be used to download artifacts from a GitHub Actions workflow?
Ans: the actions/download-artifact action

## Q16) What level of access is required on a GitHub repository in order to delete log files from workflow runs?
Ans : Write

## Q17) Dave is creating a templated workflow for his organization.  Where must Dave store the workflow files and associated metadata files for the templated workflow?
Ans : inside a directory named workflow-templates within a repository named .github

## Q18) GitHub Actions will allow for deleting a workflow run under the following conditions (select two)
Ans : a workflow run that is more than two weeks old and a workflow run that has been completed

## Q19) The ACTIONS_STEP_DEBUG can be set to true to enable step debug logging.  How can this setting be configured?
Ans : as a secret or variable with the value of the secret taking precedence

## Q20) What can be viewed directly on the Actions tab in GitHub?  (select three)

Ans : the status of each workflow run, the branch for each workflow run and the length of time for each workflow run

## Q21) Steve wants to create a configuration variable for use across multiple workflows.  He has learned that he can define this variable at the organization, repository, or environment level.  Which value takes precedence if Steve configures a variable with the same name at each level?
Ans : environment-level (If a variable with the same name exists at multiple levels, the variable at the lowest level takes precedence.)

## Q22) Which of the following statements are true regarding GitHub default environment variables?
Ans: default environment variables are all uppercase, default environment variables are available to every step in a workflow and default environment variables are not accessible through the env context

## Q23) John has configured his workflow to save artifacts created from the build job. Where can John access the artifacts from the GitHub user interface that were saved within the build job?
Ans : from the Artifacts section within the Actions workflow run

## Q24) What status should you filter on to see only failed workflow runs on the GitHub Actions tab?
Ans : failure

## Q25) Which of the following events can trigger workflows? (select three)
Ans : when a discussion is created, when a commit is pushed to the repository and when a GitHub issue is created

## Q26) For an action that was triggered on: pull request, where can you see the workflow run status? (select three)
Ans: on the Checks tab of the pull request, from the Actions tab of the repository and in a pull request before a merge

## Q27) What additional steps does GitHub add to each job in a workflow run?
Ans: "Set up job" and "Complete job"

## Q28) Ryan is looking for the GitHub Actions workflow files for his repository. Where should he look?
Ans : the .github/workflows directory of the repository

## Q29) Which API does GitHub Actions use to output statuses, results, and logs for a workflow?
Ans: Checks API : The Checks API is the correct choice because GitHub Actions use this API to output statuses, results, and logs for a workflow. It allows workflows to create detailed status checks, annotations, and summaries for each job and step in the workflow, providing visibility into the execution and results of the workflow.

Other Concept:

Health API : The Health API in GitHub is used to check the health status of GitHub services and systems, providing information on the operational status of GitHub's infrastructure
Actions API : The Actions API in GitHub is used to interact with GitHub Actions workflows, such as triggering workflows, listing workflow runs, and getting workflow run details.
Logs API: It is more focused on accessing and managing log data generated during workflow execution.

## Q30) What is the filename of the metadata file that defines the inputs, outputs, and runs configuration for your action?
Ans : action.yaml

## Q31) After creating a new workflow, GitHub Actions will suggest starter workflows for your repository. What option should you click on if there is a starter workflow that you want to use?
Ans : Configure

## Q32) What level of access is required to download workflow artifacts?
Ans: read

## Q33) On a Github hosted runner, what is the recorded in the "Set up Job " Steps of given job?
Ans: Operating system, Runner and Github Token permission 

## Q34) Which keyword in GitHub Workflow configuration is used to match a triggering event?
Ans: on:

other concepts:
run: ( Used to define the action that should be executed as a part of specific job within workflow.)
when: ( Used to define the Condition under which job run within the workflow such as success, failure and always.)

## Q35) If an organization's templated workflow contains secret information such as `${{ secrets.token }}`, what needs to be configured before using the workflow?

Ans: Create a repository secret named `token`

## Q36) Which default environment variable contains the operating system of the runner executing the job?
Ans: 

```text
RUNNER_OS
```
`RUNNER_OS` tells you which operating system the GitHub Actions runner is using.

Possible values:

```text
Linux
Windows
macOS
```
**RUNNER_DEBUG** → Indicates whether runner debug logging is enabled
**RUNNER_ARCH** → Contains CPU architecture (X64, ARM64), not OS
