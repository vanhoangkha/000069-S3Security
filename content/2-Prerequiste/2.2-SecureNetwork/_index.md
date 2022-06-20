---
title : "Secure Network Access"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Safe internet access

Configure Security Group for the lab.

1. In the **AWS Management Console** interface

   - Find **VPC**
   - Select **VPC**

![Launch CloudFormation Template](/images/2-Prerequiste/0008.png?featherlight=false&width=90pc)

2. In the **VPC** interface

   - Select **Security Group**
   - Select **SID-ssh-sg**
   - Select **Actions**
   - Select **Edit inbound rules**


![Launch CloudFormation Template](/images/2-Prerequiste/0009.png?featherlight=false&width=90pc)

3. Configure **Inbound rules**

   - Select **Add rule**
   - Select Type **HTTP**, Source **Anywhere-IPv4**
   - Select Type **SSH**, Source **MyIP** (in case you can't connect, you can change it to **Anywhere-IPv4**)
   - Then select **Save rules**


![Launch CloudFormation Template](/images/2-Prerequiste/00010.png?featherlight=false&width=90pc)

4. Check the configured **Security Group**


![Launch CloudFormation Template](/images/2-Prerequiste/00011.png?featherlight=false&width=90pc)