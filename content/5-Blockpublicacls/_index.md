---
title : "Block Public ACLs"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Block public ACL



1. Same as before, go to **Amazon S3**

   - Select **Bucket**
   - Select **sid-security-xxxxxxx bucket**

![SSE](/images/5-ACLs/0001.png?featherlight=false&width=90pc)

2. In the **sid-security-xxxxxxx bucket** interface

   - Select **Permission**
   - Under **Bucket Policy** select **Edit**

![SSE](/images/5-ACLs/0002.png?featherlight=false&width=90pc)

3. Copy the bucket policy to **Bucket Policy Editor***


```
{
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::BUCKET_NAME/*",
            "Condition": {
                "StringEquals": {
                    "s3:x-amz-acl": "private"
                }
            }
        }
    ]
}
```

![SSE](/images/5-ACLs/0003.png?featherlight=false&width=90pc)

4. Replace **BUCKET_NAME** with the bucket name you copied into your text editor and click **Save changes**

![SSE](/images/5-ACLs/0004.png?featherlight=false&width=90pc)

5. Go back to the SSH section and connect to SID-security-instance

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}
```

The request will succeed because the default for an ACL object is private.

![SSE](/images/5-ACLs/0005.png?featherlight=false&width=90pc)

6. Continue running the command

```
aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}
```
This command also succeeds, but it is not the behavior one would expect

Current Group Policy allows private ACLs but does NOT DELETE anything. It is important to write policies that prevent actions, not allow them when trying to restrict actions against a group. The current group policy also allows Public access to unintentional groups because the main character is a wildcard.

![SSE](/images/5-ACLs/0006.png?featherlight=false&width=90pc)

7. Access to **S3**

   - Select buckets
   - Select **sid-security-xx** bucket
   - Select **Permissions**
   - Select **Edit** Bucket policy

![SSE](/images/5-ACLs/0007.png?featherlight=false&width=90pc)

8. Replace new policy

```
{
    "Statement": [
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": [
                    "s3:PutObject",
                    "s3:PutObjectAcl"
                    ],
            "Resource": "arn:aws:s3:::BUCKET_NAME/*",
            "Condition": {
                "StringEquals": {
                    "s3:x-amz-acl": [
                           "public-read",
                           "public-read-write",
                           "authenticated-read"
                    ]
                }
            }
        }
    ]
}
```

- Select **Save changes**

![SSE](/images/5-ACLs/0008.png?featherlight=false&width=90pc)

9. Edit the policy successfully.

![SSE](/images/5-ACLs/0009.png?featherlight=false&width=90pc)

10. Back to the SSH interface, run the following command.

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}
```
The request will succeed because the default for an ACL object is private.

![SSE](/images/5-ACLs/00010.png?featherlight=false&width=90pc)

11. Continue to run the following command.

```
aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}
```

The request failed because group policy now restricts the ACL from being read publicly.

![SSE](/images/5-ACLs/00011.png?featherlight=false&width=90pc)