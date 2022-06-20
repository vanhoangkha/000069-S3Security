---
title : "Block Public ACLs"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Chặn ACL công khai



1. Giống phần trước, truy cập **Amazon S3**

   - Chọn **Bucket**
   - Chọn **sid-security-xxxxxxx bucket**

![SSE](/images/5-ACLs/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **sid-security-xxxxxxx bucket**

   - Chọn **Permission**
   - Dưới **Bucket Policy** chọn **Edit**

![SSE](/images/5-ACLs/0002.png?featherlight=false&width=90pc)

3. Sao chép bucket policy vào **Bucket Policy Editor***


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

4. Thay thế **BUCKET_NAME** bằng bucket name mà bạn đã sao chép vào trình soạn thảo văn bản của bạn và nhấp vào **Save changes**

![SSE](/images/5-ACLs/0004.png?featherlight=false&width=90pc)

5. Quay lại SSH section kết nối với SID-security-instance 

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}  
```

Yêu cầu sẽ thành công vì mặc định cho một đối tượng ACL là riêng tư.

![SSE](/images/5-ACLs/0005.png?featherlight=false&width=90pc)

6. Tiếp tục chạy lệnh

```
aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}   
```
Lệnh này cũng thành công, nhưng nó không phải là hành vi mà người ta mong đợi

Chính sách nhóm hiện tại cho phép các ACL riêng tư nhưng không TỪ CHỐI bất cứ điều gì. Điều quan trọng là viết các chính sách ngăn chặn các hành động, không cho phép nó khi cố gắng hạn chế các hành động chống lại một nhóm. Chính sách nhóm hiện tại cũng cho phép Công khai truy cập vào nhóm không chủ ý do ký tự chính là ký tự đại diện.

![SSE](/images/5-ACLs/0006.png?featherlight=false&width=90pc)

7. Truy cập vào **S3**

   - Chọn buckets
   - Chọn **sid-security-xx** bucket
   - Chọn **Permissions**
   - Chọn **Edit** Bucket policy

![SSE](/images/5-ACLs/0007.png?featherlight=false&width=90pc)

8. Thay thế policy mới 

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

- Chọn **Save changes**

![SSE](/images/5-ACLs/0008.png?featherlight=false&width=90pc)

9. Chỉnh sửa policy thành công.

![SSE](/images/5-ACLs/0009.png?featherlight=false&width=90pc)

10. Quay lại giao diện SSH, chạy lệnh sau.

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}
```
Yêu cầu sẽ thành công vì mặc định cho một đối tượng ACL là riêng tư.

![SSE](/images/5-ACLs/00010.png?featherlight=false&width=90pc)

11. Tiếp tục chạy lệnh sau.

```
aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}
```

Yêu cầu không thành công vì chính sách nhóm hiện hạn chế ACL đọc công khai.

![SSE](/images/5-ACLs/00011.png?featherlight=false&width=90pc)


