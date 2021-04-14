## AWS Objects

#### AssumeRole:
- [AWS Reff Doc](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)
- Returns a set of temporary security credentials that you can use to access AWS resources that you might not normally have access to. These temporary credentials consist of an access key ID, a secret access key, and a security token. Typically, you use AssumeRole within your account or for cross-account access
- You cannot use AWS account root user credentials to call AssumeRole. You must use credentials for an IAM user or an IAM role to call AssumeRole.

**Example:** For cross-account access, imagine that you own multiple accounts and need to access resources in each account. You could create long-term credentials in each account to access those resources. However, managing all those credentials and remembering which one can access which account can be time consuming. Instead, you can create one set of long-term credentials in one account. Then use temporary security credentials to access all the other accounts by assuming roles in those accounts

#### AWS X-Ray :
- [AWS Reff Doc](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html)
- AWS X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter, and gain insights into that data to identify issues and opportunities for optimization. For any traced request to your application, you can see detailed information not only about the request and response, but also about calls that your application makes to downstream AWS resources, microservices, databases and HTTP web APIs.
- Instead of sending trace data directly to X-Ray, the SDK sends JSON segment documents to a daemon process listening for UDP traffic. The X-Ray daemon buffers segments in a queue and uploads them to X-Ray in batches. The daemon is available for Linux, Windows, and macOS, and is included on AWS Elastic Beanstalk and AWS Lambda platforms.
- X-Ray uses trace data from the AWS resources that power your cloud applications to generate a detailed service graph. The service graph shows the client, your front-end service, and backend services that your front-end service calls to process requests and persist data. Use the service graph to identify bottlenecks, latency spikes, and other issues to solve to improve the performance of your applications.
![AWS Xray](https://github.com/vurachaitanya/AWS/blob/master/images/AWS%20Xray.JPG)


#### AWS Simple Notification Service :
- [AWS Reff Doc](https://aws.amazon.com/sns/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc)
- Amazon Simple Notification Service is a notification service provided as part of Amazon Web Services since 2010. It provides a low-cost infrastructure for the mass delivery of messages, predominantly to mobile users.
- Fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.
- The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

#### AWS CloudTrail :
- [AWS Reff Doc](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)
- AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account. With CloudTrail, you can log, continuously monitor, and retain account activity related to actions across your AWS infrastructure. CloudTrail provides event history of your AWS account activity, including actions taken through the AWS Management Console, AWS SDKs, command line tools, and other AWS services. This event history simplifies security analysis, resource change tracking, and troubleshooting. In addition, you can use CloudTrail to detect unusual activity in your AWS accounts. These capabilities help simplify operational analysis and troubleshooting.
- 
