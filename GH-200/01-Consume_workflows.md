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

## Q23)
