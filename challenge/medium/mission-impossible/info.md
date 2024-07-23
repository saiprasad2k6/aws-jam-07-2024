# MISSION IMPOSSIBLE, SECURE THE NOC LIST!

The Non-Official Cover List, or simply known as the NOC List, is list of covert operatives of the Impossible Missions
Force, showing their codenames and their real names. After the fiasco that we all witnessed in Mission Impossible I, the
CIA has decided to move away from on-premise and wants to store the NOC list on S3 in AWS cloud.

You have been hired by the Chief of Impossible Missions Force (C-IMF) to setup NOC list on Amazon S3 and establish
security best practices with encryption and associated notifications.

Your mission, should you choose to accept it , is to accomplish four tasks:

Setup AWS Key Management Service (AWS KMS) encryption key

Setup Amazon Simple Notification Service (Amazon SNS) encrypted topics

Create Amazon S3 bucket that is encrypted with KMS key

Enable S3 Event Notifications to track events to your NOC list bucket

noc_access_key_725789539585

### Task 1: Security is Key!

#### Background

The mandate from Impossible Missions Force (IMF) is to encrypt everything! You need to create a new KMS key and enable
key rotation. Create and manage separate keys for different services.

#### Task

Your mission here is to create a new KMS Key named noc_access_key_XXXXXXXXXXXX where the X's represent your 12-digit AWS
Account number. You have to add your Federated user as key administrator and key user. Also you have to apply KMS
security best practices to your KMS key.

#### Getting Started

Setup AWS KMS key https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying.html

#### Inventory

AWS Key Management Service (AWS KMS), Amazon Simple Notification Service (Amazon SNS), Amazon Simple Storage Service (
Amazon S3)

#### Services You Should Use

AWS Key Management Service (KMS)

#### Task Validation

The task will be completed automatically if you have done the required changes correctly or you can always click on "
Check My Progress" button to see the status of your task.

---

### Task 2: Establish Secure Communication Channel!

#### Background

Register yourself as a trusted member of the Chief of Impossible Missions Force C-IMF's inner circle. Subscribe via
Email to receive the notifications for New Object Created (NOC) events!

#### Task

You have to create an encrypted SNS topic with name topic_NOC_event and subscribe to it SNS topic via your email.
Remember to confirm you subscription via Email link!

IMPORTANT: It can take anywhere from 2 to 5 minutes for emails to arrive to your mailbox depending on AWS Region.

#### Getting Started

Create your first SNS topic https://docs.aws.amazon.com/sns/latest/dg/sns-getting-started.html

#### Inventory

AWS Key Management Service (AWS KMS), Amazon Simple Notification Service (Amazon SNS), Amazon Simple Storage Service (
Amazon S3)

#### Services You Should Use

Amazon SNS

#### Task Validation

The task will be completed automatically if you have done the required changes correctly or you can always click on "
Check My Progress" button to see the status of your task.

---

### Task 3: Secure NOC Bucket!

#### Background

You need a globally accessible, highly scalable, reliable, fast, and inexpensive cloud data storage - where all the
company secrets will be held!

#### Task

You have to ceate a secure Amazon S3 bucket with name secret-noc-bucket-XXXXXXXXXXXX , where the X's represent your 12
digit account number. Confirm that the bucket in the same region your challenge is executing and you have encryption
enabled using KMS key from previous task.

#### Getting Started

Create your first S3 bucket https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-bucket.html

#### Inventory

AWS Key Management Service (AWS KMS), Amazon Simple Notification Service (Amazon SNS), Amazon Simple Storage Service (
Amazon S3)

#### Services You Should Use

Amazon S3

#### Task Validation

We will automatically keep checking on an interval to validate whether this task has been completed. You can also click
the Check Progress button to check manually.

---

#### Task 4: Setup NOC Notifications!

#### Background
So far you have completed the security setup for Impossible Missions Force (IMF) KMS key , established secure
communications channel over email and also secured their S3 bucket that will contain the NOC list.

#### Task
You have to setup S3 Event Notifications with name IMF_NOC_Event , to track Add and Delete activities on the NOC bucket.
You will need to allow S3 service permission to publish to SNS, and also permission to use the KMS Key.

Then you need to create a NOC file , filename must be uppercase NOC_YYYYMMDD.TXT , using today's date, with TAB
separated data for following columns (no need for a header row)

Agent First name , Agent Last Name , Real First Name , Real Last Name
Note the AWS Region you are running and make sure you use "today" as per the AWS Region that you are running in, and not
your physical region or local timezone. Example, if the lab is running in a South America time zone it be a day ahead if
you are in Canada time zone, so use South America time zone for the file name.

Enter four rows like shown below

ETHANtabHUNTtabTOMtabCRUISE
MARISSAtabWIEGLERtabCATEtabBLANCHETT
JASONtabBOURNEtabMATTtabDAMON
JANEtabSMITHtabANGELINAtabJOLIE
Once you upload the NOC file to S3 NOC bucket, if you have setup everything correctly you will receive email
notification to your subscribed address

#### Getting Started
Refer AWS News Blog https://aws.amazon.com/blogs/aws/s3-event-notification/

#### Inventory
AWS Key Management Service (AWS KMS), Amazon Simple Notification Service (Amazon SNS), Amazon Simple Storage Service (
Amazon S3)

#### Services You Should Use
Amazon SNS, Amazon S3

#### Task Validation
We will automatically keep checking on an interval to validate whether this task has been completed. You can also click
the Check Progress button to check manually.

IMPORTANT: It can take anywhere from 2 to 5 minutes for notifications to arrive to your mailbox depending on AWS Region
and for Cloudwatch metrics to reflect.