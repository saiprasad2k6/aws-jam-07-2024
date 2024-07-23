# Background

Dyna Inc. sells high-quality pet food, toys, and play areas for the pet dinosaurs of its discerning clientele. Dyna Inc.
has the largest market share in this space with loyal customers that love their dinosaurs and want only the best for
them. Unfortunately, in recent years, competition from low-cost retailers has been fierce.

Dyna Inc. does not want to reduce prices by compromising on quality. Instead, they want to hold exclusive events and
provide deep discounts in some categories for their most valuable customers. To do this, Dyna Inc. should be able to
identify "Elite" customers who have spent $1,000 or more with Dyna Inc.

In fact, it would be great if they can congratulate a customer and provide them the "Elite" card as soon as the customer
completes the qualifying transaction.

A developer at Dyna Inc. performed an analysis and started working on achieving this. That developer has since left Dyna
Inc. and did not have time to provide a full transition. As an AWS specialist, you have been brought in to help complete
the business use case.

Dyna Inc. has already scheduled the first exclusive event, but they can't figure out who to invite. If the event fails,
it would mean a waste of their entire year's marketing budget. They are looking to you to enable them to identify the "
Elite" customers quickly so they can start sending out invites.

# Task 1

Task 1: Complete Lambda to Update Customer Profile
Possible Points: 90 Clue Penalty: 0 Points Available: 90
BACKGROUND:
The documents left behind by the developer indicate that the two Amazon DynamoDB tables below can be leveraged to
achieve the business goal.

Table Name Description
CustTransactions Stores all customer transactions
CustProfile Stores customer profiles
------------------------	--------------------------------
In the CustProfile table, the developer added two additional fields to capture the total spend of a customer and the
corresponding Customer Status - "Normal" or "Elite".

The developer also started working on a Lambda function named JAM_Lambda_Exec_Function_EDIT_THIS, that will accept
changes to the CustTransactions table as an event and update the CustProfile table. The Lambda function is missing some
code, and the developer helpfully added the comment "YOUR CODE GOES HERE" to where you need to fill in the details to
get the function running.

YOUR TASK:
As a first step, you have to complete the AWS Lambda function to update the total transaction value and customer status
in the CustProfile Amazon DynamoDB table whenever the customer makes a new transaction. The Inventory section below
provides the name of the Lambda function and the schema of the DynamoDB tables. Use this information to complete the
task. Once you update the Lambda function, you will use the test event in the Task Validation section below to test the
function.

TASK VALIDATION:
Once you complete the Lambda function by filling in the missing code, test the function with the sample event below:

```json
{
  "Records": [
    {
      "eventName": "INSERT",
      "eventSource": "aws:dynamodb",
      "dynamodb": {
        "Keys": {
          "CustID": {
            "S": "task1test1record"
          },
          "TnValue": {
            "N": "250"
          }
        }
      }
    }
  ]
}
```

Once you successfully test the lambda, it will be verified automatically and the task will be marked as complete within
a few minutes.

INVENTORY:

Lambda Function:

JAM_Lambda_Exec_Function_EDIT_THIS

CustTransactions Table Schema:

Field Type Description
CustID string Unique identifier for customer
TnNum integer Unique identifier for transaction
TnValue integer Dollar value of transaction
-------------	-----------	--------------------------------

CustProfile Table Schema:

Field Type Description
CustID string Unique identifier for customer
TotalTnValue integer Total Dollar value of all customer spend
CustStatus string Normal / Elite
-------------------	-----------	--------------------------

GETTING STARTED:
Go to the AWS Lambda console. If you don't see a list of Lambda Functions, click on Services in the top-left of the
console and choose Lambda to see the list of Lambda Functions.

Do the same if the list of Lambda Functions disappears at some point. This may occur because the Jam User's Team Role is
blocked from accessing the task verification Lambda Functions.

SERVICES YOU SHOULD USE:
AWS Lambda

#### Task 1: Complete Lambda to Update Customer Profile

BACKGROUND:
The documents left behind by the developer indicate that the two Amazon DynamoDB tables below can be leveraged to
achieve the business goal.

Table Name Description
CustTransactions Stores all customer transactions
CustProfile Stores customer profiles
------------------------	--------------------------------
In the CustProfile table, the developer added two additional fields to capture the total spend of a customer and the
corresponding Customer Status - "Normal" or "Elite".

The developer also started working on a Lambda function named JAM_Lambda_Exec_Function_EDIT_THIS, that will accept
changes to the CustTransactions table as an event and update the CustProfile table. The Lambda function is missing some
code, and the developer helpfully added the comment "YOUR CODE GOES HERE" to where you need to fill in the details to
get the function running.

YOUR TASK:
As a first step, you have to complete the AWS Lambda function to update the total transaction value and customer status
in the CustProfile Amazon DynamoDB table whenever the customer makes a new transaction. The Inventory section below
provides the name of the Lambda function and the schema of the DynamoDB tables. Use this information to complete the
task. Once you update the Lambda function, you will use the test event in the Task Validation section below to test the
function.

TASK VALIDATION:
Once you complete the Lambda function by filling in the missing code, test the function with the sample event below:

```json
{
  "Records": [
    {
      "eventName": "INSERT",
      "eventSource": "aws:dynamodb",
      "dynamodb": {
        "Keys": {
          "CustID": {
            "S": "task1test1record"
          },
          "TnValue": {
            "N": "250"
          }
        }
      }
    }
  ]
}
```

Once you successfully test the lambda, it will be verified automatically and the task will be marked as complete within
a few minutes.

INVENTORY:

Lambda Function:

JAM_Lambda_Exec_Function_EDIT_THIS

CustTransactions Table Schema:

Field Type Description
CustID string Unique identifier for customer
TnNum integer Unique identifier for transaction
TnValue integer Dollar value of transaction
-------------	-----------	--------------------------------

CustProfile Table Schema:

Field Type Description
CustID string Unique identifier for customer
TotalTnValue integer Total Dollar value of all customer spend
CustStatus string Normal / Elite
-------------------	-----------	--------------------------

GETTING STARTED:
Go to the AWS Lambda console. If you don't see a list of Lambda Functions, click on Services in the top-left of the
console and choose Lambda to see the list of Lambda Functions.

Do the same if the list of Lambda Functions disappears at some point. This may occur because the Jam User's Team Role is
blocked from accessing the task verification Lambda Functions.

SERVICES YOU SHOULD USE:
AWS Lambda

#### Task 2: Automate the Updation of Customer Profile

##### BACKGROUND:

Congratulations! You have completed the AWS Lambda function which can update the CustProfile table in the Amazon
DynamoDB in near real-time whenever the customer makes a transaction. However, we are not done yet.

Next, the Lambda function must be automatically triggered whenever the customer completes a new transaction so that the
customer profile can be updated immediatly.

Once we achieve this, a customer's profile status will be automatically updated to Elite upon making a qualifying
transaction. Subsequently, the front-end staff will then be able to present the customer with a shiny new Elite member's
card, accompanied by an invite to the exclusive event.

You're thrilled at the prospect of contributing to customer delight and get cracking right away to trigger the Lambda
function whenever an item is inserted in the CustTransactions Amazon DynamoDB table.

##### YOUR TASK:
You must make the required changes to automatically trigger the AWS Lambda function, JAM_Lambda_Exec_Function_EDIT_THIS,
whenever an item is inserted into the Amazon DynamoDB CustTransactions table.

##### TASK VALIDATION:
Once you enable the Lambda function to be triggered when an item is added to the CustTransactions DynamoDB table, the
verification will be completed automatically, and the task will be marked complete.

Note: Based on the parameters you choose, it might take a few minutes for the Lambda function to be triggered and for
the verification process to confirm the completion of the challenge.

##### INVENTORY:

Lambda Function:

JAM_Lambda_Exec_Function_EDIT_THIS

CustTransactions Table Schema:

Field Type Description
CustID string Unique identifier for customer
TnNum integer Unique identifier for transaction
TnValue integer Dollar value of transaction
-------------	-----------	--------------------------------

CustProfile Table Schema:

Field Type Description
CustID string Unique identifier for customer
TotalTnValue integer Total Dollar value of all customer spend
CustStatus string Normal / Elite
-------------------	-----------	--------------------------


##### SERVICES & FEATURES YOU SHOULD USE:
* AWS Lambda 
* Amazon DynamoDB Streams
