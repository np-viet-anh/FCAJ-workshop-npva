---
title : "Tên miền tùy chỉnh (Custom Domain)"
date: 2026-08-30 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### 1. Ý nghĩa của tên miền tùy chỉnh

Mặc định, AWS API Gateway sẽ cấp phát một đường dẫn khá dài dạng `https://d-xxxx.execute-api.ap-southeast-2.amazonaws.com`. Để hệ thống Rút gọn liên kết đúng nghĩa là "rút gọn", chúng ta cần ánh xạ một tên miền thật ngắn (ví dụ: `nuguseyo.com`) trực tiếp vào API Gateway. Lúc này, liên kết tạo ra sẽ có dạng chuyên nghiệp: `https://nuguseyo.com/10Ugru`.

#### 2. Sở hữu tên miền qua Amazon Route 53

- Truy cập dịch vụ **Route 53** -> **Registered domains** để mua và đăng ký tên miền mong muốn.
- Sau khi thanh toán, cần xác thực địa chỉ Email với tổ chức ICANN (thông qua link gửi về email đăng ký) để đảm bảo tên miền không bị khóa (ClientHold).

#### 3. Xin chứng chỉ SSL/TLS (AWS Certificate Manager - ACM)

- Chuyển sang dịch vụ **AWS Certificate Manager (ACM)**, chọn **Request a public certificate**.
- Nhập tên miền (ví dụ: `nuguseyo.com` và `*.nuguseyo.com`).
- Lựa chọn phương pháp xác thực DNS (DNS validation). AWS sẽ tự động sinh ra các bản ghi CNAME, bạn chỉ cần bấm **Create records in Route 53** để tự động thêm vào DNS. Chờ trạng thái chuyển sang **Issued**.

#### 4. Cấu hình Custom Domain trong API Gateway

- Trong giao diện API Gateway, chọn mục **Custom domain names** -> **Create**.
- Khai báo tên miền, chọn Endpoint Type là `Regional`, gắn kèm chứng chỉ ACM vừa xin, và chính sách bảo mật TLS 1.2.
- Sang tab **API mappings**, cấu hình ánh xạ Domain này về HTTP API đã tạo ở Stage `$default`.

#### 5. Trỏ DNS tại Route 53

- Trong Hosted zone của Route 53, tạo một bản ghi **A (Alias)**.
- Bật công tắc Alias, trỏ tới **API Gateway API** và chọn đúng khu vực cũng như ID Custom Domain Name được cung cấp.
- *Chú ý:* Tắt bỏ tùy chọn **Evaluate target health** để tránh việc Route 53 từ chối trả về địa chỉ IP khi hệ thống không hỗ trợ cơ chế Health check truyền thống.
- Chờ vài phút để DNS cập nhật, và hệ thống Rút gọn siêu ngắn đã hoàn thiện 100%!
