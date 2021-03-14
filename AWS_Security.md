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
