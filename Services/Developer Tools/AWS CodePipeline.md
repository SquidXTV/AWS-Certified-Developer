# [AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)

CodePipeline is a continuous delivery service that automates the building, testing, and deployment of your software into production.
It integrates with CodeCommit, CodeBuild, and CodeDeploy.

## [CodePipeline Stages](https://docs.aws.amazon.com/codepipeline/latest/userguide/concepts.html#concepts-pipelines)

A stage is a logical unit you can use to isolate an environment and to limit the number of concurrent changes in that environment.
Each stage contains actions that are performed on the application artifacts.


## [CodePipeline Actions](https://docs.aws.amazon.com/codepipeline/latest/userguide/concepts.html#concepts-pipelines)

An action is a set of operations performed on application code and configured so that the actions run in the pipeline at a specified point.
This can include things like a source action from a code change, an action for deploying the application to instances, and so on


## [CodePipeline Artifacts](https://docs.aws.amazon.com/codepipeline/latest/userguide/concepts.html#concepts-artifacts)

Artifacts refers to the collection of data, such as application source code, built applications, dependencies, definitions files,
templates, and so on, that is worked on by pipeline actions. Artifacts are produced by some actions and consumed by others.
