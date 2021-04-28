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
arn:aws:iam::123456789012:root
arn:aws:iam::123456789012:user/JohnDoe
arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/JaneDoe
arn:aws:iam::123456789012:group/Developers
arn:aws:iam::123456789012:group/division_abc/subdivision_xyz/product_A/Developers
arn:aws:iam::123456789012:role/S3Access
arn:aws:iam::123456789012:role/application_abc/component_xyz/RDSAccess
arn:aws:iam::123456789012:role/aws-service-role/access-analyzer.amazonaws.com/AWSServiceRoleForAccessAnalyzer
arn:aws:iam::123456789012:role/service-role/QuickSightAction
arn:aws:iam::123456789012:policy/UsersManageOwnCredentials
arn:aws:iam::123456789012:policy/division_abc/subdivision_xyz/UsersManageOwnCredentials
arn:aws:iam::123456789012:instance-profile/Webserver
arn:aws:sts::123456789012:federated-user/JohnDoe
arn:aws:sts::123456789012:assumed-role/Accounting-Role/JaneDoe
arn:aws:iam::123456789012:mfa/JaneDoeMFA
arn:aws:iam::123456789012:u2f/user/JohnDoe/default (U2F security key)
arn:aws:iam::123456789012:server-certificate/ProdServerCert
arn:aws:iam::123456789012:server-certificate/division_abc/subdivision_xyz/ProdServerCert
arn:aws:iam::123456789012:saml-provider/ADFSProvider
arn:aws:iam::123456789012:oidc-provider/GoogleProvider
 ```
 - The following example shows a policy that you could assign to Richard to allow him to manage his own access keys. Notice that the resource is the IAM user Richard.
 ```
 {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageRichardAccessKeys",
            "Effect": "Allow",
            "Action": [
                "iam:*AccessKey*",
                "iam:GetUser"
            ],
            "Resource": "arn:aws:iam::*:user/division_abc/subdivision_xyz/Richard"
        },
        {
            "Sid": "ListForConsole",
            "Effect": "Allow",
            "Action": "iam:ListUsers",
            "Resource": "*"
        }
    ]
}
 ```
 - You can use wildcards in the resource portion of the ARN to specify multiple users or user groups or policies. For example, to specify all users working on product_1234, you would use: `arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/product_1234/*`
- Let's say you have users whose names start with the string app_. You could refer to them all with the following ARN. `arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/product_1234/app_*`
- In this example, Jules in the Marketing_Admin user group creates a project-based user group within the /marketing/ path. Jules assigns users from different parts of the company to the user group. This example illustrates that a user's path isn't related to the user groups the user is in.
  - The marketing group has a new product they'll be launching, so Jules creates a new user group in the /marketing/ path called Widget_Launch. Jules then assigns the following policy to the user group, which gives the user group access to objects in the part of the example_bucket that is designated to this particular launch.
 ```
 {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::example_bucket/marketing/newproductlaunch/widget/*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket*",
      "Resource": "arn:aws:s3:::example_bucket",
      "Condition": {"StringLike": {"s3:prefix": "marketing/newproductlaunch/widget/*"}}
    }
  ]
}
 ```

### IAM Policy
![image](https://user-images.githubusercontent.com/6918419/116284654-f1539e00-a7aa-11eb-957e-cffe92b84090.png)
