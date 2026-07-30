---
title : "Chuẩn bị môi trường"
date: 2026-07-25
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Các công cụ và dịch vụ cần thiết

Trước khi tiến hành triển khai dự án, chúng ta cần chuẩn bị các môi trường và tài nguyên sau:

1. **Tài khoản AWS (AWS Account):**
   - Cần có một tài khoản AWS đang trong trạng thái hoạt động (khuyến nghị dùng tài khoản mới để tận dụng gói Free Tier).
   - Đã tạo IAM User có quyền quản trị (AdministratorAccess) hoặc ít nhất có các quyền truy cập vào S3, Lambda, API Gateway, DynamoDB, CloudFront, Route 53 và ACM.

2. **Môi trường phát triển cục bộ (Local Development):**
   - **Visual Studio Code (VS Code):** Hoặc bất kỳ IDE nào hỗ trợ lập trình Python và Web.
   - **Python 3.10+**: Đã được cài đặt và cấu hình biến môi trường (PATH) trên máy tính cá nhân (Windows/Mac/Linux).
   - Khuyến nghị cài đặt **AWS CLI** và cấu hình `aws configure` với Access Key/Secret Key để phục vụ quá trình test local kết nối với DynamoDB.

3. **Mã nguồn (Source Code):**
   - Cấu trúc dự án gồm hai thư mục chính: `backend` (chứa code FastAPI) và `frontend` (chứa code HTML/JS/CSS).

4. **Tên miền tùy chỉnh (Optional nhưng khuyến nghị):**
   - Một tên miền ngắn (ví dụ: `domain.link`, `abc.to`) được đăng ký qua Amazon Route 53 hoặc nhà cung cấp bên thứ ba (Namecheap, Hostinger) để làm Domain rút gọn thực tế.
