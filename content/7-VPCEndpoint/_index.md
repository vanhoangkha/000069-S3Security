---
title : "Restrict access to S3 VPC Endpoint"
date : "`r Sys.Date()`"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Restrict access to S3 VPC Endpoint

![Launch CloudFormation Template](/images/1-Introduce/0004.png?featherlight=false&width=60pc)

1. Access **AWS Management Console**

    - Find **VPC**
    - Select **VPC**

![VPC Endpoint](/images/7-VPCEndpoint/0001.png?featherlight=false&width=90pc)

2. In the **VPC** interface

   - Select **Enpoints**
   - Select **Create endpoint**


![VPC Endpoint](/images/7-VPCEndpoint/0002.png?featherlight=false&width=90pc)

3. In the **Create endpoint** interface

   - **Name tag**, enter **```S3-Endpoint```**
   - Select **AWS services**


![VPC Endpoint](/images/7-VPCEndpoint/0003.png?featherlight=false&width=90pc)

4. In services, we find **S3**

   - Select Type **Gateway**


![VPC Endpoint](/images/7-VPCEndpoint/0004.png?featherlight=false&width=90pc)

5. Select VPC **SID-vpc**, do not select **Route Table**


![VPC Endpoint](/images/7-VPCEndpoint/0005.png?featherlight=false&width=90pc)

6. Select **Create endpoint**


![VPC Endpoint](/images/7-VPCEndpoint/0006.png?featherlight=false&width=90pc)

7. Successfully created VPC endpoint

   - Note down **Endpoint ID** for the next steps


![VPC Endpoint](/images/7-VPCEndpoint/0007.png?featherlight=false&width=90pc)

8. Access to **S3 bucket**

   - Select **sid-security-xxx** bucket


![VPC Endpoint](/images/7-VPCEndpoint/0008.png?featherlight=false&width=90pc)

9. In the bucket interface

   - Select **Permissions**
   - Select **Edit** Bucket Policy.


![VPC Endpoint](/images/7-VPCEndpoint/0009.png?featherlight=false&width=90pc)

10. Copy the bucket policy into the Bucket Policy Editor

```
{
    "Statement": [
        {
            "Action": "s3:*",
            "Effect": "Deny",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*",
            "Condition": {
                "StringNotEquals": {
                    "aws:sourceVpce": "VPC_ENDPOINT_ID"
                }
            },
            "Principal": "*"
        }
    ]
}
```

    - Replace your **BUCKET NAME** and **VPC ENDPOINT ID**.

![VPC Endpoint](/images/7-VPCEndpoint/00010.png?featherlight=false&width=90pc)

11. Return to **SSH** interface

```
aws s3api head-object --key app1/file1 --profile user1 --bucket ${bucket}
```


![VPC Endpoint](/images/7-VPCEndpoint/00011.png?featherlight=false&width=90pc)

12. Return to **VPC endpoint** interface

    - Select **S3 endpoint**
    - Select **Actions**
    - Select **Manage route tables**

![VPC Endpoint](/images/7-VPCEndpoint/00012.png?featherlight=false&width=90pc)

13. In the **Manage route tables** interface

    - Select **SID-routes**
    - Select **Modify route tables**

![VPC Endpoint](/images/7-VPCEndpoint/00013.png?featherlight=false&width=90pc)

13. Successfully added route table


![VPC Endpoint](/images/7-VPCEndpoint/00014.png?featherlight=false&width=90pc)

14. Return to **SSH** interface

```
aws s3api head-object --key app1/file1 --profile user1 --bucket ${bucket}
```

![VPC Endpoint](/images/7-VPCEndpoint/00015.png?featherlight=false&width=90pc)