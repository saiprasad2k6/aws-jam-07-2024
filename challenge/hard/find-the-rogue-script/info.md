# FIND THE ROGUE SCRIPT

## Overview

One of your EC2 web servers has been compromised by an insider! A rogue script is invoking many AWS APIs. Find the
instance and isolate it using automation, so you can investigate later. You will use services like Amazon EC2, AWS
CloudTrail, AWS Athena and AWS Lambda.

## Summary

Our e-commerce web site has gone viral! Who would have thought that selling organic jeans would have so much demand! But
something is wrong.

A CloudWatch Alarm is warning about unauthorized activity. One of the e-commerce web servers seems to be compromised. It
is invoking many AWS APIs. We're worried that someone on the development team has leaked credentials with authority to
deploy scripts on our web servers. You need to find the instance running a rogue script and isolate it using automation.
We assume forensics will be performed later.

Instance isolation for forensics involves a few steps:
* Disconnect the web server from the application load balancer. 
* Allow inbound traffic ONLY from the forensics EC2 instance. 
* Block all outbound traffic originating from the compromised instance.

## Objectives
Identify the compromised instance. Thankfully, we have a CloudWatch Alarm Unauthorized Activity Attempt monitoring
unauthorized access attempts.
* You need to isolate the compromised instance using automation. You should modify and extend the InstanceIsolater Lambda
function that is provided. 
* You will need to SSH into the compromised instance. Remember you can only reach it from the forensics EC2 instance that
has been provided. None of the web server EC2 instances SSH access from anywhere else. 
* Identify and inspect the rogue script to find the challenge answer.

## Inventory
The following resources have been provisioned for you. Make sure you review them before you start hacking. Pay special
attention to security groups.

* 2 web server instances 
* 1 Application Load Balancer 
* 1 forensics EC2 instance

Some security groups 
* 1 CloudWatch Alarm named Unauthorized Activity Attempt 
* 1 Lambda function named InstanceIsolater 
* 1 AWS CloudTrail trail delivering log files to a S3 bucket.


