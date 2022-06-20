---
title : "Using AWS Config to Detect Public Bucket"
date : "`r Sys.Date()`"
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### Using AWS Config to Detect Public Bucket

1. Go to **AWS Management Console**

    - Find **AWS Config**
    - Select **AWS Config**

![AWS Config](/images/8-AWSConfig/0001.png?featherlight=false&width=90pc)

2. In the **AWS Config** interface

    - Select **Rules**
    - Select **Add rules**

![AWS Config](/images/8-AWSConfig/0002.png?featherlight=false&width=90pc)

3. Choose a rule type

    - Select **Add AWS managed rule**

![AWS Config](/images/8-AWSConfig/0003.png?featherlight=false&width=90pc)


4. For **AWS Managed Rules**

   - Find **s3-bucket-public-read-prohibited**
   - Select **s3-bucket-public-read-prohibited**
   - Select **Next**

![AWS Config](/images/8-AWSConfig/0004.png?featherlight=false&width=90pc)

5. Select **Next**

![AWS Config](/images/8-AWSConfig/0005.png?featherlight=false&width=90pc)

6. Check again and select **Add rule**

![AWS Config](/images/8-AWSConfig/0006.png?featherlight=false&width=90pc)

7. The rule has been added successfully.
![AWS Config](/images/8-AWSConfig/0007.png?featherlight=false&width=90pc)

8. Go to **AWS Config** interface and select **Dashboard**

![AWS Config](/images/8-AWSConfig/0008.png?featherlight=false&width=90pc)

9. Return to **S3 bucket** interface

   - Select **sid-security-xxx** bucket.

![AWS Config](/images/8-AWSConfig/0009.png?featherlight=false&width=90pc)

10. In the bucket interface select **Permissions**

![AWS Config](/images/8-AWSConfig/00010.png?featherlight=false&width=90pc)


11. For **Access control list (ACL)**, select **Edit**

![AWS Config](/images/8-AWSConfig/00011.png?featherlight=false&width=90pc)

12. In the **ACL** editing interface

    - For **Everyone (public access)**, select **List** and **Read**

![AWS Config](/images/8-AWSConfig/00012.png?featherlight=false&width=90pc)

13. Select **I understand the effects...*** and select **Save changes**

![AWS Config](/images/8-AWSConfig/00013.png?featherlight=false&width=90pc)

14. Now we will see **Permissions** in state **Public** (Public Bucket)

![AWS Config](/images/8-AWSConfig/00014.png?featherlight=false&width=90pc)

15. Return to **Config** interface

    - Select **Rules**
    - Select **s3-bucket-public-read-prohibited**
    - Observation **Resource in scope** is currently not available.

![AWS Config](/images/8-AWSConfig/00015.png?featherlight=false&width=90pc)

16. In the same interface, select **Actions**

    - Select **Re-evaluate**

![AWS Config](/images/8-AWSConfig/00016.png?featherlight=false&width=90pc)

17. Observe the **Resource in scope** section appears resource.

![AWS Config](/images/8-AWSConfig/00017.png?featherlight=false&width=90pc)