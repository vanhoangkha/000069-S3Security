---
title : "Hạn chế quyền truy cập vào S3 VPC Endpoint"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Hạn chế quyền truy cập vào  S3 VPC Endpoint

![Launch CloudFormation Template](/images/1-Introduce/0004.png?featherlight=false&width=60pc)

1. Truy cập **AWS Management Console**

    - Tìm **VPC**
    - Chọn **VPC**

![VPC Enpoint](/images/7-VPCEndpoint/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **VPC**

   - Chọn **Enpoints**
   - Chọn **Create endpoint**


![VPC Enpoint](/images/7-VPCEndpoint/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create endpoint**

   - **Name tag**, nhập **```S3-Endpoint```**
   - Chọn **AWS services**


![VPC Enpoint](/images/7-VPCEndpoint/0003.png?featherlight=false&width=90pc)

4. Trong các service, chúng ta tìm **S3**

   - Chọn Type **Gateway**


![VPC Enpoint](/images/7-VPCEndpoint/0004.png?featherlight=false&width=90pc)

5. Chọn VPC **SID-vpc**, không chọn **Route Table**


![VPC Enpoint](/images/7-VPCEndpoint/0005.png?featherlight=false&width=90pc)

6. Chọn **Create endpoint**


![VPC Enpoint](/images/7-VPCEndpoint/0006.png?featherlight=false&width=90pc)

7. Tạo VPC endpoint thành công

   - Ghi chú lại **Endpoint ID** dùng cho các bước tiếp theo


![VPC Enpoint](/images/7-VPCEndpoint/0007.png?featherlight=false&width=90pc)

8. Truy cập vào **S3 bucket**

   - Chọn **sid-security-xxx** bucket


![VPC Enpoint](/images/7-VPCEndpoint/0008.png?featherlight=false&width=90pc)

9. Trong giao diện bucket 

   - Chọn **Permissions**
   - Chọn **Edit** Bucket Policy.


![VPC Enpoint](/images/7-VPCEndpoint/0009.png?featherlight=false&width=90pc)

10. Sao chép bucket policy vào  Bucket Policy Editor

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

    - Thay thế **BUCKET NAME** và **VPC ENDPOINT ID** của bạn. 

![VPC Enpoint](/images/7-VPCEndpoint/00010.png?featherlight=false&width=90pc)

11. Trở lại  giao diện **SSH**

```
aws s3api head-object --key app1/file1 --profile user1 --bucket ${bucket}
```


![VPC Enpoint](/images/7-VPCEndpoint/00011.png?featherlight=false&width=90pc)

12. Quay lại giao diện **VPC endpoint**

    - Chọn **S3 endpoint** 
    - Chọn **Actions**
    - Chọn **Manage route tables**

![VPC Enpoint](/images/7-VPCEndpoint/00012.png?featherlight=false&width=90pc)

13. Trong giao diện **Manage route tables**

    - Chọn **SID-routes**
    - Chọn **Modify route tables**

![VPC Enpoint](/images/7-VPCEndpoint/00013.png?featherlight=false&width=90pc)

13. Thêm route table thành công


![VPC Enpoint](/images/7-VPCEndpoint/00014.png?featherlight=false&width=90pc)

14. Quay trở lại giao diện **SSH**

```
aws s3api head-object --key app1/file1 --profile user1 --bucket ${bucket}
```

![VPC Enpoint](/images/7-VPCEndpoint/00015.png?featherlight=false&width=90pc)

