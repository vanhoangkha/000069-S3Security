---
title : "Using Amazon Access Analyzer for S3"
date : "`r Sys.Date()`"
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Using Amazon Access Analyzer for S3

1. Go to **AWS Management Console**

   - Find **IAM**
   - Select **IAM**

![Amazon Access Analyzer](/images/Analyzer/0001.png?featherlight=false&width=90pc)

2. In the **IAM** interface

    - Select **Access analyzer**
    - Select **Create analyzer**

![Amazon Access Analyzer](/images/Analyzer/0002.png?featherlight=false&width=90pc)

3. In the **Create analyzer** interface

   - Select **Create analyzer**

![Amazon Access Analyzer](/images/Analyzer/0003.png?featherlight=false&width=90pc)

4. Create **Analyzer** successfully.

![Amazon Access Analyzer](/images/Analyzer/0004.png?featherlight=false&width=90pc)

5. In the **Analyzer** interface

    - Select **Active**
    - Select **S3 bucket**

![Amazon Access Analyzer](/images/Analyzer/0005.png?featherlight=false&width=90pc)

6. Access to **Access analyzer for S3** interface

![Amazon Access Analyzer](/images/Analyzer/0006.png?featherlight=false&width=90pc)

7. In the **S3** interface

   - Select **Bucket**
   - Select **sid-security-xxx**

![Amazon Access Analyzer](/images/Analyzer/0007.png?featherlight=false&width=90pc)

8. In the **bucket** interface

    - Select **Permissions**

![Amazon Access Analyzer](/images/Analyzer/0008.png?featherlight=false&width=90pc)

9. For **Access control list (ACL)**

    - Select **Edit**

![Amazon Access Analyzer](/images/Analyzer/0009.png?featherlight=false&width=90pc)

10. In the Edit ACLs interface

    - Uncheck **List** and **Read** of **Everyone (public access)**
    - Select **Save changes**

![Amazon Access Analyzer](/images/Analyzer/00010.png?featherlight=false&width=90pc)

11. Return to **Access Analyzer** interface of **IAM**

    - Select **Resolved**
    - Find **S3**
    - Select **Finding ID** appears.

![Amazon Access Analyzer](/images/Analyzer/00011.png?featherlight=false&width=90pc)

12. In the **Finding ID** interface

    - View status is in **Resolved**

![Amazon Access Analyzer](/images/Analyzer/00012.png?featherlight=false&width=90pc)