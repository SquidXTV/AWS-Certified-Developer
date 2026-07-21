# [AWS Key Management Service (KMS)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)

AWS Key Management Service creates, stores, and controls cryptographic keys used to encrypt data across
many AWS services. It provides centralized key policies, automatic rotation, and auditing.

## [Key Management Service Key Types](https://docs.aws.amazon.com/kms/latest/developerguide/kms-cryptography.html)

Key Management Service supports both symmetric and asymmetric keys. **Symmetric keys** use a single secret key
for both encryption and decryption internally. **Asymmetric keys** are public/private key pairs used for encryption,
decryption, and digital signature.


## [Key Management Service Key Management Types](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)

Key Management Service supports different Key Management Types. **AWS-owned keys** are completely internal, invisible, and
managed by AWS. **AWS-managed keys** are created per service, but still managed by AWS. **Customer-managed keys** are
created by the customer and under full control.


## [Key Management Service Key Policies](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html)

A key policy is a resource policy for an AWS KMS key. Key policies are the primary way to control access to KMS keys.
Every KMS key must have exactly one key policy. The statements in the key policy determine who has permission to use
the KMS key and how they can use it.


## [Key Management Service Envelope Encryption](https://docs.aws.amazon.com/kms/latest/developerguide/kms-cryptography.html#enveloping)

Envelope encryption is a pattern where you encrypt your data with a locally generated data key, and then encrypt that
small data key itself with a master key. The encrypted data key (the “envelope”) is stored alongside the ciphertext,
and on decryption you first ask KMS to decrypt the data key, then use that plaintext data key to decrypt the bulk data.
Because the KMS APIs can only process up to 4 KB of plaintext per call, larger files must be encrypted and decrypted
locally using data keys, while KMS is used only to protect those small keys.
