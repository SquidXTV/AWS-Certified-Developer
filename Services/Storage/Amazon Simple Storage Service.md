# [Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)

## [S3 Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html)


- **SSE-S3 (default):**
	automatically encrypts objects at rest using its own managed keys with AES-256
	
	`x-amz-server-side-encryption: AES-256`
- **SSE-KMS:**
	encrypts objects at rest using AWS KMS customer or AWS-managed keys for centralized management, fine-grained access control, rotation, and auditing
	
	`x-amz-server-side-encryption: aws:kms`
- **SSE-C:**
	encrypts objects at rest using customer-provided encryption keys sent with each requests, requires https
	
	```
	x-amz-server-side-encryption-customer-algorithm: AES-256
	x-amz-server-side-encryption-customer-key: <key>
	x-amz-server-side-encryption-customer-key-MD5: <md5 hash of key for validation>
	```
- **Client-side encryption:**
	encrypt objects before sending them to S3 and decrypt it after retrieval manually
