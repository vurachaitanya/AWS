## AWS_Security

#### AWS Security Basic :
-	**At rest :** Designed to protect data against unauthorized access and theft.
-	**In Transit :** Designed to protect data that is being transferred between two places.
-	**Plaintext :** Unencrypted data
-	**Algorithm :** Code that takes plaintext and the encryption key and encrypts your data
-	**Key :** Password
-	**Ciphertext :** Encrypted data

Symmetric | Asymmetric
---|---
Use algorithms – AES 256 | Two keys: public and private
Same key is used for encryption and decryption| public key generates ciphertext
Laptops, local file encryption | private key decrypts
One party| two party


#### Key Management Service (KMS) Overview
-	KMS is an AWS service that integrates with other AWS services
-	Regional and public service
-	Sits in the AWS public Zone
-	Allows us to create, store and manage cryptographic keys
-	Encrypt and decrypt plaintext to ciphertext
-	Works with symmetric and asymmetric keys.
-	KMS can only imports keys and manage in KMS and can’t take out keys outsize of KMS.
-	FIPS 140-2(L2) are supported
-	KMS features are compliant with Level 3
-	KMS manages customer master keys (CMK’s)
-	CMK’s hold the ID, Creation date, resource policy, description and state
-	It holds data of 4KB of data and also larger size data encryption keys.
-	Different roles will have different access like one will have only to encrypt and other will have decrypt.
-	CMKs are created for resources key policies and key policies and they can also be used along with IAM policies
-	KMS allows role separation providing another layer of security, as the encrypt and decrypt roles are separate.
-	CMK’s are regional and isolated to that region. CMKs can’t be used across regions. 

AWS Managed CMK | Customer Managed Keys
--- | ---
Created by AWS | Created by us
Used in S3 using KMS | More configurable
Support key rotation | Support key rotation
Key rotation can’t be disabled | key rotation is optional
Rotation occurs every 3 years | rotation occurs once a year

#### AWS Systems Manager Parameter store
-	Securely store configurations and secrets
-	Optional KMS to encrypt our configurations
-	Scalable, durable and free to use
-	Allows version tracking of configurations and secrets
-	IAM permissions needs 1. cloudwatch events & 2 Cloudformatio

![AWS System manager parameter sotre interactin with app](https://github.com/vurachaitanya/AWS/blob/master/images/AWS%20Systems%20manager%20parameter%20store.JPG)

-	When an app is created we can route our requests to AWS System manager parameter store so with required IAM access.
-	Once it has the access it System manager will automatically checks with KMS can decrypt configurations 
-	Once its decrypts it request configuration parameter etc.
-	**NOTE** No direct interacting with KMS, SSM Parameter store handles that interaction for us. 
-	Allows us to securely store our configurations and secrets along with version tracking
-	Define a hierarchy to store parameters – Plaintext or encrypted parameters
-	GetParameters or GetParametersByPath API


#### AWS Secrets managers :
-	Designed to store secrets
-	Can force rotation of your secrets every X no of days
-	Can automate the generation of secrets on the rotation
-	Can integrate with RDS to sync
-	Secrets are encrypted using KMS
-	Used mostly with RDS