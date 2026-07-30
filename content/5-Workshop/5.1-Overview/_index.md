---
title : "System Overview"
date : 2026-08-30 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Serverless URL Shortener Architecture

The system is designed with a modern Serverless architecture, utilizing fully managed AWS services:

1. **End Users:** Access the web interface through a short domain (Custom Domain).
2. **Amazon Route 53:** The DNS system points the custom domain to Amazon CloudFront (for Frontend) and API Gateway (for Backend).
3. **Amazon CloudFront:** A global CDN caching the frontend, enabling ultra-fast loading and providing HTTPS certificates (via AWS Certificate Manager).
4. **Amazon S3:** Securely hosts the static frontend files (HTML, CSS, JS).
5. **Amazon API Gateway:** Acts as the HTTP API, receiving link creation or redirect requests and forwarding them to AWS Lambda.
6. **AWS Lambda:** The serverless compute service, running Python (FastAPI) code to handle shortening logic and generate unique hash codes.
7. **Amazon DynamoDB:** A NoSQL database with millisecond latency, storing the `{short_id: long_url}` key-value pairs.

---

This combination allows the application to handle thousands of concurrent requests without operational intervention (zero ops), while maximizing cost savings.
