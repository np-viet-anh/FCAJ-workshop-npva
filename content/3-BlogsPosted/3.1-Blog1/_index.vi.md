---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Triển khai FastAPI (Python) trên AWS Lambda bằng thư viện Mangum

Kiến trúc Serverless (không máy chủ) đang trở thành một tiêu chuẩn mới trong việc phát triển ứng dụng Backend nhờ khả năng tối ưu hóa cả về chi phí lẫn công sức vận hành. 

Một trong những công nghệ phổ biến được lựa chọn là sự kết hợp giữa **AWS Lambda**, **API Gateway** và framework **FastAPI (Python)**. Tuy nhiên, để một ứng dụng web framework truyền thống như FastAPI có thể tương thích và hoạt động ổn định trên môi trường Serverless của AWS Lambda, giải pháp tối ưu là sử dụng thư viện **Mangum** làm bộ chuyển đổi (adapter).

**Các ưu điểm của kiến trúc này:**
- **Không yêu cầu vận hành (Zero-ops):** Khắc phục hoàn toàn gánh nặng quản trị hệ điều hành và mở rộng máy chủ. AWS Lambda sẽ tự động thay đổi quy mô dựa trên lưu lượng truy cập thực tế của hệ thống.
- **Tối ưu hóa chi phí:** Đối với các ứng dụng quy mô vừa và nhỏ hoặc trong giai đoạn thử nghiệm, chi phí vận hành được giảm thiểu đáng kể, phần lớn được bao phủ bởi gói AWS Free Tier. Chi phí chỉ phát sinh dựa trên số mili-giây thực thi mã nguồn.
- **Tốc độ phát triển:** Quá trình lập trình với FastAPI diễn ra thuận lợi, hiện đại và hỗ trợ tự động tạo ra tài liệu API theo chuẩn Swagger/OpenAPI.

Phương pháp tiếp cận Serverless kết hợp FastAPI và Mangum đang chứng minh được hiệu quả mạnh mẽ trong việc xây dựng các API trên đám mây AWS.

---
**Tài liệu tham khảo:**
- [AWS Lambda](https://aws.amazon.com/lambda/)
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Mangum](https://mangum.io/)

---
**Bài đăng trên cộng đồng:**
- [Xem bài blog trên nhóm AWS Study Group FCJ](https://www.facebook.com/groups/awsstudygroupfcj/posts/2233035990794694/)
