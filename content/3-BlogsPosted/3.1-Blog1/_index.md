---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Deploying FastAPI (Python) on AWS Lambda using the Mangum library

During the development of the URL Shortener project, the team decided to adopt a Serverless architecture for the Backend component instead of deploying on traditional EC2 virtual servers.

The selected technology stack includes **AWS Lambda**, **API Gateway** combined with the **FastAPI (Python)** framework. To ensure the FastAPI application is compatible and runs reliably on the AWS Lambda environment, the project utilizes the **Mangum** library as an adapter.

**Advantages of this solution:**
- **Zero-ops:** Completely eliminates the burden of operating system administration and server scaling. AWS Lambda automatically scales based on actual traffic volume.
- **Cost optimization:** During the development phase and for small to medium-scale applications, operational costs are significantly minimized, often covered by the AWS Free Tier. Costs are only incurred based on the actual code execution time.
- **Development efficiency:** Programming with FastAPI is straightforward and modern, automatically generating API documentation according to the Swagger/OpenAPI standard.

The Serverless approach is increasingly proving its effectiveness in building applications on the AWS cloud.

---
**References:**
- [AWS Lambda](https://aws.amazon.com/lambda/)
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Mangum](https://mangum.io/)
