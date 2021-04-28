## IAM Access

###### [Reff AWS doc](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html)

### PATH :
- Just because you give a user and user group the same path doesn't automatically put that user in that user group. For example, you might create a Developers user group and specify its path as /division_abc/subdivision_xyz/product_1234/engineering/. Just because you create a user named Bob and give him that same path doesn't automatically put Bob in the Developers user group. IAM doesn't enforce any boundaries between users or user groups based on their paths. Users with different paths can use the same resources

### IAM Roles:

### IAM ARN :
- Most resources have a friendly name (for example, a user named Bob or a user group named Developers). However, the permissions policy language requires you to specify the resource or resources using the following Amazon Resource Name (ARN) format.
`arn:partition:service:region:account:resource`
  - `partition` identifies the partition that the resource is in. For standard AWS Regions, the partition is aws. If you have resources in other partitions, the partition is aws-partitionname.
  - `service` identifies the AWS product. For IAM resources, this is always iam.
  - `region` is the Region the resource resides in. For IAM resources, this is always kept blank.
  - `account` is the AWS account ID with no hyphens.
  - `resource` is the portion that identifies the specific resource by name.
  - The Region portion of the ARN is blank because IAM resources are global.
 ```
 arn:aws:iam::account-id:root  
arn:aws:iam::account-id:user/user-name-with-path
arn:aws:iam::account-id:group/group-name-with-path
arn:aws:iam::account-id:role/role-name-with-path
arn:aws:iam::account-id:policy/policy-name-with-path
arn:aws:iam::account-id:instance-profile/instance-profile-name-with-path
arn:aws:sts::account-id:federated-user/user-name
arn:aws:sts::account-id:assumed-role/role-name/role-session-name
arn:aws:iam::account-id:mfa/virtual-device-name-with-path
arn:aws:iam::account-id:u2f/u2f-token-id
arn:aws:iam::account-id:server-certificate/certificate-name-with-path
arn:aws:iam::account-id:saml-provider/provider-name
arn:aws:iam::account-id:oidc-provider/provider-name
 
 ```

### IAM Policy
![image](https://user-images.githubusercontent.com/6918419/116284654-f1539e00-a7aa-11eb-957e-cffe92b84090.png)
