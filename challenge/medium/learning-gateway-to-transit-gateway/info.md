# LEARNING GATEWAY TO TRANSIT GATEWAY

## Overview

You are a network administrator of MyTCPPackets Company, which has multiple Amazon Virtual Private Cloud (Amazon VPC)
architectures. For inter-VPC communication, you were using VPC peering. You learned that AWS Transit Gateway solves the
problem of transitive peering (you can find more information about transitive peering in this link), and you wanted to
implement the concepts of AWS Transit Gateway using two test VPCs.

As a proof of concept to the leadership team, you deployed two VPCs with all networking components and AWS Transit
Gateway using AWS CloudFormation. You have one Amazon Elastic Compute Cloud (Amazon EC2) instance deployed in the
private subnets of both VPCs and a bastion host deployed in the public subnet of VPC1.

After deploying the resources, you noticed the following issues.

You cannot SSH into the bastion host and then into the private subnet instance of VPC1.
EC2 instances in the private subnets of VPC1 and VPC2 cannot ping one another.
You should resolve the issues and establish connectivity between the two VPCs using AWS Transit Gateway. Are you up for
the challenge?

Architecture Diagram:
Link to Architecture Diagram
Note: please refer to the challenge inventory section in task 1 for the challenge inventory.

Services you should use:

* Amazon EC2
* Amazon VPC
* AWS Transit Gateway

## Tasks

### Task 1: Remove Virtual Firewall blocks for the Packets!!!

#### Background:

As per the initial setup, you noticed that something is preventing you from accessing EC2 instances. As a network
administrator of MyTCPPackets Company, you must clear the blocks so that the EC2 instances can communicate.

To complete the task, you need to update three security groups. Two security groups will be in VPC1 and the other in
VPC2.

You should accomplish the following:

* Ping the VPC1 bastion host from your local workstation. You can find the public IP address of the bastion host in the
  Output Properties tab to the left of these instructions.
* SSH into the VPC1 bastion host using the credentials provided in the Getting Started section.
* Ping VPC1 private subnet instance (10.0.2.x) from the bastion host (10.0.1.x).
* SSH into the VPC1 private subnet instance (10.0.2.x) from the bastion host (10.0.1.x) using the credentials provided
  in
  the Getting Started section. Although you won't be able to ping the private subnet instance in VPC2 (192.168.0.0/16)
  yet, ensure the VPC2 private
  subnet EC2 instance security group is appropriately configured to allow the private instance in VPC1 to ping this
  instance.
* Once complete, this task will allow you to SSH into the VPC1 bastion host in VPC1 using the public IP of the host and
  then into the VPC1 Private Subnet Instance (10.0.2.x).

#### Challenge inventory

* VPC1 (10.0.0.0/16):
* Public subnet(10.0.1.0/24)
* Public subnet route table
* Internet Gateway
* Private subnet (10.0.2.0/24)
* Private subnet route table
* Bastion host (10.0.1.x)
* Bastion host Security Group
* Private subnet EC2 instance (10.0.2.x)
* Private subnet EC2 instance security group
* VPC2 (192.168.0.0/16):
* Private subnet (192.168.2.0/24)
* Private subnet route table
* Private subnet EC2 instance (192.168.2.x)
* Private subnet EC2 instance security group
* Transit Gateway
* VPC1 Transit Gateway attachment
* VPC2 Transit Gateway attachment
* Transit Gateway route table

#### Getting started

Things you should CONSIDER doing:
Use VPC CIDR, subnet CIDR, or instance private IP addresses in security group ingress rules and route table entries.

Things you should AVOID doing:

* As per best practices, using All-Traffic in the ingress rules of security groups is prohibited.
* As per best practices, using zero-CIDR (0.0.0.0/0) is prohibited in the ingress rules of all security groups.
* As per best practices, using All TCP ports in the ingress rules of all security groups is prohibited.
* The automatic task validation script will verify adherence to these best practices throughout the challenge. Any
  non-compliance will result in the task not being marked completed.
* SSH into VPC2 private subnet instance (192.168.2.x).
* You can reference this documentation link to find out how to add ingress rules to Security Groups.

NOTE: You don't need to use a key pair to log into any EC2 instance in this challenge. A local account has been created
in all VPC1 instances. The credentials can be found in the SSH instructions below.

#### SSH instructions

Use the information below to SSH into the bastion host EC2 instance using its public IP address. The public IP address
of the bastion host can be found in the Output Properties tab to the left of these instructions.

#### Credentials

Username: participant
Password: tgw123

For Mac users
To SSH into the Bastion host, Open the Terminal application and connect to the bastion host using the following SSH
command. Note: You must replace bastion_host_public_ip with public IP of bastion host.

> ssh participant@{bastion_host_public_ip}
> Upon successful login to the Bastion host, SSH into the VPC1 Private Subnet Instance (10.0.2.x) using the below command
> in bastion host terminal. Note: You must replace vpc1_private_subnet_instance_private_ip with private IP of the EC2
> instance in VPC1 private subnet (i.e. 10.0.2.x).

> ssh participant@{vpc1_private_subnet_instance_private_ip}
> For Windows users
> To SSH into the bastion host, you must use a client such as PuTTY. If this is not installed on your computer, you must
> download and install one. Check your policies to ensure this is allowed if you use a company computer.

Once you download and install PuTTY, start the application.

In the Category pane, choose Session and complete the following fields:

> Enter participant@{bastion_host_public_ip} as the host, Note: You must replace the bastion_host_public_ip with public
> IP
> of bastion host.

Ensure that the Port value is 22.

> Under Connection type, select SSH.

> Click Open button

For more details, please refer to the Connecting to your Linux instance section in the AWS documentation.

> Upon successful login to the Bastion host, SSH into the VPC1 Private Subnet Instance (10.0.2.x) using the below
> command
> from Bastion host. Note: You must replace vpc1_private_subnet_instance_private_ip with private IP of the EC2 instance in
> VPC1 private subnet (i.e. 10.0.2.x).

> ssh participant@{vpc1_private_subnet_instance_private_ip}
> Task inventory
> VPC1 and VPC2 security groups

#### Services you should use

Amazon VPC

#### Task validation

You must update three security groups with appropriate ingress rules to complete this task.

The task will be automatically completed once you find the solution. In addition, you can always check your progress by
pressing the "Check my progress" button on the task details screen.

Note: As per security best practices, security groups' ingress rules should not allow zero cidr on any port. Hence,
using zero cidr as the source is strictly prohibited in this challenge, and the task will not move to a completed state.
In addition, the automatic task validation script will not consider inbound rules of type All TCP and All Traffic as
correct solutions.

Hint: Using ICMP(All ICMP - IPv4) and SSH ports is sufficient to complete this task. No other ports are required.

### Task 2: Show the packets a way to go!!!

#### Background

Now that you can log in to the private instance (10.0.2.x) of VPC1 through the bastion host (10.0.1.x), routing is
required to ping the instance in the private subnet of VPC2 (192.168.2.x). Identify a way to accomplish this
requirement.

Things you should CONSIDER doing:

Use the VPC CIDR, subnet CIDR, or instance private IP addresses in route table entries.
Things you should AVOID doing:

Per best practices, using zero-CIDR (0.0.0.0/0) in route entries of all route tables is prohibited. The automatic task
validation script will verify this condition throughout the challenge. Any non-compliance will result in the task being
evaluated as incomplete.
SSH instructions
Use the information below to SSH into the bastion host EC2 instance using its public IP address. You can find the public
IP address of the bastion host in the Output Properties tab to the left of these instructions.

#### Getting Started

AWS documentation that may help perform the steps necessary for this task is linked below.

* Add and remove routes from a route table
* Add routes between the transit gateway and your VPCs

#### Inventory

VPC1 and VPC2 route tables

#### Services you should use

Amazon VPC

#### Task Validation

To complete this task, you must update two route tables with appropriate route entries.

Once you find the solution, the task will be automatically completed. However, you can always check your progress by
pressing the "Check my progress" button on the task details screen.

Note: Per security best practices, the route tables should not have zero-CIDR entries as a destination for internal
traffic. Hence, using zero-CIDR as a destination in route entries is prohibited. The automatic task validation function
will verify compliance with this requirement. In addition, the automatic task validation script will verify your route
entries before marking the task as completed.

Hint: Updating VPC route tables with the required route entries is sufficient to complete this task. Usage of other
services is not required.

---

### Task 3: Get the Packets Going!!!

#### Background

After successfully adding the required route entries, you should find a way to successfully ping the EC2 instance in the
VPC2 private subnet (192.168.2.x) from the VPC1 private subnet EC2 instance (10.0.2.x) through the transit gateway.
Figure out a way to accomplish this requirement.

This task will enable connectivity between VPC1 and VPC2 through AWS Transit Gateway. Once completed, your proof of
concept on AWS Transit Gateway will be ready for your company's leadership team review.

Note: Do not create a static route to accomplish this.

To complete the challenge, you should accomplish the following:

Ping the private IP of the VPC2 private subnet instance from the VPC1 private subnet instance.
Note: You DON'T need to log in to the VPC2 Private Subnet Instance to complete this challenge.

#### Getting started

You can use these documentation links to learn about transit gateway concepts.

> Transit gateway concepts
> How transit gateways work
> You can use Step 4 in this documentation link to get more information about testing the Transit Gateway.

> Before initiating a ping command to the VPC2 private subnet EC2 instance (192.168.2.x), make sure that you are in the
> VPC1 private subnet EC2 instance (10.0.2.x) before initiating a ping command to the VPC2 private subnet instance (
> 192.168.2.x).

> SSH instructions
> Use the information below to SSH into the bastion host EC2 instance using its public IP address. You can find the public
> IP address of the bastion host in the Output Properties tab to the left of these instructions.

Credentials
Username: participant
Password: tgw123
For Mac users
To SSH into the Bastion host, Open the Terminal application and connect to the bastion host using the following SSH
command. Note: You must replace bastion_host_public_ip with public IP of bastion host.

> ssh participant@{bastion_host_public_ip}
> Upon successful login to the Bastion host, SSH into the VPC1 Private Subnet Instance (10.0.2.x) using the below command
> in bastion host terminal. Note: You must replace vpc1_private_subnet_instance_private_ip with private IP of the EC2
> instance in VPC1 private subnet (i.e. 10.0.2.x).

> ssh participant@{vpc1_private_subnet_instance_private_ip}
> For Windows users
> To SSH into the bastion host, you must use a client such as PuTTY. If this is not installed on your computer, you must
> download and install one. Check your policies to ensure this is allowed if you use a company computer.

Once you download and install PuTTY, start the application.

In the Category pane, choose Session and complete the following fields:

* Enter participant@{bastion_host_public_ip} as the host, Note: You must replace the bastion_host_public_ip with public
  IP
  of bastion host.
* Ensure that the Port value is 22.
* Under Connection type, select SSH.
* Click Open button
* For more details, please refer to the Connecting to your Linux instance section in the AWS documentation.
* Upon successful login to the Bastion host, SSH into the VPC1 Private Subnet Instance (10.0.2.x) using the below
  command
  from Bastion host. Note: You must replace vpc1_private_subnet_instance_private_ip with private IP of the EC2 instance
  in
  VPC1 private subnet (i.e. 10.0.2.x).

> ssh participant@{vpc1_private_subnet_instance_private_ip}

#### Inventory

* VPC Transit Gateway
* VPC Transit Gateway attachments
* VPC Transit Gateway route tables
* Services you should use
* Amazon VPC
* AWS Transit Gateway

#### Task validation

Once you figure out the solution, SSH into the VPC1 bastion host. Then, SSH into the VPC1 private subnet instance (
10.0.2.x) using the local credentials provided in the SSH instructions. Then, you will issue a ping command to the VPC2
private subnet EC2 instance (192.168.2.x) from the VPC1 private subnet EC2 instance (10.0.2.x). If your solution is
correct, you should be able to successfully send ICMP traffic from VPC1 to VPC2 through Transit Gateway. Please continue
to ping the instance for at least 5 to 10 minutes.

The automatic task validation script will take approximately 5 to 10 minutes to analyze the number of packets going out
of Transit Gateway to evaluate the correctness of your solution.

Once you ping the VPC2 private subnet instance from the VPC1 Private Subnet, the task will be automatically completed.
However, you can always check your progress by pressing the "Check my progress" button on the task details screen.
