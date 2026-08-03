---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Triển khai FastAPI (Python) trên AWS Lambda bằng thư viện Mangum

Trong quá trình phát triển dự án URL Shortener, nhóm đã quyết định ứng dụng kiến trúc Serverless (không máy chủ) cho thành phần Backend thay vì triển khai trên các máy chủ ảo EC2 truyền thống.

Công nghệ được lựa chọn bao gồm **AWS Lambda**, **API Gateway** kết hợp với framework **FastAPI (Python)**. Để ứng dụng FastAPI có thể tương thích và hoạt động ổn định trên môi trường AWS Lambda, dự án sử dụng thư viện **Mangum** làm bộ chuyển đổi.

**Các ưu điểm của giải pháp này:**
- **Không yêu cầu vận hành (Zero-ops):** Khắc phục hoàn toàn gánh nặng quản trị hệ điều hành và mở rộng máy chủ. AWS Lambda sẽ tự động thay đổi quy mô dựa trên lưu lượng truy cập thực tế.
- **Tối ưu hóa chi phí:** Trong giai đoạn phát triển và đối với các ứng dụng quy mô vừa và nhỏ, chi phí vận hành được giảm thiểu đáng kể, thường được bao phủ bởi gói AWS Free Tier. Chi phí chỉ phát sinh dựa trên thời gian thực thi mã nguồn.
- **Tốc độ phát triển:** Quá trình lập trình với FastAPI diễn ra thuận lợi, hiện đại và tự động tạo ra tài liệu API theo chuẩn Swagger/OpenAPI.

Phương pháp tiếp cận Serverless đang ngày càng chứng minh được hiệu quả trong việc xây dựng các ứng dụng trên đám mây AWS.

---
**Tài liệu tham khảo:**
- [AWS Lambda](https://aws.amazon.com/lambda/)
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Mangum](https://mangum.io/)
