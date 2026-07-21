# [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)

Amazon API Gateway is an AWS service for creating, publishing, maintaining, monitoring, and securing REST, HTTP,
and WebSocket APIs at any scale. API developers can create APIs that access AWS or other web services, as well as
data stored in the AWS Cloud.

## [API Gateway Endpoint Type](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html)

- **Edge-optimized:** requests are routed to the nearest CloudFront Edge Location and routed to the API Gateway
- **Regional:** requests are targeted directly to the region-specific API Gateway
- **Private:** requests can only be accessed from within a private VPC


## [API Gateway Deployment](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-deployments.html)

A Deployment is a snapshot of an API with its configuration at a specific point.


## [API Gateway Stages](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-stages.html)

A Stage is a named reference to a specific deployment.

### [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html)

Stage variables are key-value pairs that you can define as configuration attributes associated with a deployment stage of a REST API.
They act like environment variables and can be used in your API setup and mapping templates. With deployment stages in API Gateway,
you can manage multiple release stages for each API and use stage variables you can configure an API deployment stage to interact
with different backend endpoints.



## [API Gateway Caching](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-caching.html)

You can enable API caching in API Gateway to cache your endpoint's responses. With caching, you can reduce the number of calls
made to your endpoint and also improve the latency of requests to your API.

When you enable caching for a stage, API Gateway caches responses from your endpoint for a specified time-to-live period,
in seconds. API Gateway then responds to the request by looking up the endpoint response from the cache instead of making
a request to your endpoint. The default TTL value for API caching is 300 seconds. The maximum TTL value is 3600 seconds.
TTL=0 means caching is disabled.


## [API Gateway Canary Deployment](https://docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html)

Canary release is a software development strategy in which a new version of an API is deployed for testing purposes,
and the base version remains deployed as a production release for normal operations on the same stage.
In a canary release deployment, total API traffic is separated at random into a production release and a canary release with a pre-configured ratio.


## [API Gateway Integrations](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-integration-settings.html)

- **MOCK:** hardcoded response without sending the request to a backend
- **HTTP Endpoint:** forward request to http endpoint using a proxy
- **Lambda:** forward request to lambda function to handle and make a response


## [API Gateway Mapping Template](https://docs.aws.amazon.com/apigateway/latest/developerguide/models-mappings.html)

A mapping template transformation uses a mapping template to modify your integration request or integration response.
A mapping template is a script expressed in Velocity Template Language (VTL) and applied to a payload using JSONPath based on the `Content-type` header.


## [API Gateway OpenAPI](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-import-api.html)

You can use API Gateway to import a REST API from an external definition file into API Gateway or export a stage as OpenAPI spec.


## [API Gateway Usage Plan & API Keys](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-usage-plans.html)

A usage plan specifies who can access one or more deployed API stages and methods and optionally sets the target request rate to start throttling requests.
The plan uses API keys to identify API clients and who can access the associated API stages for each key. API keys are supplied using the `x-api-key` header.


## [API Gateway Monitoring](https://docs.aws.amazon.com/apigateway/latest/developerguide/rest-api-monitor.html)

- **CloudWatch Metrics:** capture related metrics to your API Gateway
  (`Count`, `4XXError`, `5XXError`, `CacheHitCount`, `CacheMissCount`, `Latency`, `IntegrationLatency`)
- **CloudWatch Logs:** log requests and response going through API Gateway
- **X-Ray:** enable tracing about requests in an API


## [API Gateway Security](https://docs.aws.amazon.com/apigateway/latest/developerguide/security.html)

API Gateway supports IAM for Authentication and IAM Policies for Authorization of requests.
Alternatively, it supports user management using Cognito User Pools.
