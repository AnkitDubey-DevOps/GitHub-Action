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
