## AWS CLI 
#### AWS CLI :
-	`aws configure` -  to configure the credentials.
-	You will be asked with AWS Access key ID:
-	You will be asked for Secret Access key:
-	You will be asked with default region name: 
-	You will be asked with output format:
-	`aws s3 ls` to list the s3 buckets
-	`aws s3 mb s3://testbucket12323232` to create a new s3 bucket.
-	`aws configure list`  -- list of configuration available in detail
-	`aws configure get region –profile chaitu `  -- list profile specific region configured 
-	[AWS CLI official 57Pg](https://docs.aws.amazon.com/cli/latest/userguide/aws-cli.pdf)
-	`aws iam list-users --profile chaitu` list all the users created throught IAM.
-	list current user's info : `aws iam get-user`
-	list all security groups : `aws ec2 describe-security-groups`
-	list all keypairs  `aws ec2 describe-key-pairs`
-	[Other userful cheatsheet](https://gist.github.com/apolloclark/b3f60c1f68aa972d324b)
-	List API Gateway IDs and Names: `aws apigateway get-rest-apis | jq -r ‘.items[ ] | .id+” “+.name’`
-	[AWS CLI Cheatsheet](https://www.bluematador.com/learn/aws-cli-cheatsheet)
-	[AWS Cheatsheet](https://dev.to/mdminhazulhaque/aws-cli-cheatsheet-15f2)
-	`aws ec2 describe-images --owners self amazon` -- List all the images whos owner is Amazon
-	`aws ec2 describe-images --owners self amazon --filters "Name=root-device-type,Values=ebs"` -- AMI's with EBS volume for root device.
- `aws ssm get-parameters-by-path --path /aws/service/ami-amazon-linux-latest --query "Parameters[].Name"` ---list latest Amazon images path and types