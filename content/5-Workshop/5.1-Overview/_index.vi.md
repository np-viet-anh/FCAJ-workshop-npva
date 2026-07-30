---
title : "Tổng quan hệ thống"
date: 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Kiến trúc Serverless URL Shortener

Hệ thống được thiết kế theo kiến trúc Serverless hiện đại, sử dụng các dịch vụ quản lý hoàn toàn của AWS:

1. **Người dùng cuối (End Users):** Truy cập vào giao diện web thông qua một tên miền ngắn (Custom Domain).
2. **Amazon Route 53:** Hệ thống phân giải tên miền (DNS) trỏ tên miền tùy chỉnh về Amazon CloudFront (cho Frontend) và API Gateway (cho Backend).
3. **Amazon CloudFront:** Mạng phân phối nội dung (CDN) lưu bộ nhớ đệm toàn cầu, giúp tải giao diện siêu tốc và cung cấp chứng chỉ HTTPS (thông qua AWS Certificate Manager).
4. **Amazon S3:** Nơi lưu trữ an toàn các tệp tin giao diện tĩnh tĩnh (HTML, CSS, JS).
5. **Amazon API Gateway:** Đóng vai trò là HTTP API, tiếp nhận các yêu cầu tạo link hoặc chuyển hướng (redirect) từ người dùng và chuyển đến AWS Lambda.
6. **AWS Lambda:** Dịch vụ điện toán Serverless, chạy mã nguồn Python (FastAPI) để xử lý logic rút gọn link và tạo mã hash độc nhất.
7. **Amazon DynamoDB:** Cơ sở dữ liệu NoSQL với độ trễ tính bằng mili-giây, lưu trữ cặp giá trị `{short_id: long_url}`.

---

Sự kết hợp này giúp ứng dụng có khả năng chịu tải hàng ngàn truy cập đồng thời mà không cần can thiệp vận hành (zero ops), đồng thời tiết kiệm chi phí tối đa.
