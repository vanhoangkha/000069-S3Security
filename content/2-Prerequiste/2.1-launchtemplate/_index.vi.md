---
title : "Khởi tạo CloudFormation Template"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b>  2.1 </b> "
---

#### Khởi tạo CloudFormation Template

Chúng ta thực hiện khởi tạo các tài nguyên để sử dụng cho bài lab.

Cách 1: Tải **[CloudFormation template](https://raw.githubusercontent.com/AWS-First-Cloud-Journey/FCj-S3-LAB/master/sid-base-template.yaml)**

Cách 2: Tải **[CloudFormation template](https://aws-storage-immersion-day.s3.us-west-2.amazonaws.com/sid-base-template.yaml)**

1. Truy cập vào giao diện **[AWS Management Console](https://ap-southeast-1.console.aws.amazon.com/console/home?region=ap-southeast-1)**

    - Tìm **CloudFormation**
    - Chọn **CloudFormation**

![Launch CloudFormation Template](/images/2-Prerequiste/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **CloudFormation**

   - Chọn **Stack**
   - Chọn **Create stack**


![Launch CloudFormation Template](/images/2-Prerequiste/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create stack**

   - Chọn **Template is ready**
   - **Template source**, tùy theo cách template về mà bạn chọn 

   - Bạn có thể chọn đường dẫn **Amazon S3 URL**: https://aws-storage-immersion-day.s3.us-west-2.amazonaws.com/sid-base-template.yaml
   - Hoặc cũng có thể upload file.


![Launch CloudFormation Template](/images/2-Prerequiste/0003.png?featherlight=false&width=90pc)

4. Trong phần này

   - Bạn nhập **FCJ-S3-LAB** đối với **Stack name**
   - Về phần **Lab Modules**, bạn chọn **true** đối với **Deploy S3 Security Lab** (bài lab đang thực hiện) và có thể chọn thêm **Deploy Storage Performance Lab**(chuẩn bị cho lab tiếp theo).
   - Các module khác chọn **false**
   - Chọn **Next**


![Launch CloudFormation Template](/images/2-Prerequiste/0004.png?featherlight=false&width=90pc)

5. Chọn **Next**


![Launch CloudFormation Template](/images/2-Prerequiste/0005.png?featherlight=false&width=90pc)

6. Xác nhận tạo IAM cần thiết

   - Chọn **I acknowledge that AWS CloudFormation might create IAM resources with custom names.**
   - Chọn **I acknowledge that AWS CloudFormation might require the following capability: CAPABILITY_AUTO_EXPAND**
   - Chọn **Create Stack**


![Launch CloudFormation Template](/images/2-Prerequiste/0006.png?featherlight=false&width=90pc)

7. Hoàn thành quá trình tạo **Stack**

   - Khi các status của các stack chuyển sang **CREATE_COMPLETE**


![Launch CloudFormation Template](/images/2-Prerequiste/0007.png?featherlight=false&width=90pc)




