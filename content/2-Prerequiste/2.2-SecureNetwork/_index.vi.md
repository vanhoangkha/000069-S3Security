---
title : "Truy cập mạng an toàn"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b>  2.2 </b> "
---

#### Truy cập mạng an toàn

Thực hiện cấu hình Security Group cho bài lab.

1. Trong giao diện **AWS Management Console**

   - Tìm **VPC**
   - Chọn **VPC**

![Launch CloudFormation Template](/images/2-Prerequiste/0008.png?featherlight=false&width=90pc)

2. Trong giao diện **VPC**

   - Chọn **Security Group**
   - Chọn **SID-ssh-sg**
   - Chọn **Actions**
   - Chọn **Edit inbound rules**


![Launch CloudFormation Template](/images/2-Prerequiste/0009.png?featherlight=false&width=90pc)

3. Thực hiện cấun hình **Inbound rules**

   - Chọn **Add rule**
   - Chọn Type **HTTP**, Source **Anywhere-IPv4**
   - Chọn Type **SSH**, Source **MyIP** (trường hợp không kết nối được bạn có thể thay đổi về **Anywhere-IPv4**)
   - Sau đó chọn **Save rules**


![Launch CloudFormation Template](/images/2-Prerequiste/00010.png?featherlight=false&width=90pc)

4. Kiểm tra **Security Group** đã cấu hình 


![Launch CloudFormation Template](/images/2-Prerequiste/00011.png?featherlight=false&width=90pc)
