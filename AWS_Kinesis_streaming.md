## AWS Kinesis Streaming

-	Kinesis is a streaming ingestion tool for logs an Analytics.
-	Kinesis can be integrated with any application using 
-	-  Amazon Kinesis Agent
-	- Amazon Kinesis producer library 
-	-  AWS SDK’s
-	To AWS Kinesis Data streams
-	Further can be sent to 
-	-  AWS Kinesis Data Analytics
-	-  AWS Kinesis Consumer library – (Java)
-	-  AWS Kinesis Data Frames 
![AWS Kinesis Flow](https://github.com/vurachaitanya/AWS/blob/master/images/AWS%20Kinesis.png)
-	 Kinesis data streams – Collect and store data streams for analytics
-	Kinesis data Firehose – Load data streams into AWS Data stores (like S3, AWS Elastic search, Splunk) for buffering and adding some data functions for data transformation operations.  
-	Kinesis Data Analytics – Analyze data streams with SQL or Java
-	Kinesis Video Streams – Capture and store video streams for analytics.
-	Kinesis Data Streams = Kafka streaming (Data Producer vs Consumers)
-	-  data consumes up to 1 MB or 1000 records per seconds, per shard.
-	- GetRecords(): 5 transactions per seconds per shard.
-	-  Data: 2MB per Second per shard.
-	- if multiple consumers are there 400 KBps transaction.
![Kinesis Data Stream Flow](https://github.com/vurachaitanya/AWS/blob/master/images/Kinesis%20data%20Streams.JPG)
-	`aws kinesis register-stream-consumer –stream-arn`
-	**Glue Data Catalog** -- Convert to columnar format.

### Terraform resources blocks
##### [kinesis_stream](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kinesis_stream#example-usage)
##### [aws_kinesis_analytics_application](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kinesis_analytics_application#kinesis-stream-input)
##### [aws_kinesis_firehose_delivery_stream](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kinesis_firehose_delivery_stream#example-usage)



## Kinesis Demo for EC2 logs to data stream
[Reff video](https://www.youtube.com/watch?v=ZErwfH-OLk4)
-	Kinesis-demo: For EC2 instance we add Role with S3 + Kinesis full access 
-	Kinesis-demo : group created with (S3,Kinesis full access)
-	kinesis-demo: user created with programmatical access. With kinesis-demo as group
-	Create EC2 instance with linux free tier + t2 micro.
-	EC2 Image = ami-0742b4e673072066f (64-bit x86) in N.Virginia
-	EC2 instances created : i-0bfc433d9caeec998
-	Create Kinesis Data streams with kinesis-demo name and 1 shards.
-	Create kinesis Firehose to push the data to data streams from EC2
-	Kinesis-demo Firehose is created with kinesis-demo1 data streams inputs.
-	Create S3 bucket to store data pushed to kinesis streamskinesis firehose to  S3 bucket. In N.Virginia - kinesis-demo12331
-	Using Cloud shell connect to EC2 instances. ssh -i "kinesis.pem" ec2-user@ec2-54-160-52-121.compute-1.amazonaws.com
-	Copy pem keys in cloud shell and connect to EC2 instance.
-	Install kinesis agent on EC2 instance from the link: https://docs.aws.amazon.com/firehose/latest/dev/writing-with-agents.html
-	Install latest version of agent : sudo yum install –y https://s3.amazonaws.com/streaming-data-agent/aws-kinesis-agent-latest.amzn2.noarch.rpm
-	/etc/aws-kinesis/agent.json is configuration file for pushing the data.
-	Mkdir /var/log/weather – Landing location for pushing the files.
-	Mkdir /root/data; git clone https://github.com/manish9363/AWS.git
-	Head -20 city_temperature_data_stream.csv >first.log
-	Cp first.log /var/log/weather/
-	Get the configuration files from and update with Access key ID & Secret access key: https://raw.githubusercontent.com/manish9363/AWS/master/agent_template.txt
-	Update the agent.json file in /etc/aws-kinesis location.
-	Start the Agent : ./etc/init.d/aws-kinesis-agent start && ps -ef|grep kinesis
-	Logs can be checked from tail aws-kinesis-agent.log

#### Deleting : 
1.	Delete EC2 instance
2.	Delete S3 instance
3.	Delete Kinesis Data stream
4.	Delete kinesis Firehose – Automatically 
5.	Delete VG attached to EC2 instance. – slowly it deletes the data
