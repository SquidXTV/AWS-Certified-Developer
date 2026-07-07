## [AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html)

AWS Step Functions is a serverless orchestration service that lets you define workflows as state machines,
coordinating multiple AWS services visually using JSON-based state definitions. It handles sequencing, branching,
retries, error handling, and human approval steps.

### [Step Functions Task States](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-statemachines.html)

Task states represent units of work that invoke an activity or an AWS service and then pass their result to the next
state.

### [Step Functions Flow States](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-statemachines.html)

Flow states are used to control the execution flow of a state machine, such as **Choice states** for conditional logic,
**Wait states** for pausing the workflow execution, **Map states** to run child workflows for each item in a dataset, and
**Parallel states** to create separate branches.

### [Step Functions Error Handling](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-error-handling.html)

Error handling is configured per state using **Retry** and **Catch** blocks, where you define which errors to match, backoff
strategy, and fallback states.

### [Step Functions Task Token](https://docs.aws.amazon.com/step-functions/latest/dg/connect-to-resource.html#connect-wait-token)

Task Token callbacks let an external service or process resume a waiting state machine execution by calling back with a unique task
token. States that use the callback pattern pause until `SendTaskSuccess` or `SendTaskFailure` is invoked with that token, enabling
asynchronous or human-in-the-loop workflows.

### [Step Functions Activity Task](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-activities.html)

Activity Tasks represent work that is pulled and executed by external workers. Workers poll for activity tasks, perform the
work and then report completion or failure back.

### [Step Functions Workflow Type](https://docs.aws.amazon.com/step-functions/latest/dg/choosing-workflow-type.html)

Step Functions supports both **Standard** and **Express** workflows. Standard workflows are ideal for long-running,
durable, exactly-once executions with detailed history, while Express workflows are optimized for high-volume, short-lived
workflows with at-least-once execution for asynchronous and at-most-once execution for synchronous Express workflows.
