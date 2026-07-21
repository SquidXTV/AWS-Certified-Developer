# [Amazon Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)

Amazon Cognito is an identity platform for web and mobile apps. It’s a user directory, an authentication server,
and an authorization service for OAuth 2.0 access tokens and AWS credentials. With Amazon Cognito, you can authenticate
and authorize users from the built-in user directory, from your enterprise directory, and from consumer identity providers like Google and Facebook.

## [Cognito User Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools.html)

An Amazon Cognito user pool is a user directory for web and mobile app authentication and authorization.
Cognito supports several methods to authenticate users such as simple username/password, email or phone
number verification, multi-factor authentication, or federated identities from Facebook or others.

### [Cognito User Pool Lambda Triggers](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-working-with-lambda-triggers.html)

Amazon Cognito works with AWS Lambda functions to modify the authentication behavior at various stages of your user pool.
This includes triggers such as pre authentication, post authentication, pre token generation and pre sign-up triggers.


### [Cognito User Pool Managed Login](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-managed-login.html)

The managed login pages are a collection of provided web interfaces for basic sign-up, sign-in, multi-factor authentication and
password-reset activities in your user pool. You can make the managed login user experience fit your brand with custom logos, backgrounds and styles.


### [Cognito Adaptive Authentication](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pool-settings-adaptive-authentication.html)

With adaptive authentication, you can configure your user pool to block suspicious sign-ins or add second factor authentication in response to
an increased risk level. For each sign-in attempt, Amazon Cognito generates a risk score for how likely the sign-in request is to be from a
compromised source. This risk score is based on device and user factors that your application provides, and others that Amazon Cognito derives
from the request. Some factors that contribute to the risk evaluation by Amazon Cognito are IP address, user agent, and geographical distance
from other sign-in attempts. Adaptive authentication can turn on or require multi-factor authentication (MFA) for a user in your user pool when
Amazon Cognito detects risk in a user's session, and the user hasn't yet chosen an MFA method.



## [Cognito Identity Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-identity.html)

An Amazon Cognito identity pool is a directory of federated identities that you can exchange for AWS credentials.
Identity pools generate temporary AWS credentials for the users of your app to interact with AWS Services.
