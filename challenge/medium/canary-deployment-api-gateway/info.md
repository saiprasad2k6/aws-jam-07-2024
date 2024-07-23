# Canary Deployment API Gateway

## Overview

API Gateway supports Canary Release Deployments and you can use this deployment to gradually roll out new APIs in Amazon
API Gateway. The canary deployment is a process where you deploy a new software feature and shift some percentage of
traffic to new feature. This helps to reduce the risk of introducing a new software version in production by slowly
rolling out the change to a small subset of users before making it available to everyone.

In any development cycle, you can use canary when you want to deploy a version 1 to version 2 of your application and
shift a small amount of traffic to new version. We have also seen customers are using Amazon API Gateway a mechanism for
migrating traditional monolithic API to modern microservice based API.

Using canary you can shift portion of traffic to new backend. You can do it method by method basis. The same applies to
migrate an API from on-premises to AWS via private endpoint integration in Amazon VPC.

In this challenge, you will accomplish a canary release strategy for Rest API in Amazon API Gateway.

{ "year": "$input.path('$.Item.year.S')", "country": "$input.path('$.Item.country.S')", "winner": "$input.path('
$.Item.winner.S')" }

{ "year": "$input.path('$.Item.year.S')", "country": "$input.path('$.Item.country.S')", "winner": "$input.path('
$.Item.winner.S')","runners-up": "$input.path('$.Item.runners-up.S')" }

## Tasks

### Background

As an AWS developer your manager asks you to set up a new REST API at Amazon API Gateway. This returns three fields
“country”, "year”, “winner” information based on year as an input.

### Getting Started

Here is a reference you got that might help you find the
URL: https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html

Basic Amazon API Gateway knowledge is required to complete the task.

### Inventory

1 X REST API deployed at Amazon API Gateway.
1 X Amazon DynamoDB table.
Services you should use
Amazon API Gateway, Amazon DynamoDB.

### Task 1

#### Task Validation

Find Rest API name and then enter it back to the challenge answer!

#### Notes

Found the API Name and submitted

---

### Task 2

#### Task Validation

From a Browser tab, find the output of the Rest API for year "2014". Enter the exact json response from the output as
the answer.

Tips : You should append "2014" at the end of URL

#### Notes

Found the endpoint and hit the endpoint with 2014. Found the response and submitted the response.

### Task 3

#### Background

You receive a new requirement that necessitates a change to your Rest API application: the "runners-up" information
stored in Amazon DynamoDB must be included.

#### Getting Started

Here is a reference you got that might help you find the
URL: https://docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html
Basic Amazon API Gateway knowledge is required to complete the task.
Important note:
Please ignore the permission related warning/error while navigating the API in the console.

#### Task Validation
Enter the value of the "runners-up" key from REST API json output after promoting the Canary version.

#### Notes
Added "runners-up" in the response mapping of the API Gateway Integrations. 