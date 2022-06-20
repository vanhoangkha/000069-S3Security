---
title : "Launch CloudFormation Template"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Launch CloudFormation Template

We perform the initialization of the resources to use for the lab.

Method 1: Download **[CloudFormation template](https://raw.githubusercontent.com/AWS-First-Cloud-Journey/FCj-S3-LAB/master/sid-base-template.yaml)**

Method 2: Download **[CloudFormation template](https://aws-storage-immersion-day.s3.us-west-2.amazonaws.com/sid-base-template.yaml)**

1. Access the interface **[AWS Management Console](https://ap-southeast-1.console.aws.amazon.com/console/home?region=ap-southeast-1)**

    - Find **CloudFormation**
    - Select **CloudFormation**

![Launch CloudFormation Template](/images/2-Prerequiste/0001.png?featherlight=false&width=90pc)

2. In the **CloudFormation** interface

   - Select **Stack**
   - Select **Create stack**


![Launch CloudFormation Template](/images/2-Prerequiste/0002.png?featherlight=false&width=90pc)

3. In the **Create stack** interface

   - Select **Template is ready**
   - **Template source**, depending on how you choose the template

   - You can choose the path **Amazon S3 URL**: https://aws-storage-immersion-day.s3.us-west-2.amazonaws.com/sid-base-template.yaml
   - Or you can also upload files.


![Launch CloudFormation Template](/images/2-Prerequiste/0003.png?featherlight=false&width=90pc)

4. In this section

   - You enter **FCJ-S3-LAB** for **Stack name**
   - Regarding **Lab Modules**, you choose **true** for **Deploy S3 Security Lab** (the lab is in progress) and you can choose to add **Deploy Storage Performance Lab** (preparing for the next lab).
   - Other modules choose **false**
   - Select **Next**


![Launch CloudFormation Template](/images/2-Prerequiste/0004.png?featherlight=false&width=90pc)

5. Select **Next**


![Launch CloudFormation Template](/images/2-Prerequiste/0005.png?featherlight=false&width=90pc)

6. Confirm required IAM generation

   - Select **I acknowledge that AWS CloudFormation might create IAM resources with custom names.**
   - Select **I acknowledge that AWS CloudFormation might require the following capability: CAPABILITY_AUTO_EXPAND**
   - Select **Create Stack**


![Launch CloudFormation Template](/images/2-Prerequiste/0006.png?featherlight=false&width=90pc)

7. Complete the **Stack** creation process

   - When the status of the stack changes to **CREATE_COMPLETE**


![Launch CloudFormation Template](/images/2-Prerequiste/0007.png?featherlight=false&width=90pc)