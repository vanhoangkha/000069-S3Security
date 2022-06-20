---
title : "Require SSE-S3 Encryption"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Require SSE-S3 Encryption

Amazon S3 supports both server-side encryption (with 3 key management options: SSE-KMS, SSE-C, SSE-S3) and client-side encryption for data uploads. Amazon S3 provides flexible security features to prevent unauthorized users from accessing your data. You can connect to S3 resources from Amazon Virtual Private Cloud (Amazon VPC) using the VPC endpoint

![SSE](/images/1-Introduce/0005.png?featherlight=false&width=20pc)

In this section, we create **S3 Bucket Policy** to require encryption of data at rest.

1. Similar to the previous lab, we access **AWS Management Console**

   - Find **S3**
   - Select **S3**

![SSE](/images/4-SSE-S3/0001.png?featherlight=false&width=90pc)

2. In the **S3** interface

   - Select **Buckets**
   - Select **sid-security-xxxxxxx bucket**

![SSE](/images/4-SSE-S3/0002.png?featherlight=false&width=90pc)

3. In the **sid-security-xxxxxxx bucket** interface

   - Select **Permission**

   - In **Bucket policy**, select **Edit**

![SSE](/images/4-SSE-S3/0003.png?featherlight=false&width=90pc)

4. Copy **bucket policy** to **Bucket Policy Editor**


```
{
    "Statement": [
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*",
            "Condition": {
                "StringNotEquals": {
                    "s3:x-amz-server-side-encryption": "AES256"
                }
            }
        }
    ]
}
```

![SSE](/images/4-SSE-S3/0004.png?featherlight=false&width=90pc)

5. Replace **BUCKET_NAME** with the bucket name you copied into your text editor and click **Save changes**.

![SSE](/images/4-SSE-S3/0005.png?featherlight=false&width=90pc)

6. Return to the SSH interface. Run command

```
cd ~
echo "123456789abcdefg" > textfile
```

![SSE](/images/4-SSE-S3/0006.png?featherlight=false&width=90pc)

7. Execute the command **put an object** into the bucket

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}
```

The request will fail because the object is not encrypted.

![SSE](/images/4-SSE-S3/0007.png?featherlight=false&width=90pc)

8. Continue running put object using SSE-S3 encoding

```
aws s3api put-object --key text01 --body textfile --server-side-encryption AES256 --profile user1 --bucket ${bucket}
```

The command was successful because the PUT used SSE-S3.



![SSE](/images/4-SSE-S3/0008.png?featherlight=false&width=90pc)

9. Check S3 has 1 file **text01**

![SSE](/images/4-SSE-S3/0009.png?featherlight=false&width=90pc)