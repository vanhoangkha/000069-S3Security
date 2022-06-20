---
title : "Sử dụng Amazon Access Analyzer cho S3"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Sử dụng Amazon Access Analyzer cho S3

1. Truy cập vào **AWS Management Console**

   - Tìm **IAM**
   - Chọn **IAM**

![Amazon Access Analyzer](/images/Analyzer/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **IAM**

    - Chọn **Access analyzer**
    - Chọn **Create analyzer**

![Amazon Access Analyzer](/images/Analyzer/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create analyzer**

   - Chọn **Create analyzer**

![Amazon Access Analyzer](/images/Analyzer/0003.png?featherlight=false&width=90pc)

4.  Tạo **Analyzer** thành công.

![Amazon Access Analyzer](/images/Analyzer/0004.png?featherlight=false&width=90pc)

5. Trong giao diện **Analyzer** 

    - Chọn **Active**
    - Chọn **S3 bucket**

![Amazon Access Analyzer](/images/Analyzer/0005.png?featherlight=false&width=90pc)

6. Truy cập vào giao diện **Access analyzer for S3**

![Amazon Access Analyzer](/images/Analyzer/0006.png?featherlight=false&width=90pc)

7. Trong giao diện **S3**

   - Chọn **Bucket**
   - Chọn **sid-security-xxx**

![Amazon Access Analyzer](/images/Analyzer/0007.png?featherlight=false&width=90pc)

8. Trong giao diện **bucket**

    - Chọn **Permissions**

![Amazon Access Analyzer](/images/Analyzer/0008.png?featherlight=false&width=90pc)

9. Đối với **Access control list (ACL)**

    - Chọn **Edit**

![Amazon Access Analyzer](/images/Analyzer/0009.png?featherlight=false&width=90pc)

10. Trong giao diện Edit ACLs

    - Bỏ chọn **List** và **Read** của **Everyone (public access)**
    - Chọn **Save changes**

![Amazon Access Analyzer](/images/Analyzer/00010.png?featherlight=false&width=90pc)

11. Quay lại giao diện **Access Analyzer**  của **IAM**

    - Chọn **Resolved**
    - Tìm **S3**
    - Chọn **Finding ID** đã hiện ra.

![Amazon Access Analyzer](/images/Analyzer/00011.png?featherlight=false&width=90pc)

12. Trong giao diện **Finding ID**

    - Xem status đang ở **Resolved**

![Amazon Access Analyzer](/images/Analyzer/00012.png?featherlight=false&width=90pc)
