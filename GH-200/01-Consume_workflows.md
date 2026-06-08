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
Ans
