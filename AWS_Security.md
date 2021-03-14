## AWS_Security

##### Ref :  Logging and Security for Associate AWS Solutions Architects

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


#### Cloud HSM 
-	Hardware security module
-	AWS provisions the encryption hardware for us
-	We use our won client to perform encryption
-	Dedicated hardware
-	Tamper resistant 
-	FIPS 140-2(L3)
-	CloudHSM software can be used to manage encryption keys and users
-	IAM permissions can only be used to create, read, update and delete your HSM cluster.
-	It should be added to each AZ for HA
-	It supports Symmetric and asymmetric encryption.
-	If we lose AWS CloudHSM credential, we can’t restore them & it’s not AWS responsibility.


#### EC2 Proxy servers:
-	**What is firewall: ** A deice that sits at the border of different networks and monitors traffic flows.
-	Reads pkt data and allow or deny traffic.
-	Establishes a barrier to offer different security levels. 
-	Higher the Networking layer higher the cost of the computing process to flow.
-	Web application firewall – WAP
-	Advance version of WAP is – AWS Shield 
-	Proxy server = Firewall 
-	It can sit in public or private subnets of AZ in a VPC.
-	It handles out going traffic and uses Gateway to send and receive the traffic. 
-	Using proxy servers need application support. 
-	It can be configured inside browser, OS, application. 
-	User connects to the proxy server using Username/passwd to destination servers
-	Proxy server can be acts as a **Caching server**, **Filter** which filters malware using IP address as we can’t see the layers. 
-	AWS EC2 Proxy server instance acts as an additional filter for AWS network filtering.
![Networking layers](https://github.com/vurachaitanya/AWS/blob/master/images/Network%20security%20layers.JPG)

#### Web application firewall (WAF) & AWS Shield overview
-	WAF filters at layer 7 which is at HTTP/HTTPS.
-	WAF can be implemented at 3 levels 1. Application Load Balancer 2. API Gateway & 3. Cloudfront.
-	Add a web access control list (ACL) and add rules at IP address, HTTP Headders, body or URL Strings. 
-	This will protect us from SQL injections & Cross site scripting.
-	Can also work on Geo Match
-	DDos attacks.
-	How many network packets can pass through? 

#### AWS Firewall manager:
-	Manages all rules for our WAF
-	Application Load Balancer
-	API Gateway 
-	cloudFront


#### AWS Shield :
-	AWS Shield standard is free and provides protection from attacks on layers 3 & 4.
-	AWS Shield Advance will support DDoS attack and starts at $3k per month & provides 24/7 protection from attacks on EC2, LB, CloudFront & Route53.
-	Can only be used with Application Load balancer, Classic load balancer, Elastic IP & BFcloudfront.


#### AWS Guard Duty:
-	Is a threat detection service that provides insights into activity. 
-	Monitors for malicious activity and unauthorized behavior in S3.
-	IT uses AI/ML intelligence by anomaly detection and thread detection to identify and prevents it.
-	Monitors account and resources like Cloudtrail Event logs, VPC Flow logs, DNS logs.
-	Integrates with cloudwatch events and watches activity inside your AWS account. 
-	Based on the analyses we can integrate with lamda function to automatic remediation or Malware and no extra infrastructure cost. 
