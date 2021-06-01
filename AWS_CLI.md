- ## AWS CLI 
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
-	`aws sts decode-authorization-message --encoded-message <encodedmessage>` If EC2 failed with an error and need to decode it.
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
- `aws iam get-user --user-name test --profile personal` - List user test for the aws profile personal [AWS Reff](https://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html)
- `aws codecommit list-repositories` - ListRepositories  , which lists all AWS CodeCommit repositories asso-ciated with your AWS account.
- `aws codecommit list-branches --repository-name <Repo name>` - ListBranches , which lists all branches for a specified repository.
- `aws codecommit list-pull-requests --repository-name <Repo name>` - ListPullRequests , which lists all pull requests for a repository
- `aws sts get-caller-identity --profile sandbox` to check which profile it is assuming 

### AWS Config :
- `aws configservice describe-config-rules` AWS Config Rule Described.

### IAM :
- `aws iam list-groups --profile lab` - List groups in AWS Profile
- `aws iam list-users --profile lab` - List users
- `aws iam list-policies` - List all policy name,id, ARN
- `aws iam get-account-authorization-details` will give policy and detailed services listed associated to policy.
- `aws iam get-policy --policy-arn arn:aws-us-gov:iam::aws:policy/AmazonRoute53FullAccess` Policy details with description and attached status.
- `aws iam generate-service-last-accessed-details --arn arn:aws-us-gov:iam::aws:policy/AWSIoTDataAccess` list Policy last accessed details.
- `aws iam list-policies --scope Local --only-attached --policy-usage-filter PermissionsPolicy` -- Policy details (ID, Name), ARN, Path, CreateDate date, update date etc
- `aws iam list-roles` - List all Roles
- `aws iam list-roles --query Roles[].RoleName` - List Roles names only.
- `aws iam list-role-policies --role-name codepipeline-build` - List the Role Codepipeline policy information which is attached to.
- `aws iam list-policies  --query Policies[].[Arn,PolicyName,DefaultVersionId]` List Policys with required details using JQuery
- `aws iam list-policies-granting-service-access --service-namespaces "AWSIoTDataAccess" --arn arn:aws:iam::aws:policy/AWSIoTDataAccess  --profile personal` - Granting the services access using ARN.
- `aws iam list-attached-role-policies --role-name AWSServiceRoleForAccessAnalyzer` Lists the roles which are attached to associated Role given.
- `aws iam list-role-policies --role-name AWSServiceRoleForAccessAnalyzer` - list policys  **NOT working while testing

### Organization :
- `aws organizations list-roots` - list the root organization
- `aws organizations describe-organization` - describe organization
- `aws organizations describe-organizational-unit --organizational-unit-id` list the organization unit id details.
- `aws organizations leave-organization`  - Removes  a member account from its parent organization. This version of the operation is performed by the account that wants to leave.
- `aws organizations list-accounts` - Lists  all  the  accounts  in  the  organization.
- `aws organizations list-organizational-units-for-parent --parent-id <o-OrgID>` - List the Organization unit for the parent ID
- `aws organizations list-parents --child-id <o-OrgID>` - List the parent org info for the Chaild id given.

### RDK Framework :
- `pip install rdk` - Install RDK framework
- `rdk init` - AWS Configure should be config to work 
- `rdk create ec2_desired_instance_type --runtime python3.7 --resource-types AWS::EC2::Instance --input-parameters '{"desiredInstanceType":"t2.micro"}' ` python template would be created.
- `rdk test-local ec2_desired_instance_type` - Test cases for checking compliance Test cases. 
- `rdk modify ec2_desired_instance_type --maximum-frequency One_Hour` - modify Interval to 1 hour
- `rdk deploy ec2_desired_instance_type` - deploy AWS Config rule for EC2 deployment to be T2Micro
- `rdk sample-ci AWS::EC2::Instance` - Show list of parameters for EC2 Instance which can be given for AWS Config as input parameter.

##### Possible resources :
```
'AWS::ApiGateway::Stage', 'AWS::ApiGatewayV2::Stage', 'AWS::ApiGateway::RestApi', 'AWS::ApiGatewayV2::Api', 'AWS::CloudFront::Distribution', 'AWS::CloudFront::StreamingDistribution', 'AWS::CloudWatch::Alarm', 'AWS::DynamoDB::Table', 'AWS::EC2::Volume', 'AWS::EC2::Host', 'AWS::EC2::EIP', 'AWS::EC2::Instance', 'AWS::EC2::NetworkInterface', 'AWS::EC2::SecurityGroup', 'AWS::EC2::NatGateway', 'AWS::EC2::EgressOnlyInternetGateway', 'AWS::EC2::FlowLog', 'AWS::EC2::VPCEndpoint', 'AWS::EC2::VPCEndpointService', 'AWS::EC2::VPCPeeringConnection', 'AWS::Elasticsearch::Domain', 'AWS::QLDB::Ledger', 'AWS::Redshift::Cluster', 'AWS::Redshift::ClusterParameterGroup', 'AWS::Redshift::ClusterSecurityGroup', 'AWS::Redshift::ClusterSnapshot', 'AWS::Redshift::ClusterSubnetGroup', 'AWS::Redshift::EventSubscription', 'AWS::RDS::DBInstance', 'AWS::RDS::DBSecurityGroup', 'AWS::RDS::DBSnapshot', 'AWS::RDS::DBSubnetGroup', 'AWS::RDS::EventSubscription', 'AWS::RDS::DBCluster', 'AWS::RDS::DBClusterSnapshot', 'AWS::SNS::Topic', 'AWS::SQS::Queue', 'AWS::S3::Bucket', 'AWS::S3::AccountPublicAccessBlock', 'AWS::EC2::CustomerGateway', 'AWS::EC2::InternetGateway', 'AWS::EC2::NetworkAcl', 'AWS::EC2::RouteTable', 'AWS::EC2::Subnet', 'AWS::EC2::VPC', 'AWS::EC2::VPNConnection', 'AWS::EC2::VPNGateway', 'AWS::AutoScaling::AutoScalingGroup', 'AWS::AutoScaling::LaunchConfiguration', 'AWS::AutoScaling::ScalingPolicy', 'AWS::AutoScaling::ScheduledAction', 'AWS::ACM::Certificate', 'AWS::CloudFormation::Stack', 'AWS::CloudTrail::Trail', 'AWS::CodeBuild::Project', 'AWS::CodePipeline::Pipeline', 'AWS::ElasticBeanstalk::Application', 'AWS::ElasticBeanstalk::ApplicationVersion', 'AWS::ElasticBeanstalk::Environment', 'AWS::IAM::User', 'AWS::IAM::Group', 'AWS::IAM::Role', 'AWS::IAM::Policy', 'AWS::KMS::Key', 'AWS::Lambda::Function', 'AWS::NetworkFirewall::Firewall', 'AWS::NetworkFirewall::FirewallPolicy', 'AWS::NetworkFirewall::RuleGroup', 'AWS::SecretsManager::Secret', 'AWS::ServiceCatalog::CloudFormationProduct', 'AWS::ServiceCatalog::CloudFormationProvisionedProduct', 'AWS::ServiceCatalog::Portfolio', 'AWS::Shield::Protection', 'AWS::ShieldRegional::Protection', 'AWS::Shield::Protection', 'AWS::ShieldRegional::Protection', 'AWS::SSM::ManagedInstanceInventory', 'AWS::SSM::PatchCompliance', 'AWS::SSM::AssociationCompliance', 'AWS::SSM::FileData', 'AWS::WAF::RateBasedRule', 'AWS::WAF::Rule', 'AWS::WAF::WebACL', 'AWS::WAF::RuleGroup', 'AWS::WAFRegional::RateBasedRule', 'AWS::WAFRegional::Rule', 'AWS::WAFRegional::WebACL', 'AWS::WAFRegional::RuleGroup', 'AWS::WAFRegional::RateBasedRule', 'AWS::WAFRegional::Rule', 'AWS::WAFRegional::WebACL', 'AWS::WAFRegional::RuleGroup', 'AWS::WAFv2::WebACL', 'AWS::WAFv2::RuleGroup', 'AWS::WAFv2::ManagedRuleSet', 'AWS::XRay::EncryptionConfig', 'AWS::ElasticLoadBalancingV2::LoadBalancer', 'AWS::ElasticLoadBalancing::LoadBalancer'
```

### AWS Python API BOTO3 :
- Using boto3 list all s3 buckets :
```
import boto3
session = boto3.Session(profile_name='profile_name')
dev_s3_client = session.client('s3')
response = dev_s3_client.list_buckets()
print('Existing buckets:')
for bucket in response['Buckets']:
    print(f'  {bucket["Name"]}')
```
- Or using directly hardcoding keys in code which is not recommended :
```
import boto3
s3 = boto3.client(
    's3',
    aws_access_key_id="aaaaaaaaaaaaaaaa",
    aws_secret_access_key="bbbbbbbbbbbbbbbbbbbbbbbbb",region_name="us-west-1")

s3 = boto3.client('s3')
response = s3.list_buckets()
print('Existing buckets:')
for bucket in response['Buckets']:
    print(f'  {bucket["Name"]}')
```

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
