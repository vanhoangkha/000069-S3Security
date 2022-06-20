---
title : "Require HTTPS"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Require HTTPS

In this section, we need to create **S3 Bucket Policy** to request a connection to use **HTTPS**

1. First we access **S3**

   - Select **Buckets**
   - Select **sid-security-xxxxxxx bucket**

![Require HTTPS](/images/3-HTTPS/0001.png?featherlight=false&width=90pc)

2. In the **sid-security-xxxxxxx bucket** interface

  - Select **Permissions**
  - In the **Bucket policy** section, select **Edit**

![Require HTTPS](/images/3-HTTPS/0002.png?featherlight=false&width=90pc)

3. Copy the following bucket policy into **Bucket Policy Editor**

```
{
"Statement": [
{
   "Action": "s3:*",
   "Effect": "Deny",
   "Principal": "*",
   "Resource": "arn:aws:s3:::BUCKET_NAME/*",
   "Condition": {
       "Bool": {
        "aws:SecureTransport": false
        }
    }
    }
  ]
}
```

Replace BUCKET_NAME with the group name you copied into your text editor. Make sure you don't remove the /* end of the group name.

![Require HTTPS](/images/3-HTTPS/0003.png?featherlight=false&width=90pc)

4. Check **Policy** and select **Save changes**

![Require HTTPS](/images/3-HTTPS/0004.png?featherlight=false&width=90pc)

5. Return to **SSH** interface to **SID-security-instance**. Run command

```
aws s3api head-object --key app1/file1 --endpoint-url http://s3.amazonaws.com --profile user1 --bucket ${bucket}
```
   - The command will return a 403 error because the endpoint-url is HTTP.


![Require HTTPS](/images/3-HTTPS/0005.png?featherlight=false&width=90pc)

6. Continue running the following command.

```
aws s3api --endpoint-url https://s3.amazonaws.com --profile user1 head-object --key app1/file1 --bucket ${bucket}
```

  The command succeeds because you used s3api which uses HTTPS.

![Require HTTPS](/images/3-HTTPS/0006.png?featherlight=false&width=90pc)