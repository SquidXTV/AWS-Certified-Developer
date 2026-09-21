# [AWS Identity and Access Management (IAM)](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources.
With IAM, you can manage permissions that control which AWS resources users can access.
You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.
IAM provides the infrastructure necessary to control authentication and authorization for your AWS accounts.

## [IAM Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)

When you first create an Amazon Web Services (AWS) account, you begin with a single sign-in identity that has
complete access to all AWS services and resources in the account. This identity is called the AWS account root user.
The email address and password that you used to create your AWS account are the credentials you use to sign in as your root user.

While MFA is enforced for root users by default, it requires customer action to add MFA during the initial account creation or as prompted during sign-in.


## [IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)

An IAM user is an entity that you create in your AWS account. The IAM user represents the human user or workload
who uses the IAM user to interact with AWS resources. An IAM user consists of a name and credentials.
An IAM user can represent a person or an application that uses its credentials to make AWS requests. This is typically referred to as a service account.

An IAM user with administrator permissions is not the same thing as the AWS account root user.

### [IAM Users Access Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html#id_users_creds)

You can access AWS in different ways depending on the IAM user credentials:
- Console password
- Access keys
- SSH keys for CodeCommit


### [IAM User Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html#id_users_perms)

By default, a new IAM user has no permissions to do anything. They are not authorized to perform any AWS operations or to access any AWS resources.
An advantage of having individual IAM users is that you can assign permissions individually to each user.
You might assign administrative permissions to a few users, who then can administer your AWS resources and can even create and manage other IAM users.
In most cases, however, you want to limit a user's permissions to just the tasks (AWS actions or operations) and resources that are needed for the job. 


### [IAM User and Accounts](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html#id_users_accounts)

Each IAM user is associated with one and only one AWS account. Because IAM users are defined within your AWS account,
they don't need to have a payment method on file with AWS. Any AWS activity performed by IAM users in your account is billed to your account.



## [IAM User Groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html)

An IAM user group is a collection of IAM users. User groups let you specify permissions for multiple users,
which can make it easier to manage the permissions for those users.

- A user group can contain many users, and a user can belong to multiple user groups.
- User groups can't be nested; they can contain only users, not other IAM groups.
- There is no default user group that automatically includes all users in the AWS account. If you want to have a user group like that, you must create it and assign each new user to it.


## [IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)

An IAM role is an IAM identity that you can create in your account that has specific permissions.
An IAM role is similar to an IAM user, in that it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS.
However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it.
Also, a role does not have standard long-term credentials such as a password or access keys associated with it.
Instead, when you assume a role, it provides you with temporary security credentials for your role session.

### [IAM Service Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#id_roles_terms-and-concepts)

A service role is an IAM role that a service assumes to perform actions on your behalf.


### [IAM Role Chaining](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#id_roles_terms-and-concepts)

Role chaining is when you use a role to assume a second role. For example, RoleA has permission to assume RoleB.
You can enable User1 to assume RoleA by using their long-term user credentials in the AssumeRole API operation.
This returns RoleA short-term credentials. With role chaining, you can use RoleA's short-term credentials to enable User1 to assume RoleB.


### [IAM Delegation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#id_roles_terms-and-concepts)

The granting of permissions to someone to allow access to resources that you control. Delegation involves setting up a trust between two accounts.
The first is the account that owns the resource. The second is the account that contains the users that need to access the resource.


### [IAM Role for Cross-Account Access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#id_roles_terms-and-concepts)

A role that grants access to resources in one account to a trusted principal in a different account. Roles are the primary way to grant cross-account access.
However, some AWS services allow you to attach a policy directly to a resource. These are called resource-based policies,
and you can use them to grant principals in another AWS account access to the resource.



## [IAM Principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#id_roles_additional-resources)

Principals are entities in AWS that can perform actions and access resources. A principal can be an AWS account root user, an IAM user, or a role.
A principal that represents the identity of an AWS service is a service principal. Use the Principal element in role trust policies to define
the principals that you trust to assume the role.


## [IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)

Manage access in AWS by creating policies and attaching them to IAM identities (users, groups of users, or roles) or AWS resources.
A policy is an object in AWS that, when associated with an identity or resource, defines their permissions.
AWS evaluates these policies when an IAM principal (user or role) makes a request. Permissions in the policies determine whether the request is allowed or denied.
Most policies are stored in AWS as JSON documents.

The JSON policy document structure contains the following elements:
- **Version:** The version of the policy language that you want to use
- **Statement:** Main element container for one or more statements
- **Sid (Optional):** Statement id to differentiate between statements
- **Effect:** Use `Allow` or `Deny` to indicate whether the policy allows or denies access
- **Principal:** The principal to allow/deny access to a resource policy, implied automatically for Identity-based policies
- **Action:** A list of actions that the policy allows or denies
- **Resource:** A list of resources to which the actions apply
- **Condition (Optional):** Specify the condition under which the policy applies

### [IAM Identity-based Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#access_policy-types)

Identity-based policies are JSON permissions policy documents that control what actions an identity (users, groups of users, and roles) can perform,
on which resources, and under what conditions. Identity-based policies can be further categorized:
- **Managed Policies:** Standalone stored identity-based policies that you can attach to multiple users, groups, and roles and is either managed by AWS or made by the customer
- **Inline Policies:** Policies that get added directly to a single user, group, or role that strictly maintain a one-to-one relationship and get deleted when you delete the identity


### [IAM Resource-based Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#access_policy-types)

Resource-based policies are JSON policy documents that you attach to a resource such as an Amazon S3 bucket.
These policies grant the specified principal permission to perform specific actions on that resource and defines under what conditions this applies.
Resource-based policies are inline policies. There are no managed resource-based policies.

To enable cross-account access, you can specify an entire account or IAM entities in another account as the principal in a resource-based policy.
Adding a cross-account principal to a resource-based policy is only half of establishing the trust relationship.
When the principal and the resource are in separate AWS accounts, you must also use an identity-based policy to grant the principal access to the resource. 

The IAM service supports only one type of resource-based policy called a role trust policy, which is attached to an IAM role.
An IAM role is both an identity and a resource that supports resource-based policies. For that reason, you must attach both a trust policy
and an identity-based policy to an IAM role. Trust policies define which principal entities (accounts, users, roles, and federated users) can assume the role.



## [IAM Credentials Report](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_getting-report.html)

You can generate and download a credential report that lists all users in your account and the status of their various credentials,
including passwords, access keys, and MFA devices.


## [IAM SSL/TLS Server Certificates](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_server-certs.html)

Use IAM as a certificate manager only when you must support HTTPS connections in a Region that is not supported by ACM.
IAM securely encrypts your private keys and stores the encrypted version in IAM SSL certificate storage.
IAM supports deploying server certificates in all Regions, but you must obtain your certificate from an external provider
for use with AWS. You cannot upload an ACM certificate to IAM. Additionally, you cannot manage your certificates from the IAM Console.
