---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Giải pháp lưu trữ Web tĩnh hiệu năng cao và tối ưu chi phí với Amazon S3 và CloudFront

Đối với thành phần giao diện (Frontend) của các ứng dụng web tĩnh hiện đại, hệ thống thường sử dụng các công nghệ biên dịch phía máy khách như React, Vue, hoặc đơn thuần là HTML, Javascript và CSS. Việc triển khai các tệp tĩnh này trên một máy chủ EC2 truyền thống sẽ không tận dụng được tối đa hiệu suất và gây lãng phí tài nguyên máy tính.

Do đó, kiến trúc tiêu chuẩn thường được áp dụng trên đám mây AWS là sự kết hợp giữa **Amazon S3** và **Amazon CloudFront**:

1. **Amazon S3 (Lưu trữ):** Dịch vụ S3 cung cấp tính năng Static Website Hosting, đóng vai trò là không gian lưu trữ an toàn và bền bỉ cho toàn bộ mã nguồn giao diện đã được biên dịch của ứng dụng.
2. **Amazon CloudFront (Mạng phân phối nội dung - CDN):** CloudFront đảm nhiệm việc phân phối và lưu trữ bộ nhớ đệm (cache) nội dung tại các Edge Locations trên toàn cầu. Điều này giúp giảm thiểu độ trễ mạng đáng kể, đảm bảo trang web được tải nhanh chóng bất kể vị trí địa lý của người dùng.
3. **Bảo mật và Tên miền tùy chỉnh:** CloudFront hỗ trợ thiết lập kết nối mã hóa HTTPS thông qua chứng chỉ bảo mật SSL/TLS được cấp phát miễn phí từ AWS Certificate Manager (ACM), đồng thời có thể dễ dàng kết hợp với Amazon Route 53 để định tuyến lưu lượng truy cập tới tên miền tùy chỉnh.

**Kết quả:** Giải pháp này mang lại một nền tảng frontend có khả năng đáp ứng đồng thời khối lượng truy cập lớn với hiệu năng cao, trong khi chi phí duy trì hàng tháng được tối ưu hóa ở mức thấp nhất nhờ cơ chế tính phí theo lượng sử dụng thực tế (pay-as-you-go).

---
**Tài liệu tham khảo:**
- [Host a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
- [Amazon CloudFront](https://aws.amazon.com/cloudfront/)
- [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/)
