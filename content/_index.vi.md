---
title : "Thực hành về Bảo mật S3"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

# Thực hành về bảo mật S3

Trong bài lab này, chúng ta thực hành phương pháp bảo mật tốt nhất để bảo mật dữ liệu trong Amazon S3.

Để bảo vệ dữ liệu của bạn trong Amazon S3, theo mặc định, người dùng chỉ có quyền truy cập vào tài nguyên S3 mà họ tạo. Bạn có thể cấp quyền truy cập cho người dùng khác bằng cách sử dụng một hoặc kết hợp các tính năng quản lý truy cập sau: **AWS Identity and Access Management (IAM)** để tạo người dùng và quản lý quyền truy cập tương ứng của họ; **Danh sách kiểm soát truy cập (ACL)** để cấp phép cho người dùng truy cập vào từng đối tượng; **chính sách vùng lưu trữ**  để định cấu hình quyền cho tất cả đối tượng trong một vùng lưu trữ S3 và Xác thực chuỗi ký tự truy vấn để cấp quyền truy cập trong thời gian giới hạn cho người khác bằng URL tạm thời. Amazon S3 cũng hỗ trợ Nhật ký kiểm tra liệt kê các yêu cầu được tạo đối với tài nguyên S3 để bạn có được cái nhìn toàn diện về đối tượng truy cập và dữ liệu được truy cập.

![Launch CloudFormation Template](/images/1-Introduce/s3BPIndex-02.png?featherlight=false&width=60pc)

#### Nội dung

1. [Giới thiệu](1-introduce/)
2. [Chuẩn bị](2-prerequiste/)
3. [Require HTTPS](3-requirehttps/)
4. [Require SSE-S3 Encryption](4-requiresse/)
5. [Block Public ACLs](5-blockpublicacls/)
6. [Configure S3 Block Public Access](6-s3pba/)
7. [Restrict Access to a S3 VPC Endpoint](7-vpcendpoint/)
8. [Use AWS Config Rules to Detect a Public Bucket](8-awsconfig/)
9. [Use Amazon Access Analyzer for S3](9-accessanalyzer/)
10. [Dọn dẹp tài nguyên](10-cleanup/)