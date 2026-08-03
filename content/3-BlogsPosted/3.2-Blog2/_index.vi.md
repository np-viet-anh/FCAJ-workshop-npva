---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Tại sao mình lại chọn Amazon DynamoDB cho ứng dụng URL Shortener?

Khi xây dựng một ứng dụng rút gọn link (URL Shortener), một trong những bài toán quan trọng nhất là tốc độ truy xuất dữ liệu: "Làm sao để khi người dùng click vào link ngắn, hệ thống phải ngay lập tức tìm ra link gốc và redirect trong chưa tới 1 giây?"

Mình đã thử nghiệm với **Amazon DynamoDB** và thực sự ấn tượng vì những lý do sau:

🔹 **Kiến trúc Key-Value hoàn hảo:** URL Shortener bản chất chỉ cần ánh xạ mã `short_id` thành `long_url`. DynamoDB là cơ sở dữ liệu NoSQL sinh ra để xử lý các truy vấn Key-Value như vậy một cách cực kỳ tối ưu.
🔹 **Độ trễ mili-giây (Single-digit millisecond latency):** Tốc độ đọc/ghi dữ liệu luôn được đảm bảo ở mức dưới 10 mili-giây ở bất kỳ quy mô nào.
🔹 **Serverless Database:** Không cài đặt, không bảo trì cấu hình cụm database (như RDS). Cứ tạo bảng là xài, tự động scale. 

Quá trình cấu hình để AWS Lambda giao tiếp với DynamoDB bằng `boto3` cũng rất đơn giản. Tuy nhiên mình có một bài học là cần lưu ý cấu hình IAM Role thật chuẩn (least privilege) để Lambda chỉ có quyền thao tác trên đúng table đó thôi.

Nếu bạn xây dựng hệ thống tương tự, bạn sẽ chọn RDS, ElastiCache (Redis) hay DynamoDB? Cùng thảo luận nhé! 🚀

---
**Tài liệu tham khảo:**
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
- [Boto3 DynamoDB Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html)
