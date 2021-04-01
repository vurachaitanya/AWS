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

