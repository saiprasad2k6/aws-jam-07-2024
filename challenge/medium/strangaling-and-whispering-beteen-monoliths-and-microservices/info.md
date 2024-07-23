# STRANGLING AND WHISPERING BETWEEN MONOLITHS AND MICROSERVICES

## Overview
You work for a company that has an online store for purchasing their products. This online store is backed by a huge
monolithic application. Your team is concerned that this application will not scale to support your company's current
growth trajectory. The team decided to break down this monolith into a set of microservices to support the expected
scale.

After doing some research, your team chose the Strangler pattern to handle the migration from monolith to microservices.
In the Strangler pattern, you gradually replace specific parts of the monolith functionality with new microservices. You
create a facade that intercepts the requests going to the monolith application. Then you use the facade to route the
requests either to monolith or microservice.

Your team started building microservices. They picked the products feature of monolith and migrated it into a dedicated
microservice.

Now it's time to build the facade that can help route the traffic between monolith and 'products' microservice. The same
facade will be used to transition others features of monolith in future when they are migrated to dedicated
microservices. As the AWS expert of the team, you have been tasked to build this facade to start migrating traffic from
monolith to microservices.

## Tasks

### Task 1: Configure API Gateway to route all calls to monolith application

#### Background
You have been provided access to an AWS account in which the monolith application and products microservice have been
deployed. You did some research and chose Amazon API Gateway to build the facade because it allows you to create an API
endpoint and route calls for different resources to different backend integrations. You notice that a REST API named
ecommerce-api which points to a mock service is provisioned for you on the Amazon API Gateway.

You will use the Amazon Web Services (AWS) SDK for Python or boto3 to write code to update the ecommerce-api.

But wait, no need to write this on your own! You will be using Amazon CodeWhisperer, a machine-learning powered service
that helps improve developer productivity by generating code recommendations based on developers’ comments in natural
language. You will use Amazon CodeWhisperer with AWS Cloud9 as your Integrated Development Environment (IDE).

#### Getting Started
A rundown of assets you can work with:

Click on Console (in the top right corner), and go to the AWS API Gateway Console. You will see two APIs: 1)
ecommerce-api and 2) product-catalog-api. The ecommerce-api already has one ANY method for mock integration created by
default.

In the Output Properties (menu on the left), you will use the IDs below when writing your code.

ECommerceMonolithRestApiId - The REST API ID of the ECommerce monolith application.
ECommerceMonolithResourceId - The Root Resource ID of the ECommerce monolith application.
Additionally, be familiar with the root endpoint as you will also need this to write your code.

MonolithRootEndpoint - The root endpoint of the monolith application.
To start working with Amazon CodeWhisperer in AWS Cloud9:

Follow the instructions under Solving Methods Info > Using CodeWhisperer (left navigation menu).
In AWS Cloud9, begin writing code comments depicting the tasks you want to achieve (more on the tasks later). To see
generated code suggestions from Amazon CodeWhisperer, you may press Option + C (in macOS) or Alt + C (in Windows) in the
AWS Cloud9 editor. Please refer to User Actions for more keyboard shortcut options.
Run your Python script in AWS Cloud9, and check your progress.
Your Task
Your task is to update the ecommerce-api REST API to route all the calls to the monolith application.

Using the boto3 code generated by Amazon CodeWhisperer:

Firstly, delete the existing ANY method (pointing to the mock integration), and
Secondly, create a new resource to setup up proxy integration with the monolith endpoint.
After the API is configured, you should be able to access the products and customers endpoints through the prod stage of
ecommerce-api REST API endpoints with the following URLs:

https://<ECommerceMonolithRestApiId>.execute-api.us-east-1.amazonaws.com/prod/ecommerce/products, and
https://<ECommerceMonolithRestApiId>.execute-api.us-east-1.amazonaws.com/prod/ecommerce/customers
Inventory
Recalling the assets already pre-generated for you from the Output Properties menu:

ECommerceMonolithRestApiId - The REST API ID of the ECommerce monolith application.
ECommerceMonolithResourceId - The Root Resource ID of the ECommerce monolith application.
MonolithRootEndpoint - The root endpoint of the monolith application.
For reference, you can also take a look at the product and customer endpoints of the monolith application:

MonolithProductsEndpoint - The products endpoint of the monolith application.
MonolithCustomersEndpoint - The customers endpoint of the monolith application.

#### Services you should use
* Amazon API Gateway 
* AWS Systems Manager Parameter Store 
* Amazon CodeWhisperer 
* AWS Cloud9 
* Additional Resources 
  * Developing a REST API in API Gateway
  * Boto3 documentation for API Gateway

#### Task validation
The task will be automatically marked as complete once you correctly configure the proxy integration to invoke the
monolith endpoint. Alternatively, you may click the Check my progress button to check the completion status.
---
### Task 2: Update API Gateway to route 'products' calls to microservice

#### Background
After finishing Task 1, you have an API gateway that routes all calls to monolith application. It's time to 'strangle'
the products feature off of the monolith application. You want to achieve this by splitting the traffic between monolith
application and products microservice using this API gateway.

Your team is ready with the products microservice. This microservice is implemented as a Lambda function and is deployed
for you.

#### Your Task
Your task is to configure the REST API to split the traffic between monolith and microservice. You are expected to
update the ecommerce-api REST API to route all traffic coming to products resource to the products microservice;
essentially routing all traffic heading to `https://<ECommerceMonolithRestApiId>
.execute-api.us-east-1.amazonaws.com/prod/ecommerce/products` endpoint to the productcatalogfunction Lambda function.

The API should continue to route rest of the traffic to monolith.

#### Getting started
Navigate to AWS Lambda Console and review the products microservice implemented by Lambda function which contains
`productcatalogfunction` as part of its name.
On the API Gateway console, start updating the ecommerce-api to create ecommerce resource and products child resource
and integrate with products service.

#### Inventory
From the Output Properties menu:
* ECommerceMonolithRestApiId - The REST API ID of the ECommerce monolith application. 
* ECommerceMonolithResourceId - The Root Resource ID of the ECommerce monolith application. 
* ProductCatalogLambdaInvocationUri - The Lambda Invocation URI of the products microservice that is deployed to your AWS
account. This is implemented as a Lambda function which has productcatalogfunction in its name. 
* ProductCatalogInvokeLambdaRoleArn - The ARN of the IAM Role to allow API Gateway to invoke the Product Catalog Lambda
function. For reference, you can also take a look at the product and customer endpoints of the monolith application:
* MonolithProductsEndpoint - The products endpoint of the monolith application. 
* MonolithCustomersEndpoint - The customers endpoint of the monolith application.

#### Services you should use
* Amazon API Gateway 
* Amazon CodeWhisperer 
* AWS Cloud9 
* Additional Resources 
  * Developing a REST API in API Gateway 
  * Boto3 documentation for API Gateway 

#### Task validation
The task will be automatically marked as complete once you correctly split the traffic between products microservice and
monolith application using the ecommerce-api REST API. Alternatively, you may click the Check my progress button to
check the completion status.