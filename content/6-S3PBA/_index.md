---
title : "Configuring S3 Block Public Access"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Configure S3 Block Public Access

With just a few selects in the S3 management console, you can apply **S3 Block Public Access** to any bucket in your account – both existing buckets and any buckets any new ones created in the future – while ensuring that there is no public access to any objects. S3 Block Public Access settings replace the S3 permission for public access, making it easy for account administrators to set up centralized controls to prevent changes in security configurations, no matter how the added object or how to create a storage area.

![Launch CloudFormation Template](/images/1-Introduce/0003.png?featherlight=false&width=60pc)

#### Practice

1. Access to **S3**

    - Select **sid-security-xxxxxxxx**

![SSE](/images/6-S3Block/0001.png?featherlight=false&width=90pc)

2. Select **Permissions**

   - In the **Bucket Policy** section, select **Delete**

![SSE](/images/6-S3Block/0002.png?featherlight=false&width=90pc)

3. Fill in **Delete** and select **Delete** to confirm the deletion.

![SSE](/images/6-S3Block/0003.png?featherlight=false&width=90pc)

4. In the **Block public access (bucket settings)** section

   - Select **Edit**

![SSE](/images/6-S3Block/0004.png?featherlight=false&width=90pc)

5. Make edits

   - Select **Block public access to buckets and objects granted through new access control lists (ACLs)**
   - Select **Save changes**

![SSE](/images/6-S3Block/0005.png?featherlight=false&width=90pc)

6. Fill in **confirm** and then select **Confirm**

![SSE](/images/6-S3Block/0006.png?featherlight=false&width=90pc)

7. After the change, we observe that **Block all public access** is **On**

![SSE](/images/6-S3Block/0007.png?featherlight=false&width=90pc)

8. Return to **SSH** interface

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}
```
The request succeeds because default for an ACL object is private.

![SSE](/images/6-S3Block/0008.png?featherlight=false&width=90pc)

9. Continue running the command

```
aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}
```

The request failed because group policy restricts the ACL from being read publicly.

![SSE](/images/6-S3Block/0009.png?featherlight=false&width=90pc)

10. Perform access to **S3**

    - Select **Buckets**
    - Select **sid-security-xxx** bucket

![SSE](/images/6-S3Block/00010.png?featherlight=false&width=90pc)

11. In the exchange **bucket**

    - Select **Permissions**
    - For **Block public access (bucket settings)**, select **Edit**

![SSE](/images/6-S3Block/00011.png?featherlight=false&width=90pc)

12. Make edits

    - Select **Block public access to buckets and objects granted through new access control lists (ACLs)**
    - Select **Save changes**

![SSE](/images/6-S3Block/00012.png?featherlight=false&width=90pc)

13. Fill in **confirm** and select **Confirm**

![SSE](/images/6-S3Block/00013.png?featherlight=false&width=90pc)

14. Finish editing.

![SSE](/images/6-S3Block/00014.png?featherlight=false&width=90pc)