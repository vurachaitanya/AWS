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
- `aws iam get-account-summary|jq .SummaryMap.Users` -- Account information and  grep summary map users list
- `aws iam list-policies --scope Local --only-attached --policy-usage-filter PermissionsPolicy` -- Policy details (ID, Name), ARN, Path, CreateDate date, update date etc
- `aws iam get-user --user-name test --profile personal` - List user test for the aws profile personal [AWS Reff](https://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html)
 - `aws codecommit list-repositories` - ListRepositories  , which lists all AWS CodeCommit repositories asso-ciated with your AWS account.
 - `aws codecommit list-branches --repository-name <Repo name>` - ListBranches , which lists all branches for a specified repository.
 - `aws codecommit list-pull-requests --repository-name <Repo name>` - ListPullRequests , which lists all pull requests for a repository
 - `aws sts get-caller-identity --profile sandbox` to check which profile it is assuming 


### AWS Commands :
```
accessanalyzer                           | acm
acm-pca                                  | alexaforbusiness
amplify                                  | apigateway
apigatewaymanagementapi                  | apigatewayv2
appconfig                                | application-autoscaling
application-insights                     | appmesh
appstream                                | appsync
athena                                   | autoscaling
autoscaling-plans                        | backup
batch                                    | budgets
ce                                       | chime
cloud9                                   | clouddirectory
cloudformation                           | cloudfront
cloudhsm                                 | cloudhsmv2
cloudsearch                              | cloudsearchdomain
cloudtrail                               | cloudwatch
codebuild                                | codecommit
codeguru-reviewer                        | codeguruprofiler
codepipeline                             | codestar
codestar-connections                     | codestar-notifications
cognito-identity                         | cognito-idp
cognito-sync                             | comprehend
comprehendmedical                        | compute-optimizer
connect                                  | connectparticipant
cur                                      | dataexchange
datapipeline                             | datasync
dax                                      | detective
devicefarm                               | directconnect
discovery                                | dlm
dms                                      | docdb
ds                                       | dynamodb
dynamodbstreams                          | ebs
ec2                                      | ec2-instance-connect
ecr                                      | ecs
efs                                      | eks
elastic-inference                        | elasticache
elasticbeanstalk                         | elastictranscoder
elb                                      | elbv2
emr                                      | es
events                                   | firehose
fms                                      | forecast
forecastquery                            | frauddetector
fsx                                      | gamelift
glacier                                  | globalaccelerator
glue                                     | greengrass
groundstation                            | guardduty
health                                   | iam
imagebuilder                             | importexport
inspector                                | iot
iot-data                                 | iot-jobs-data
iot1click-devices                        | iot1click-projects
iotanalytics                             | iotevents
iotevents-data                           | iotsecuretunneling
iotsitewise                              | iotthingsgraph
kafka                                    | kendra
kinesis                                  | kinesis-video-archived-media
kinesis-video-media                      | kinesis-video-signaling
kinesisanalytics                         | kinesisanalyticsv2
kinesisvideo                             | kms
lakeformation                            | lambda
lex-models                               | lex-runtime
license-manager                          | lightsail
logs                                     | machinelearning
macie                                    | macie2
managedblockchain                        | marketplace-catalog
marketplace-entitlement                  | marketplacecommerceanalytics
mediaconnect                             | mediaconvert
medialive                                | mediapackage
mediapackage-vod                         | mediastore
mediastore-data                          | mediatailor
meteringmarketplace                      | mgh
migrationhub-config                      | mobile
mq                                       | mturk
neptune                                  | networkmanager
opsworks                                 | opsworkscm
organizations                            | outposts
personalize                              | personalize-events
personalize-runtime                      | pi
pinpoint                                 | pinpoint-email
pinpoint-sms-voice                       | polly
pricing                                  | qldb
qldb-session                             | quicksight
ram                                      | rds
rds-data                                 | redshift
rekognition                              | resource-groups
resourcegroupstaggingapi                 | robomaker
route53                                  | route53domains
route53resolver                          | s3control
sagemaker                                | sagemaker-a2i-runtime
sagemaker-runtime                        | savingsplans
schemas                                  | sdb
secretsmanager                           | securityhub
serverlessrepo                           | service-quotas
servicecatalog                           | servicediscovery
ses                                      | sesv2
shield                                   | signer
sms                                      | sms-voice
snowball                                 | sns
sqs                                      | ssm
sso                                      | sso-oidc
stepfunctions                            | storagegateway
sts                                      | support
swf                                      | synthetics
textract                                 | transcribe
transfer                                 | translate
waf                                      | waf-regional
wafv2                                    | workdocs
worklink                                 | workmail
workmailmessageflow                      | workspaces
xray                                     | s3api
s3                                       | configure
deploy                                   | configservice
opsworks-cm                              | runtime.sagemaker
history                                  | help
```
