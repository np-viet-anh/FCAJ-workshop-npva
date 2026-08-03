---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Tối ưu hóa truy xuất dữ liệu tốc độ cao với Amazon DynamoDB

Trong thiết kế hệ thống hiện đại, một trong những yêu cầu kỹ thuật khắt khe nhất là tốc độ truy xuất dữ liệu. Hệ thống cần đảm bảo khả năng tra cứu và phản hồi thông tin tới người dùng trong thời gian tối thiểu.

**Amazon DynamoDB** thường được lựa chọn làm cơ sở dữ liệu chính để giải quyết bài toán này nhờ vào những yếu tố kỹ thuật sau:

- **Kiến trúc Key-Value hiệu năng cao:** Rất nhiều bài toán thực tế chỉ yêu cầu thực hiện thao tác ánh xạ từ một khóa (key) sang một giá trị (value). DynamoDB là cơ sở dữ liệu NoSQL được tối ưu hóa đặc biệt cho các truy vấn theo mô hình Key-Value, mang lại tốc độ xử lý vượt trội.
- **Độ trễ mili-giây (Single-digit millisecond latency):** Tốc độ đọc và ghi dữ liệu được duy trì ổn định ở mức dưới 10 mili-giây, bất kể quy mô của cơ sở dữ liệu có mở rộng đến mức độ nào.
- **Cơ sở dữ liệu Serverless:** Giảm thiểu hoàn toàn công sức cài đặt, phân bổ tài nguyên và bảo trì cấu hình cụm máy chủ cơ sở dữ liệu (như khi sử dụng các hệ quản trị CSDL quan hệ truyền thống). Quá trình thay đổi quy mô tài nguyên được thực hiện hoàn toàn tự động dựa trên nhu cầu thực tế.

Việc tích hợp giữa các dịch vụ điện toán đám mây và DynamoDB diễn ra vô cùng thuận lợi thông qua AWS SDK. Tuy nhiên, một lưu ý quan trọng trong quá trình triển khai là cần tuân thủ nghiêm ngặt nguyên tắc cấp quyền tối thiểu (least privilege) khi cấu hình IAM, đảm bảo các dịch vụ chỉ có quyền thao tác trên đúng những bảng dữ liệu được chỉ định.

---
**Tài liệu tham khảo:**
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
- [AWS SDK / Boto3 DynamoDB Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html)
