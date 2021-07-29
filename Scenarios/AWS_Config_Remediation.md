### securityhub-lambda-function-public-access-prohibited 
- [AWS Doc about the config rule](https://docs.aws.amazon.com/config/latest/developerguide/lambda-function-public-access-prohibited.html)
- [Terraform code for the rule](https://asecure.cloud/a/lambda-function-public-access-prohibited/)

```
resource "aws_config_config_rule" "ConfigRule" {
  name = "lambda-function-public-access-prohibited"
  description = "A Config rule that checks whether the AWS Lambda function policy attached to the Lambda resource prohibits public access. If the Lambda function policy allows public access it is noncompliant."

  source {
    owner = "AWS"
    source_identifier = "LAMBDA_FUNCTION_PUBLIC_ACCESS_PROHIBITED"
  }
  scope {
    compliance_resource_types = ["AWS::Lambda::Function"]
  }
}
```
- One of the lambda functions is non-compliant and we try fixing the IAM Policy permission of the lambda to fix the issue. But we need to focus on the services which are attached to lambda has got public access is making compliant.
- We fixed this by adding ` aws_lambda_permission` with `source_arn` and `source_account`, so as to get lambda access to only to single account.
- [Fixed detailed doc from AWS](https://docs.aws.amazon.com/lambda/latest/dg/access-control-resource-based.html)
