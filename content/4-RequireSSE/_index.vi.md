---
title : "Yêu cầu mã hóa SSE-S3"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Yêu cầu mã hóa SSE-S3

Amazon S3 hỗ trợ cả mã hóa phía máy chủ (với 3 tùy chọn quản lý khóa: SSE-KMS, SSE-C, SSE-S3) và mã hóa phía máy khách để tải dữ liệu lên. Amazon S3 cung cấp các tính năng bảo mật linh hoạt để ngăn không cho người dùng trái phép truy cập dữ liệu của bạn. Bạn có thể kết nối với tài nguyên S3 từ Amazon Virtual Private Cloud (Amazon VPC) bằng cách sử dụng điểm cuối VPC

![SSE](/images/1-Introduce/0005.png?featherlight=false&width=20pc)

Trong phần này, chúng ta tạo **S3 Bucket Policy** để yêu cầu mã hóa dữ liệu ở trạng thái nghỉ.

1. Tương tự ở lab trước, chúng ta truy cập vào **AWS Management Console**

   - Tìm **S3**
   - Chọn **S3**

![SSE](/images/4-SSE-S3/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **S3**

   - Chọn **Buckets**
   - Chọn **sid-security-xxxxxxx bucket**

![SSE](/images/4-SSE-S3/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **sid-security-xxxxxxx bucket**

   - Chọn **Permission**

   - Trong **Bucket policy**, chọn **Edit**

![SSE](/images/4-SSE-S3/0003.png?featherlight=false&width=90pc)

4. Sao chép **bucket policy** vào **Bucket Policy Editor**


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

5. Thay thế **BUCKET_NAME** bằng tên bucket mà bạn đã sao chép vào trình soạn thảo văn bản của mình và nhấp vào **Save changes**.

![SSE](/images/4-SSE-S3/0005.png?featherlight=false&width=90pc)

6. Quay trở lại giao diện SSH. Chạy lệnh

```
cd ~  
echo "123456789abcdefg" > textfile  
```

![SSE](/images/4-SSE-S3/0006.png?featherlight=false&width=90pc)

7. Thực hiện chạy lệnh **put an object** vào bucket

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}  
```

Yêu cầu sẽ không thành công, vì object không được mã hóa.

![SSE](/images/4-SSE-S3/0007.png?featherlight=false&width=90pc)

8. Tiếp tục chạy lệnh put object sử dụng mã hóa SSE-S3

```
aws s3api put-object --key text01 --body textfile --server-side-encryption AES256 --profile user1 --bucket ${bucket}  
```

Lệnh thành công vì PUT đã sử dụng SSE-S3.



![SSE](/images/4-SSE-S3/0008.png?featherlight=false&width=90pc)

9. Kiểm tra S3 có 1 file **text01**

![SSE](/images/4-SSE-S3/0009.png?featherlight=false&width=90pc)

