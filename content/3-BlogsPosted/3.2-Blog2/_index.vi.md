---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Lý do lựa chọn Amazon DynamoDB cho ứng dụng URL Shortener

Khi thiết kế hệ thống rút gọn liên kết (URL Shortener), một trong những yêu cầu kỹ thuật khắt khe nhất là tốc độ truy xuất dữ liệu. Hệ thống cần đảm bảo khả năng tra cứu nhanh chóng liên kết gốc từ mã rút gọn và thực hiện chuyển hướng trong thời gian tối thiểu.

Dự án đã lựa chọn **Amazon DynamoDB** làm cơ sở dữ liệu chính dựa trên những yếu tố kỹ thuật sau:

- **Kiến trúc Key-Value phù hợp:** Ứng dụng URL Shortener về cơ bản chỉ thực hiện thao tác ánh xạ từ mã `short_id` sang `long_url`. DynamoDB là cơ sở dữ liệu NoSQL được tối ưu hóa đặc biệt cho các truy vấn theo mô hình Key-Value này.
- **Độ trễ mili-giây (Single-digit millisecond latency):** Tốc độ đọc và ghi dữ liệu được duy trì ổn định ở mức dưới 10 mili-giây, bất kể quy mô của hệ thống mở rộng đến đâu.
- **Cơ sở dữ liệu Serverless:** Giảm thiểu hoàn toàn công sức cài đặt và bảo trì cấu hình cụm máy chủ cơ sở dữ liệu (so với các giải pháp như Amazon RDS). Quá trình mở rộng tài nguyên được thực hiện hoàn toàn tự động.

Việc tích hợp giữa AWS Lambda và DynamoDB thông qua thư viện `boto3` diễn ra thuận lợi. Tuy nhiên, một lưu ý quan trọng trong quá trình triển khai là cần tuân thủ nghiêm ngặt nguyên tắc cấp quyền tối thiểu (least privilege) khi cấu hình IAM Role, đảm bảo AWS Lambda chỉ có quyền thao tác trên đúng bảng dữ liệu được chỉ định.

---
**Tài liệu tham khảo:**
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
- [Boto3 DynamoDB Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html)
