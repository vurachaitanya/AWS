## IAM Access

### PATH :
- Just because you give a user and user group the same path doesn't automatically put that user in that user group. For example, you might create a Developers user group and specify its path as /division_abc/subdivision_xyz/product_1234/engineering/. Just because you create a user named Bob and give him that same path doesn't automatically put Bob in the Developers user group. IAM doesn't enforce any boundaries between users or user groups based on their paths. Users with different paths can use the same resources

### IAM Roles:

### IAM ARN :
- Most resources have a friendly name (for example, a user named Bob or a user group named Developers). However, the permissions policy language requires you to specify the resource or resources using the following Amazon Resource Name (ARN) format.
`arn:partition:service:region:account:resource`

### IAM Policy
![image](https://user-images.githubusercontent.com/6918419/116284654-f1539e00-a7aa-11eb-957e-cffe92b84090.png)
