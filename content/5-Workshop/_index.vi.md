---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Xây dựng ứng dụng Serverless URL Shortener trên AWS

#### Tổng quan

Trong workshop này, chúng ta sẽ xây dựng một ứng dụng rút gọn liên kết (URL Shortener) hoàn chỉnh, tương tự như bit.ly hay tinyurl. 
Dự án được triển khai 100% trên kiến trúc **Serverless** của AWS, giúp tối ưu hóa chi phí (gần như $0 với Free Tier), tự động mở rộng (auto-scaling) mượt mà mà không cần phải quản lý bất kỳ máy chủ ảo (EC2) nào.

Ứng dụng chia làm hai phần tách biệt:
+ **Frontend:** Được xây dựng bằng HTML, Javascript và Tailwind CSS, lưu trữ dưới dạng trang web tĩnh trên **Amazon S3** và phân phối toàn cầu qua mạng lưới CDN **Amazon CloudFront**.
+ **Backend:** Viết bằng Python (FastAPI), được đóng gói qua thư viện Mangum để chạy trên **AWS Lambda**, sử dụng **Amazon API Gateway** làm cửa ngõ giao tiếp HTTP API, và lưu trữ dữ liệu vào **Amazon DynamoDB**.

#### Nội dung

1. [Tổng quan hệ thống](5.1-Overview/)
2. [Chuẩn bị môi trường](5.2-Preparation/)
3. [Xây dựng Database & Backend](5.3-Database-and-Backend/)
4. [Triển khai Frontend](5.4-Frontend-Deployment/)
5. [Cấu hình Tên miền tùy chỉnh (Custom Domain)](5.5-Custom-Domain/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)
