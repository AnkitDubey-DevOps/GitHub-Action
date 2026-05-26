## Q1) Syntax rules for defining indentation in YAML used for defining workflow job in GitHub Action.
Ans: YAML allows significant newline and indentation, Similiar ro python but unlike python, it prohibits the use of literal tab character for indentation.

## Q2) Why is it important to avoid passing secrets between processes from the command line?
Ans: passing secrets through the command line may expose them to other users and security audits.

## Q3) In the context of actions and workflows, what roles do steps play in the overall process?
Ans: they represent individual tasks within a job

## Q4) What is the primary purpose of custom labels in GitHub Actions for self-hosted runners?
Ans: routing jobs to specific types of self-hosted runners based on their labels

## Q5) What is required to manually run a private repository's workflow using the GitHub REST API?
Ans: Personal access token

## Q6) What happened if the job is not approved within 30 days while awaiting review in a workflow?
Ans: the job will automatically failed.

## Q7) What information is essential when drafting a new release and publishing an action to GitHub Marketplace?
Ans: The Action metadata file's category must watch an existing Github Marketplace category to ensure that action is listed in correct category.

## Q8) Why does GitHub recommend using variable to access the filesystem instead of hardcoded file paths?
Ans: Variable provides a dynamic way to adapt to different runner environment.

## Q9) GitHub Packages is compatible with following package manager.
Ans: Maven and Gradle two package manager for Java, NuGet the .NET package manager, npm a nodejs package manager.

## Q10) When might it be appropriate to use a combination of GitHub-hosted and self-hosted runners in a workflow?
Ans: when dealing with resource-intensive tasks
