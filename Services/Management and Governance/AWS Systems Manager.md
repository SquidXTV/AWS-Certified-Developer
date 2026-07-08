## [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)

AWS Systems Manager helps you centrally view, manage, and operate nodes at scale in AWS, on-premises,
and multicloud environments. With the launch of a unified console experience, Systems Manager consolidates
various tools to help you complete common node tasks across AWS accounts and AWS Regions.

### [Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html)

Parameter Store enables you to securely store, organize, and retrieve simple configuration data at scale.
It is designed to simplify configuration management across environments, allowing teams to standardize
how applications access critical data without hardcoding values or relying on fragmented storage solutions.

#### [Parameter Store Hierarchy](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-paramstore-hierarchies.html)

You can use parameter hierarchies to help you organize and manage parameters. A hierarchy is a parameter name
that includes a path that you define by using forward slashes (/).

#### [Parameter Store Policies](https://docs.aws.amazon.com/systems-manager/latest/userguide/parameter-store-policies.html)

Parameter policies help you manage a growing set of parameters by allowing you to assign specific criteria
to a parameter such as an expiration date or time to live. Parameter policies are especially helpful in
forcing you to update or delete passwords and configuration data stored in Parameter Store, a tool in AWS Systems Manager.
