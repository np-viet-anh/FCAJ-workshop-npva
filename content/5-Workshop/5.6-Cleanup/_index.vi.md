---
title : "Dọn dẹp tài nguyên"
date: 2026-07-25
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Quy trình làm sạch tài nguyên (Cleanup)

Sau khi hoàn thành bài thực hành và báo cáo, nếu bạn không có nhu cầu tiếp tục sử dụng ứng dụng trong thực tế, hãy dọn dẹp các tài nguyên đã khởi tạo để tránh phát sinh bất kỳ khoản phí ngoài ý muốn nào trên tài khoản AWS của bạn.

> [!WARNING]
> Việc giữ lại Tên miền (Domain Name) trên Route 53 sẽ phát sinh chi phí duy trì hàng năm (khoảng $10 - $16/năm). Các dịch vụ Serverless khác (S3, Lambda, API Gateway, DynamoDB) chỉ tính phí dựa trên lưu lượng sử dụng, nếu không có truy cập sẽ gần như bằng 0, nhưng vẫn nên được dọn dẹp để giữ tài khoản gọn gàng.

1. **Amazon CloudFront:**
   - Chọn Distribution, nhấn **Disable**.
   - Đợi sau khi trạng thái chuyển sang Disabled hoàn toàn, nhấn **Delete**.

2. **Amazon S3:**
   - Vào S3 Bucket chứa mã nguồn tĩnh.
   - Chọn **Empty** (Làm trống toàn bộ file) và gõ xác nhận `permanently delete`.
   - Chọn **Delete bucket** để xóa hoàn toàn Bucket.

3. **Amazon API Gateway:**
   - Trong giao diện API Gateway, vào phần Custom domain names và **Delete** domain đã map.
   - Trở lại danh sách APIs, chọn HTTP API đã tạo, nhấn nút **Delete**.

4. **AWS Lambda:**
   - Tìm đến Function `URLShortener`, trong mục Actions chọn **Delete**.

5. **Amazon DynamoDB:**
   - Vào phần Tables, chọn bảng `URLShortener` và tiến hành xóa bảng (**Delete table**).

6. **AWS Certificate Manager (ACM):**
   - Chọn các chứng chỉ đã tạo và thao tác **Delete**.

7. **Amazon Route 53 (Tùy chọn):**
   - Vào Hosted zones, xóa các bản ghi thủ công (trừ NS và SOA), sau đó xóa Hosted zone.
   - *Lưu ý:* Việc hủy đăng ký (delete registration) tên miền quốc tế không được hỗ trợ hoàn tiền sau khi đã mua. Bạn có thể vô hiệu hóa tự động gia hạn (Disable auto-renew) trong mục Registered domains.
