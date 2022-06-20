---
title : "Sử dụng AWS Config để phát hiện Public Bucket"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### Sử dụng AWS Config để phát hiện Public Bucket

1. Truy cập vào **AWS Management Console**

    - Tìm **AWS Config**
    - Chọn **AWS Config**

![AWS Config](/images/8-AWSConfig/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **AWS Config**

    - Chọn **Rules**
    - Chọn **Add rules**

![AWS Config](/images/8-AWSConfig/0002.png?featherlight=false&width=90pc)

3. Chọn kiểu rule

    - Chọn **Add AWS managed rule**

![AWS Config](/images/8-AWSConfig/0003.png?featherlight=false&width=90pc)


4. Đối với **AWS Managed Rules**

   - Tìm **s3-bucket-public-read-prohibited**
   - Chọn **s3-bucket-public-read-prohibited**
   - Chọn **Next**

![AWS Config](/images/8-AWSConfig/0004.png?featherlight=false&width=90pc)

5. Chọn **Next**

![AWS Config](/images/8-AWSConfig/0005.png?featherlight=false&width=90pc)

6. Kiểm tra lại và chọn **Add rule**

![AWS Config](/images/8-AWSConfig/0006.png?featherlight=false&width=90pc)

7. Vậy là đã thêm rule thành công.
![AWS Config](/images/8-AWSConfig/0007.png?featherlight=false&width=90pc)

8. Vào giao diện **AWS Config** và chọn **Dashboard**

![AWS Config](/images/8-AWSConfig/0008.png?featherlight=false&width=90pc)

9. Quay lại giao diện **S3 bucket**

   - Chọn **sid-security-xxx** bucket.

![AWS Config](/images/8-AWSConfig/0009.png?featherlight=false&width=90pc)

10. Trong giao diện bucket chọn **Permissions**

![AWS Config](/images/8-AWSConfig/00010.png?featherlight=false&width=90pc)


11. Đối với **Access control list (ACL)**, chọn **Edit**

![AWS Config](/images/8-AWSConfig/00011.png?featherlight=false&width=90pc)

12. Trong giao diện chỉnh sửa **ACL**

    - Đối với **Everyone (public access)**, chọn **List** và **Read**

![AWS Config](/images/8-AWSConfig/00012.png?featherlight=false&width=90pc)

13. Chọn **I understand the effects...*** và chọn **Save changes**

![AWS Config](/images/8-AWSConfig/00013.png?featherlight=false&width=90pc)

14. Bây giờ chúng ta sẽ thấy **Permissions** ở trạng thái **Public** (Public Bucket)

![AWS Config](/images/8-AWSConfig/00014.png?featherlight=false&width=90pc)

15. Quay lại giao diện **Config**

    - Chọn **Rules**
    - Chọn **s3-bucket-public-read-prohibited**
    - Quan sát **Resource in scope** hiện tại không có.

![AWS Config](/images/8-AWSConfig/00015.png?featherlight=false&width=90pc)

16. Cũng trong giao diện đó, chọn **Actions**

    - Chọn **Re-evaluate**

![AWS Config](/images/8-AWSConfig/00016.png?featherlight=false&width=90pc)

17. Quan sát phần **Resource in scope** đã xuất hiện resource.

![AWS Config](/images/8-AWSConfig/00017.png?featherlight=false&width=90pc)
