---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Serverless URL Shortener
## Giải pháp rút gọn liên kết tối ưu chi phí và tự động mở rộng trên AWS

### 1. Tóm tắt điều hành
Dự án **Serverless URL Shortener** được thiết kế nhằm cung cấp một dịch vụ rút gọn liên kết (tương tự bit.ly) nội bộ hoặc cho cộng đồng với chi phí vận hành cực kỳ thấp. Bằng việc áp dụng hoàn toàn kiến trúc Serverless của AWS, hệ thống có khả năng tự động mở rộng (Auto-scaling) để xử lý lượng lớn truy cập mà không yêu cầu bảo trì máy chủ ảo (Zero-Ops).

### 2. Tuyên bố vấn đề
*Vấn đề hiện tại*
Các doanh nghiệp hoặc cá nhân thường phải sử dụng các dịch vụ rút gọn link của bên thứ ba, đi kèm với giới hạn số lượng link, phí duy trì cao nếu muốn dùng tên miền riêng (Custom Domain) và rủi ro bị khóa tài khoản hoặc lộ lọt dữ liệu chiến dịch Marketing.

*Giải pháp*
Tự xây dựng một hệ thống URL Shortener "của nhà trồng được" sử dụng **AWS Lambda** (xử lý logic), **Amazon API Gateway** (định tuyến HTTP), **Amazon DynamoDB** (lưu trữ link), và **Amazon S3 + CloudFront** (lưu trữ và phân phối giao diện web). Toàn bộ hệ thống chạy theo mô hình pay-as-you-go (dùng bao nhiêu trả bấy nhiêu).

*Lợi ích và hoàn vốn đầu tư (ROI)*
Chi phí vận hành hàng tháng gần như bằng $0 nhờ nằm gọn trong gói AWS Free Tier (chỉ tốn khoảng $10-$15/năm để gia hạn tên miền). Hệ thống mang lại toàn quyền kiểm soát dữ liệu, dễ dàng mở rộng để tích hợp thêm các tính năng phân tích (Analytics) sau này.

### 3. Kiến trúc giải pháp
Nền tảng áp dụng kiến trúc AWS Serverless để phục vụ cả Frontend (giao diện người dùng tĩnh) và Backend (API xử lý động).

*Dịch vụ AWS sử dụng*
- *Amazon S3*: Lưu trữ mã nguồn tĩnh (HTML, CSS, JS).
- *Amazon CloudFront*: Phân phối nội dung toàn cầu, giảm độ trễ và cung cấp SSL/TLS.
- *Amazon API Gateway*: Cửa ngõ API (HTTP API) giao tiếp với Backend và nhận tên miền tùy chỉnh.
- *AWS Lambda*: Chạy mã nguồn Python (FastAPI) để xử lý logic rút gọn và điều hướng (redirect).
- *Amazon DynamoDB*: Cơ sở dữ liệu NoSQL lưu trữ bản đồ ánh xạ giữa mã ngắn (short_id) và link gốc.
- *Amazon Route 53 & ACM*: Quản lý phân giải tên miền (DNS) và chứng chỉ bảo mật HTTPS.

### 4. Triển khai kỹ thuật
*Các giai đoạn triển khai*
Dự án được chia thành 4 giai đoạn chính trong 8 tuần thực tập:
1. *Nghiên cứu kiến trúc*: Tìm hiểu các mô hình Serverless và chọn lựa các dịch vụ phù hợp.
2. *Phát triển Backend*: Viết ứng dụng bằng Python FastAPI, đóng gói với thư viện Mangum, tạo bảng DynamoDB và deploy lên Lambda.
3. *Phát triển Frontend*: Xây dựng giao diện web thân thiện với TailwindCSS, gọi API bằng Fetch.
4. *Triển khai & Tích hợp Tên miền*: Đưa Frontend lên S3 & CloudFront. Cấu hình Custom Domain cho API Gateway qua Route 53.

### 5. Lộ trình & Mốc triển khai
- *Tuần 1-4*: Học tập các nền tảng cơ bản của AWS (IAM, EC2, S3, Networking, Serverless).
- *Tuần 5-6*: Lập trình và kiểm thử Backend (Lambda + DynamoDB).
- *Tuần 7-8*: Tích hợp Frontend, cấu hình Custom Domain và viết báo cáo tổng kết.

### 6. Ước tính ngân sách
*Chi phí hạ tầng hàng tháng (Ước tính với 100,000 lượt truy cập/tháng)*
- AWS Lambda: $0.00 (Nằm trong 1 triệu request miễn phí).
- Amazon DynamoDB: $0.00 (Nằm trong 25GB miễn phí).
- API Gateway: $0.10 (Phí rất nhỏ cho HTTP API).
- CloudFront & S3: ~$0.50 (Lưu lượng băng thông thấp).
- Route 53 (Tên miền): ~$10 - $15 / năm (Phí cố định của ICANN).
*Tổng chi phí duy trì*: ~ $1/tháng (chưa tính phí mua tên miền hàng năm).

### 7. Đánh giá rủi ro
*Ma trận rủi ro*
- Lỗi mã nguồn Backend: Ảnh hưởng trung bình, xác suất thấp (Đã test kỹ trên local).
- Hết dung lượng Free Tier: Ảnh hưởng thấp, xác suất rất thấp (Vì hệ thống tối ưu).
- Cấu hình DNS bị lỗi: Ảnh hưởng cao, xác suất trung bình.

*Chiến lược giảm thiểu*
- Sử dụng API Gateway Throttling để chống DDoS.
- Đặt giới hạn ngân sách (AWS Budgets) để nhận cảnh báo qua email.
- Tắt tính năng Evaluate target health trong Route 53 để tránh các lỗi ánh xạ.

### 8. Kết quả kỳ vọng
Một hệ thống rút gọn liên kết hoạt động trơn tru 24/7 dưới tên miền riêng. Dự án này không chỉ chứng minh khả năng áp dụng kiến trúc Serverless vào thực tế mà còn là nền tảng vững chắc để phát triển thành một hệ thống SaaS (Software as a Service) thương mại hóa trong tương lai.
