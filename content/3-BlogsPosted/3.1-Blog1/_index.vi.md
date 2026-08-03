---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Đưa FastAPI (Python) lên AWS Lambda một cách dễ dàng với thư viện Mangum!

[CHIA SẺ KINH NGHIỆM] Xây dựng Backend hoàn toàn Serverless cực nhanh và tiết kiệm chi phí! ☁️

Trong quá trình làm project URL Shortener, mình đã quyết định sử dụng kiến trúc hoàn toàn không máy chủ (Serverless) cho phần Backend thay vì thuê EC2. 

Stack mình chọn là **AWS Lambda** + **API Gateway** kết hợp với **FastAPI (Python)**. Nhưng làm sao để một framework web như FastAPI có thể chạy mượt mà trên Lambda? Câu trả lời chính là sử dụng thư viện **Mangum**.

✨ **Lợi ích mà stack này mang lại:**
- **Zero-ops:** Không cần phải quản lý OS, không lo việc scale server. Lambda tự động scale dựa trên số lượng truy cập.
- **Tiết kiệm chi phí:** Trong giai đoạn dev và ứng dụng nhỏ, chi phí chạy gần như bằng $0 nhờ AWS Free Tier. Mình chỉ trả tiền cho số milliseconds mà code chạy.
- **Tốc độ code:** Code bằng FastAPI rất nhàn và hiện đại, sinh sẵn document Swagger/OpenAPI.

Có anh em nào trong group cũng đang ghiền hệ sinh thái Serverless trên AWS giống mình không? Mọi người thường dùng API Gateway hay ALB để trigger Lambda? Chia sẻ cùng mình nhé! 👇

---
**Tài liệu tham khảo:**
- [AWS Lambda](https://aws.amazon.com/lambda/)
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Mangum](https://mangum.io/)
