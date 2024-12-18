# enable-bedrock-logging-using-cloudformation

## Name
enable-bedrock-logging-using-cloudformation

## Description
This AWS CloudFormation template enables the Model Invocation Logging in Amazon Bedrock. This template provisions required S3 buckets,
CloudWatch Logs Log Group, KMS key and custom CloudFormation resource backed by AWS Lambda to enable the Amazon Bedrock Model Invocation logging. 

## Architecture
![LoggingArchitecture](/Architecture.jpg)

AWS CloudFormation templates provisions necessary resources for Amazon Bedrock Invocation logging as follows:
+ AWS KMS Key for encryption of log data in S3 buckets and CloudWatch Logs Log group
+ S3 buckets for storage of model invocation logs and server side access logs
+ CloudWatch Logs Log Group for storage of model invocation logs
+ Service IAM role for Amazon Bedrock
+ Lambda Function to call Bedrock API as a custom resource to enable Bedrock Model Invocation logging
+ Lambda Function enables following logging configuration
    + Text Data Delivery
    + Image Data Delivery
    + Embedding Data Delivery
+ Enables logging to CloudWatch Logs Group and S3 bucket

## List of Resources Created
|   Resource Logical ID                         |   Resource Type                           |
| --------------------------------------------- | ----------------------------------------- |
|   rBedrockInvocationLogsBucket                |	AWS::S3::Bucket                         |
|   rBedrockInvocationLogsBucketPolicy          |	AWS::S3::BucketPolicy                   |
|   rBedrockLoggingKey                          |	AWS::KMS::Key                           |
|   rBedrockLoggingKeyAlias                     |	AWS::KMS::Alias                         |
|   rBedrockLoggingLambdaExecutionRole          |	AWS::IAM::Role                          |
|   rBedrockLoggingLambdaFunction               |	AWS::Lambda::Function                   |
|   rBedrockLogGroup                            |	AWS::Logs::LogGroup                     |
|   rBedrockServiceRoleForLogging               |	AWS::IAM::Role                          |
|   rBedrockServiceRoleForLoggingDefaultPolicy  |	AWS::IAM::Policy                        |
|   rInvokeLambda	                            |   AWS::CloudFormation::CustomResource     |
|   rServerAccessLogsBucket	                    |   AWS::S3::Bucket                         |
|   rServerAccessLogsPolicy	                    |   AWS::S3::BucketPolicy                   |

## License
Refer License.txt for licensing information

