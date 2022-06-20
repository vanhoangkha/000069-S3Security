---
title : "Kết nối EC2"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b>  2.4 </b> "
---

#### Kết nối EC2

1. Truy cập giao diện **AWS Management Console**

    - Tìm **EC2**
    - Chọn **EC2**

![Connect EC2](/images/2.4-ConnectEC2/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **EC2**

    - Chọn **SID-security-instance**
    - Chọn **Connect**

![Connect EC2](/images/2.4-ConnectEC2/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Connect to instance**

   - Chọn **EC2 instance Connect**
   - Chọn **Connect**

![Connect EC2](/images/2.4-ConnectEC2/0003.png?featherlight=false&width=90pc)

4. Kết nối thành công

![Connect EC2](/images/2.4-ConnectEC2/0004.png?featherlight=false&width=90pc)

5. Chạy các lệnh sau để thiết lập AWS CLI.

```
aws configure
```

   - Sau đó sử dụng **Access key** và cấu hình.

![Connect EC2](/images/2.4-ConnectEC2/0005.png?featherlight=false&width=90pc)

6. Tạo tệp thông tin xác thực để AWS CLI sử dụng bằng lệnh sau. Điều này sẽ cho phép bạn dễ dàng chuyển đổi giữa hai người dùng IAM khác nhau.

```
cd ~/.aws
vi credentials
```

![Connect EC2](/images/2.4-ConnectEC2/0006.png?featherlight=false&width=90pc)

7. Nhập ivà nhấn enter để chuyển sang chế độ **insert**

   - Bây giờ sao chép và dán tệp thông tin xác thực được cập nhật từ trình soạn thảo văn bản của bạn vào phiên vi của bạn. Nó sẽ giống như sau, nhưng với các Khóa truy cập duy nhất của bạn.

![Connect EC2](/images/2.4-ConnectEC2/0007.png?featherlight=false&width=90pc)

8. Nhấn **es**c** rồi gõ **:wq!**và nhấn **enter** để lưu và thoát khỏi vi .


![Connect EC2](/images/2.4-ConnectEC2/0008.png?featherlight=false&width=90pc)

Bạn sẽ sử dụng phiên SSH này trong suốt lab này.


