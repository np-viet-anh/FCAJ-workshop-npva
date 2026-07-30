---
title : "Triển khai Frontend"
date: 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### 1. Hoàn thiện mã nguồn Frontend

- Giao diện được thiết kế đơn giản và hiện đại bằng **Tailwind CSS**.
- Trong file `script.js`, cần cập nhật biến `API_BASE_URL` trỏ tới đường dẫn (Invoke URL) của **API Gateway** vừa được khởi tạo ở bước trước.
```javascript
const API_BASE_URL = 'https://<api-id>.execute-api.<region>.amazonaws.com';
```

#### 2. Lưu trữ Web Tĩnh trên Amazon S3

- Tạo một **S3 Bucket** mới. Bỏ chọn "Block all public access" để cho phép Internet truy cập vào dữ liệu.
- Mở tab **Properties**, cuộn xuống phần **Static website hosting**, chọn **Enable** và điền `index.html` vào ô Index document.
- Cấu hình **Bucket Policy** cấp quyền `s3:GetObject` cho phép mọi người xem nội dung web.
- Tải toàn bộ mã nguồn Frontend (`index.html`, `script.js`, `style.css`) lên thư mục gốc của Bucket. Lúc này web đã có thể truy cập qua S3 Website Endpoint.

#### 3. Tăng tốc phân phối bằng Amazon CloudFront

- Truy cập **Amazon CloudFront** và tạo mới một Distribution.
- Tại mục **Origin domain**, chọn S3 bucket vừa tạo.
- Giữ nguyên các thiết lập mặc định (cấu hình WAF cơ bản mặc định đi kèm sẽ tự động bảo vệ web khỏi các cuộc tấn công phổ biến).
- Thiết lập **Default root object** là `index.html`.
- Chờ CloudFront triển khai (Deploying), sau đó bạn sẽ nhận được một đường dẫn có đuôi `.cloudfront.net`. Đây chính là đường dẫn web toàn cầu với giao thức HTTPS được bảo mật, mang lại tốc độ tải trang tối ưu cho mọi người dùng trên toàn thế giới.
