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
