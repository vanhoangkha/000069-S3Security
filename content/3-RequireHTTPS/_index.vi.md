---
title : "Yêu cầu HTTPS"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

#### Yêu cầu HTTPS

Trong phần này, chúng ta cần tạo **S3 Bucket Policy** để yêu cầu kết nối để sử dụng **HTTPS**

1. Đầu tiên chúng ta truy cập vào **S3**

   - Chọn **Buckets**
   - Chọn **sid-security-xxxxxxx bucket**

![Require HTTPS](/images/3-HTTPS/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **sid-security-xxxxxxx bucket**

  - Chọn **Permissions**
  - Phần **Bucket policy**, chọn **Edit**

![Require HTTPS](/images/3-HTTPS/0002.png?featherlight=false&width=90pc)

3. Thực hiện copy đoạn bucket policy sau vào **Bucket Policy Editor**

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

Thay thế BUCKET_NAMEbằng tên nhóm mà bạn đã sao chép vào trình soạn thảo văn bản của mình. Đảm bảo rằng bạn không xóa /*phần cuối của tên nhóm.

![Require HTTPS](/images/3-HTTPS/0003.png?featherlight=false&width=90pc)

4. Kiểm tra lại **Policy** và chọn **Save changes**

![Require HTTPS](/images/3-HTTPS/0004.png?featherlight=false&width=90pc)  

5. Quay lại giao diện **SSH** vào **SID-security-instance**. Chạy lệnh 

```
aws s3api head-object --key app1/file1 --endpoint-url http://s3.amazonaws.com --profile user1 --bucket ${bucket}
```
   - Lệnh sẽ trả về lỗi 403 vì endpoint-url là HTTP.


![Require HTTPS](/images/3-HTTPS/0005.png?featherlight=false&width=90pc)

6. Tiếp tục chạy lệnh sau.

```
aws s3api --endpoint-url https://s3.amazonaws.com --profile user1 head-object --key app1/file1 --bucket ${bucket}
```

  Lệnh thành công vì bạn đã sử dụng s3api sử dụng HTTPS.

![Require HTTPS](/images/3-HTTPS/0006.png?featherlight=false&width=90pc)







