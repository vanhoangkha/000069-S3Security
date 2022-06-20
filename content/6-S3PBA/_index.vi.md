---
title : "Định cấu hình S3 Block Public Access"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Định cấu hình S3 Block Public Access

Chỉ cần một vài lần chọn trong bảng điều khiển quản lý S3, bạn có thể áp dụng **S3 Block Public Access** cho mọi vùng lưu trữ trong tài khoản của mình – cả vùng lưu trữ hiện có và bất kỳ vùng lưu trữ mới nào được tạo trong tương lai – đồng thời đảm bảo rằng không có quyền truy cập công cộng vào bất kỳ đối tượng nào. Các cài đặt S3 Block Public Access thay thế quyền S3 cho phép truy cập công cộng, giúp quản trị viên tài khoản dễ dàng thiết lập hoạt động kiểm soát tập trung để ngăn chặn sự thay đổi trong cấu hình bảo mật, bất kể cách thêm đối tượng hay cách tạo vùng lưu trữ.

![Launch CloudFormation Template](/images/1-Introduce/0003.png?featherlight=false&width=60pc)

#### Thực hành

1. Truy cập vào **S3**

    - Chọn **sid-security-xxxxxxxx**

![SSE](/images/6-S3Block/0001.png?featherlight=false&width=90pc)

2. Chọn **Permissions**

   - Phần **Bucket Policy**, chọn **Delete**

![SSE](/images/6-S3Block/0002.png?featherlight=false&width=90pc)

3. Thực hiện điền **Delete** và chọn **Delete** để xác nhận xoá.

![SSE](/images/6-S3Block/0003.png?featherlight=false&width=90pc)

4. Trong phần **Block public access (bucket settings)**

   - Chọn **Edit**

![SSE](/images/6-S3Block/0004.png?featherlight=false&width=90pc)

5. Thực hiện chỉnh sửa

   - Chọn **Block public access to buckets and objects granted through new access control lists (ACLs)**
   - Chọn **Save changes**

![SSE](/images/6-S3Block/0005.png?featherlight=false&width=90pc)

6. Điền **confirm** và sau đó chọn **Confirm**

![SSE](/images/6-S3Block/0006.png?featherlight=false&width=90pc)

7. Sau khi thay đổi, chúng ta quan sát thấy **Block all public access** đã **On**

![SSE](/images/6-S3Block/0007.png?featherlight=false&width=90pc)

8. Quay lại giao diện **SSH**

```
aws s3api put-object --key text01 --body textfile --profile user1 --bucket ${bucket}  
```
Yêu cầu thành công vì deafult cho một đối tượng ACL là riêng tư.

![SSE](/images/6-S3Block/0008.png?featherlight=false&width=90pc)

9. Tiếp tục chạy lệnh

```
aws s3api put-object --key text01 --body textfile --acl public-read --profile user1 --bucket ${bucket}  
```

Yêu cầu không thành công vì chính sách nhóm hạn chế ACL đọc công khai.

![SSE](/images/6-S3Block/0009.png?featherlight=false&width=90pc)

10. Thực hiện truy cập vào **S3**

    - Chọn **Buckets**
    - Chọn **sid-security-xxx** bucket

![SSE](/images/6-S3Block/00010.png?featherlight=false&width=90pc)

11. Trong giao diệm **bucket**

    - Chọn **Permissions**
    - Đối với **Block public access (bucket settings)**, chọn **Edit**

![SSE](/images/6-S3Block/00011.png?featherlight=false&width=90pc)

12. Thực hiện chỉnh sửa

    - Chọn **Block public access to buckets and objects granted through new access control lists (ACLs)**
    - Chọn **Save changes**

![SSE](/images/6-S3Block/00012.png?featherlight=false&width=90pc)

13. Điền **confirm** và chọn **Confirm**

![SSE](/images/6-S3Block/00013.png?featherlight=false&width=90pc)

14. Hoàn tất chỉnh sửa.

![SSE](/images/6-S3Block/00014.png?featherlight=false&width=90pc)

