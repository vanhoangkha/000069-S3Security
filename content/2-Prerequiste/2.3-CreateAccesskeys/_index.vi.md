---
title : "Tạo khóa truy cập"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b>  2.3 </b> "
---

#### Tạo khóa truy cập cho người dùng IAM

Khóa truy cập là thông tin xác thực dài hạn cho người dùng IAM hoặc người dùng gốc tài khoản AWS. Bạn có thể sử dụng các khóa truy cập để ký các yêu cầu có lập trình tới AWS CLI hoặc AWS API (trực tiếp hoặc sử dụng AWS SDK). Khóa truy cập bao gồm hai phần: ID khóa truy cập (ví dụ: AKIAIOSFODNN7EXAMPLE) và khóa truy cập bí mật (ví dụ: wJalrXUtnFEMI / K7MDENG / bPxRfiCYEXAMPLEKEY). Giống như tên người dùng và mật khẩu, bạn phải sử dụng cả ID khóa truy cập và khóa truy cập bí mật cùng nhau để xác thực các yêu cầu của mình. Quản lý khóa truy cập của bạn một cách an toàn như khi bạn sử dụng tên người dùng và mật khẩu của mình.

1. Truy cập giao diên **AWS Management Console**

   - Tìm **IAM**
   - Chọn **IAM**

![Access Key](/images/2.3-Accesskey/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **IAM**

   - Chọn **Users**
   - Chúng ta có 2 user **SID-lab-user1** và **SID-lab-user2**
   - Chọn user **SID-lab-user1**

![Access Key](/images/2.3-Accesskey/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **SID-lab-user1**

   - Chọn **Security credentials**
   - Chọn **Create access key**

![Access Key](/images/2.3-Accesskey/0003.png?featherlight=false&width=90pc)

4. Tạo **access key** thành công. 

    - Xem chi tiết key
    - Chọn **Download.csv file**

![Access Key](/images/2.3-Accesskey/0004.png?featherlight=false&width=90pc)

5. Thực hiện tương tự với **SID-lab-user2**

   - Sau đó ghi chú lại thông tin của 2 key.

![Access Key](/images/2.3-Accesskey/0005.png?featherlight=false&width=90pc)