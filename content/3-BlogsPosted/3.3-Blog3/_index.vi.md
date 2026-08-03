---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Host giao diện Web tĩnh "rẻ như cho" nhưng tốc độ bàn thờ với Amazon S3 và CloudFront!

Xong phần Backend, tới phần giao diện (Frontend) của ứng dụng URL Shortener. Giao diện của mình chỉ đơn thuần là HTML, Javascript và TailwindCSS. Nếu chạy một server EC2 chỉ để host mấy file tĩnh này thì quá lãng phí.

Do đó, giải pháp "quốc dân" trên AWS mà mình sử dụng là kết hợp **Amazon S3** và **Amazon CloudFront**:

1️⃣ **Amazon S3 (Lưu trữ):** Chuyển S3 bucket sang chế độ Static Website Hosting. Nơi đây đóng vai trò như ổ cứng chứa source code UI của mình.
2️⃣ **Amazon CloudFront (CDN):** Đây là "vũ khí bí mật". CloudFront phân phối nội dung (cache) tới các Edge Locations trên toàn thế giới. Dù người dùng ở Mỹ hay Việt Nam truy cập, web vẫn load ngay lập tức.
3️⃣ **Bảo mật & Custom Domain:** CloudFront giúp mình dễ dàng ép buộc (force) kết nối HTTPS thông qua chứng chỉ SSL/TLS miễn phí từ AWS Certificate Manager (ACM), và trỏ tên miền cá nhân bằng Route 53.

💡 **Kết quả:** Mình có một website frontend khả năng chịu tải hàng chục ngàn truy cập một lúc mà không sập, trong khi chi phí mỗi tháng chỉ bằng... tiền giữ xe.

Anh em thường host các dự án React/Vue/HTML tĩnh bằng dịch vụ gì trên AWS? 👇

---
**Tài liệu tham khảo:**
- [Host a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
- [Amazon CloudFront](https://aws.amazon.com/cloudfront/)
- [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/)
