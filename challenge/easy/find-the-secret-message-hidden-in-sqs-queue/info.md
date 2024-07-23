# Find the Secret Message Hidden in SQS Queue

## Overview

You are a DevOps Engineer at a Multi-National company, ABC Limited. Recently, there was a security audit and the auditor
found that few of the AWS Lambda functions are not deployed in a VPC. As per your Organisation's security guidelines,
all AWS Lambda functions should be in a secured environment. Hence, it is a security violation and your team of AWS
Experts need to re-configure and deploy all the lambda functions in a VPC. Also, we need to make sure that any existing
functionality is not broken as there is a customer demo next week.

A member of your team has been assigned this task and they have re-configured the lambda functions within AWS VPC.
However, due to an emergency your team member has to take leave before fully testing the application. The Application
team is getting ready for demo and during dry run found issues with Lambda function. Your manager has reached out to you
for your help in completing this task before customer demo. Ready to Dive in?

## Tasks

### Task 1: Why Lambda Function is getting timed Out ?

#### Background

The application team complained that they are receiving timeouts from Lambda function. You verified that the lambda is
deployed within VPC by your colleague. But, when you test the Lambda function via console, the execution fails with an
error Task timed out after 3.01 seconds. You suspect an issue with VPC Endpoint configuration created to interact with
AWS SQS.

#### Task

#### Background
Verify the VPC Endpoint and apply appropriate security configuration, following LEAST privilege principle.

#### Inventory
The following resources have been provisioned for you to successfully attempt the challenge:

* AWS Lambda(Jam-Challenge-Lambda)
* AWS VPC(JAM-Challenge)
* SQS VPC endpoint
* AWS Security Group
    * Security group for SQS VPC endpoint(endpoint-sg)
    * Security group for Lambda function(lambda-sg)

#### Getting Started

1. Understand about VPC endpoint
2. How to create interface VPC endpoints
3. How to configure a Lambda function in a VPC to access AWS Services
4. Getting started with AWS Lambda
5. How to test AWS Lambda function using AWS Console

Note:

1. In order to execute and test the lambda function, create a sample test event.

#### Validation

The task will be automatically completed once you find the solution. You can always check your progress by pressing the
“Check my progress” button in the challenge details screen.

#### Notes

Modified the VPC Endpoint Access Policy to ensure that the SQS is able to be reached.
---

### Task 2

#### Background
After successfully updating the VPC Security configuration, we executed the lambda, but it it is now failing with an
error when calling the GetQueueUrl operation: The specified queue does not exist or you do not have access to it. The
application (lambda function) polls(receives) messages from SQS queue(Jam-Challenge-Queue) and processes it.

#### Task
To complete this task, you need to ensure that IAM role attached to lambda function has sufficient permissions to
perform basic operations on SQS queue and get details about SQS queue. Please remember to follow LEAST privilege
principle while adding/updating any permissions to existing policy.

#### Note:

To validate AWS Lambda function, after making necessary changes in IAM Policy please execute it.
If Least privilage policy is not given then Task validation will fail.
IAM policy attached AWS Lambda function can be updated to add additional permissions.
Inventory
The following resources have been provisioned for you to successfully attempt the challenge:

* AWS Lambda function (Jam-Challenge-Lambda)
* Amazon SQS Queue (Jam-Challenge-Queue)
* IAM Role (Jam-Challenge-Role)

#### Getting started
* Check the IAM permissions attached to IAM role Jam-Challenge-Role. 
* Refer how to use identity-based policies with Amazon SQS.

 
#### Task Validation
The task will be automatically completed once you find the solution. You can always check your progress by pressing the
“Check my progress” button in the challenge details screen.

#### Note:

* Please review the lambda function code and add only necessary permissions required as used in the function. 
* To complete the task, you have to execute the AWS Lambda function using sample test event. 
* Please adhere to least privilage IAM policy. 
* Ignore IAM Access Analyzer related errors on AWS IAM Console when you update the IAM policy. 
* SQS resource based policy is out of scope for this challenge.

#### Solution
Added permissions in the Lambda execution role for SQS Access - Read, List etc.