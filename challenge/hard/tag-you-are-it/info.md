# Tag You are it

## Overview

You're the IAM Administrator and your job is to separate the actions that two Project Teams, Green and Red, can take on
EC2 Instances in an AWS Account.

* To successfully complete this challenge, you will need to craft an IAM Policy Document that separates the permissions
  of
  the two Roles: `ProjectGreenRole` and `ProjectRedRole` so that the `ProjectGreenRole` can Run,
  Stop and Start EC2 Instances tagged with Project = Green and ProjectRedRole can do the same with EC2 Instances tagged
  with Project = Red.
* You must also ensure that these Roles can't change tags on EC2 instances after launch

## Background

You are the IAM Administrator for your AWS Accounts. You have two Projects: Red and Green that are launching and
managing EC2 Instances in the same AWS Account.

Your AWS Account has the following resources:

Two IAM Roles:

* `ProjectRedRole` tagged with Project = Red
* `ProjectGreeRole` tagged with Project = Green

Two EC2 Instances:

* Red instance tagged with Project = Red
* Green instance tagged with Project = Green
* A Managed Policy: 'ManageEC2InstancesWithProjectTag' that is attached to the ProjectRedRole and ProjectGreenRole. This
  is overly permissive to start with and does not have any IAM Conditions for the Actions.

## Requirements

Your job is to edit this policy document to meet the following three requirements:

* Restrict EC2 StartInstances & StopInstances actions to EC2 Instances with Project tag values corresponding to the
  Roles
  ProjectGreenRole and ProjectRedRole.
* Allow EC2 RunInstances only if the EC2 Instances and Volumes are tagged on creation with Project tag values
  corresponding to the Roles ProjectGreenRole and ProjectRedRole. Ensure that the only tag key allowed on creation is '
  Project' with an exact case match.
* Ensure that tags cannot be changed on EC2 Instances and Volumes after creation.
  Hint: it may help to save a copy of the original policy document before you make changes so you can always go back and
  start over.

## Getting Test Results

After saving changes to the Managed Policy wait 20 seconds and browse to or refresh the VerifierUri from the Output
Properties. This page displays results of test cases for the above requirements (green means the test passed, red means
the test failed). When all tests pass you'll get the Challenge Answer at the bottom of the same page.

## Helpful Links
Here are a few links to help you with the challenge:

Actions, Resources and Condition Keys for Amazon EC2
AWS Global Condition Context Keys
Example IAM Policies for EC2 RunInstances with Tags