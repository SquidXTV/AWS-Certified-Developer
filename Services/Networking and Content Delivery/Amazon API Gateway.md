## [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)
Amazon API Gateway is an AWS service for creating, publishing, maintaining, monitoring, and securing REST, HTTP,
and WebSocket APIs at any scale. API developers can create APIs that access AWS or other web services, as well as
data stored in the AWS Cloud.

### [API Gateway Endpoint Type](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html)
- **Edge-optimized:** requests are routed to the nearest CloudFront Edge Location and routed to the API Gateway
- **Regional:** requests are targeted directly to the region-specific API Gateway
- **Private:** requests can only be accessed from within a private VPC

### [API Gateway Deployment](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-deployments.html)
A Deployment is a snapshot of an API with its configuration at a specific point.

### [API Gateway Stages](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-stages.html)
A Stage is a named reference to a specific deployment.

#### [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html)
Stage variables are key-value pairs that you can define as configuration attributes associated with a deployment stage of a REST API.
They act like environment variables and can be used in your API setup and mapping templates. With deployment stages in API Gateway,
you can manage multiple release stages for each API and use stage variables you can configure an API deployment stage to interact
with different backend endpoints.


### [API Gateway Caching](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-caching.html)
