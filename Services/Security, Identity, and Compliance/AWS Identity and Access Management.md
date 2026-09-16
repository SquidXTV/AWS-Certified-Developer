# [AWS Identity and Access Management (IAM)](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)

## [IAM SSL/TLS Server Certificates](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_server-certs.html)

Use IAM as a certificate manager only when you must support HTTPS connections in a Region that is not supported by ACM.
IAM securely encrypts your private keys and stores the encrypted version in IAM SSL certificate storage.
IAM supports deploying server certificates in all Regions, but you must obtain your certificate from an external provider
for use with AWS. You cannot upload an ACM certificate to IAM. Additionally, you cannot manage your certificates from the IAM Console.
