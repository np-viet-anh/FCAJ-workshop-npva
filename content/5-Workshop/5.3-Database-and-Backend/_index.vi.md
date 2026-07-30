---
title : "Xây dựng Database & Backend"
date: 2026-07-25
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### 1. Khởi tạo Amazon DynamoDB

DynamoDB là dịch vụ cơ sở dữ liệu NoSQL với khả năng mở rộng tự động.
- Truy cập vào **Amazon DynamoDB** trên AWS Console, chọn **Create table**.
- **Table name**: `URLShortener`
- **Partition key**: `short_id` (Kiểu String).
- Giữ nguyên các cài đặt mặc định (Default settings) và tiến hành tạo bảng.

#### 2. Phát triển Backend với FastAPI

- Cài đặt các thư viện cần thiết trong Python: `fastapi`, `uvicorn`, `boto3`, `mangum`, `pydantic`.
- Hàm `Mangum` đóng vai trò chuyển đổi định dạng request của API Gateway thành ASGI tương thích với FastAPI.
- Code kết nối DynamoDB (`database.py`):
```python
import boto3
dynamodb = boto3.resource('dynamodb', region_name='ap-southeast-2')
table = dynamodb.Table('URLShortener')
# Các hàm put_item và get_item
```
- Endpoint xử lý logic (`main.py`): Gồm API `POST /api/shorten` để tạo link ngắn và API `GET /{short_id}` để redirect người dùng về trang gốc.

#### 3. Triển khai lên AWS Lambda

- Đóng gói mã nguồn cùng các thư viện phụ thuộc thành file `function.zip`.
  *Lưu ý cho người dùng Windows: Cần sử dụng tham số `--platform manylinux2014_x86_64` khi `pip install` để tương thích với môi trường Linux của AWS Lambda.*
- Tạo một hàm Lambda mới với Runtime là **Python 3.10**.
- Cấp quyền truy cập DynamoDB cho Lambda (Thêm policy `AmazonDynamoDBFullAccess` vào Execution Role).
- Tải file `function.zip` lên Lambda. Cấu hình **Handler** thành `main.handler`.

#### 4. Cấu hình Amazon API Gateway

- Tạo một **HTTP API** trong API Gateway.
- Thêm Route với phương thức **ANY** và đường dẫn `/{proxy+}`.
- Kết nối (Integrate) Route này tới hàm Lambda vừa tạo.
- Khai báo **CORS** cho phép mọi Origin (`*`), Methods (`*`) và Headers (`*`).
- Lấy đường dẫn **Invoke URL** của API Gateway để cung cấp cho phía Frontend.
