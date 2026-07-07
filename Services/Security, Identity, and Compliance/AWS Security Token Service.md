## [AWS Security Token Service](https://docs.aws.amazon.com/STS/latest/APIReference/welcome.html)

AWS Security Token Service enables you to request temporary, limited-privilege credentials.

### [Security Token Service AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)

`AssumeRole` lets a principal, such as a user or service, obtain temporary, short-lived security credentials
for a different IAM role.

### [Security Token Service GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html)

`GetSessionToken` lets an existing IAM user obtain temporary credentials for its own identity, often requiring MFA.
Unlike `AssumeRole`, it doesn't change the principal, but wraps those permissions in a short-lived session that can
be MFA-gated and time-bounded.
