# A MISSING FRONT-END - CODEWHISPERER EDITION

## Overview

You work for a top-secret government intelligence agency called AnyCompany-GDI (Global Defense Initiative). An advanced
computer algorithm has been developed by in-house operatives that will find and output the encrypted coordinates of an
individual.

Discovered locations are typically generated and returned by this algorithm after an operative navigates to a specific
web URL. Unfortunately, after a recent cyber-attack on GDI itself, the front-end to this system has been destroyed! You
have been tasked with re-creating a front-end solution so the algorithm can once again be run and the important location
output can be accessed.

Note: You do not need front-end web development or programming experience to complete this challenge.

## Tasks

### Task 1: Fix the Lambda Function

#### Background

In order for the locations of individuals to be discovered, the coordinates application must be fixed. The backend is
still working and is transmitting the coordinates in an Amazon Simple Storage Service (S3) bucket to an object called
locationString.txt. The part of the application that has been destroyed is the frontend where the user should be able to
browse to a website and receive the content of the locationString.txt.

#### Your Task

An AWS Lambda function called individualFinder is already setup but has been corrupted during the latest cyber-attack on
GDI where some code has been removed.

Your task is to first fix the AWS Lambda function individualFinder written in Python. The function needs to read content
from an object locationString.txt within an Amazon Simple Storage Service (S3) bucket that is currently passed as the
environment variable bucketname. Those 2 have already been set as the variables bucket_name and filename.

In the section # Insert Code here, insert some code to read the content of the object and set it to the variable body.

Use Amazon CodeWhisperer to generate Python code in the AWS Lambda function to help you out. You don't need to write any
code yourself!

#### Getting Started

Your first step will be to open the AWS Lambda function in the AWS Console and activate code suggestion from Amazon
CodeWhisperer:

In the AWS Management Console, open the AWS Lambda service console.

* Locate the function individualFinder.
* In the Code tab, open the index.py file.
* From the Tools menu, choose Amazon CodeWhisperer Code Suggestions so that a checkmark appears next to it.
* You can now enter Python comments into this function and Amazon CodeWhisperer will suggest code. If Amazon
  CodeWhisperer
  doesn't supply a suggestion you can try triggering it with Alt + C on Windows or Option + C on MacOS. Press the Enter
  key to accept the suggestion.
* Try different comments to prompt CodeWhisperer to produce the necessary code.

##### Inventory

individualFinder AWS lambda function
Please ignore all other lambda functions as they are not required for this task.
Amazon Simple Storage Service (S3) bucket and object

Services You Should Use

* AWS Lambda
* Amazon CodeWhisperer

##### Task Validation

To complete the task, the AWS Lambda function must return the content of the file specified in the Lambda function.

After you complete the task the validator will automatically check for a successful execution of the Lambda Function.
You can manually trigger the validator by clicking the Check my progress button at the top of this page.

---

#### Task 2: Add a Trigger for Lambda

##### Background

Congratulations! The AWS Lambda function has been repaired! However, a web URL is needed to invoke the AWS Lambda
funtion on-demand from outside of the AWS Management Console. It is imperative that the front-end web access URL for the
algorithm's invocation be restored!

##### Your Task

Now that the AWS Lambda Function, individualFinder, has been repaired you need to create a way to invoke that function
from a web URL.

This task requires you to connect another AWS service to the AWS Lambda function as a trigger from within the Lambda
Function Page.

Consider what services are often used to invoke AWS Lambda, and which ones may expose public web URLs. We are looking
for another service than AWS Lambda Function URL as you can't use those here.

##### Getting Started

Navigate back to the individualFinder AWS Lambda function.
Configure the appropriate service.
Services You Should Use

* AWS Lambda
* Amazon CodeWhisperer
* Amazon API Gateway

##### Task Validation

To complete the task and the challenge, you will need to create a web URL that can invoke the Lambda Function from any
internet-connected computer.

After you complete the task, use that URL in your web browser to retrieve the code and supply it in as the answer to
this challenge.