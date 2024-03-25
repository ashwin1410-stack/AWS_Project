# Lambda Function for S3 Event Processing and DynamoDB Interaction

### Introduction:-
The Lambda function described in this documentation is designed to be deployed as an AWS Lambda handler. Its primary purpose is to process events triggered by Amazon S3 object creations and updates. Subsequently, it extracts metadata from these events and stores it in a DynamoDB table for further analysis or retrieval. This documentation provides a comprehensive guide on setting up, configuring, and utilizing this Lambda function.

### **Prerequisites:-**
Before deploying the Lambda function, ensure the following prerequisites are met:

- An active AWS account with appropriate permissions to create and manage Lambda functions, S3 buckets, and DynamoDB tables.
- Basic knowledge of Python programming language and AWS services including Lambda, S3, and DynamoDB.
- Access to the AWS Management Console or AWS CLI for deploying and configuring resources.
### Setup:-  
**Create a new Lambda Function:**

- Log in to the AWS Management Console.
- Navigate to the Lambda service.
- Click on "Create function" and choose "Author from scratch".
- Configure the function details including name, runtime (Python), and execution role with necessary permissions.
**Configure Trigger:**

- Add an S3 trigger to the Lambda function.
- Select the desired S3 bucket and event types for best practice select all (PUT,POST,COPY etc)
**Configure Environment Variables:**

- Define environment variables for specifying the DynamoDB table name and other configurations required by the Lambda function.
### **Implementation:-**
Implement the Lambda function with the following logic:

- Extract metadata from S3 events (e.g., bucket name, object key, event type, event time).
- Initialize a connection to the DynamoDB table using the AWS SDK (boto3).
- Store the extracted metadata in the DynamoDB table using appropriate API calls (e.g., put_item).
```
﻿import boto3
from uuid import uuid4

def lambda_handler(event, context):
    s3 = boto3.client("s3")
    dynamodb boto3.resource('dynamodb')
    
    for record in event['Records']:
        bucket_name = record ['s3'] ['bucket']['name']
        object_key = record ['s3']['object']['key']
        size = record['s3'] ['object'].get('size', -1)
        event_name = record['eventName']
        event_time = record ['eventTime']


dynamo_table dynamodb. Table('ash1410') # Replace 'tablel' with your actual DynamoDB table name

dynamo_table.put_item(

Item={
      'unique': str(uuid4()),
      'Bucket': bucket_name,
      'Object': object_key,
      'Size': size,
      'Event': event_name,
      'EventTime': event_time }
)
```
### Deployment:-
Deploy the Lambda function to your desired environment (e.g., development, production) using AWS CLI or AWS Management Console. Ensure that necessary permissions are granted to the Lambda function to interact with S3 and DynamoDB.

### Security:-
Ensure the security of your Lambda function and data by implementing best practices such as:

- Applying least privilege IAM roles and policies.
- Encrypting sensitive data at rest and in transit.
- Perform routine maintenance tasks such as updating the function code, adjusting memory allocation, and reviewing IAM permissions.
### Conclusion:-
The Lambda function described in this documentation provides a scalable and efficient solution for processing S3 events and storing metadata in DynamoDB. By following the guidelines outlined here, you can successfully deploy, configure, and maintain the Lambda function to meet your specific requirements for event-driven architectures.

This documentation serves as a comprehensive guide for utilizing the Lambda function to process S3 events and interact with DynamoDB effectively, enabling seamless integration within AWS environments.

