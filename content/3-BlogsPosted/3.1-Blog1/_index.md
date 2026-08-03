---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Deploying FastAPI (Python) on AWS Lambda using the Mangum library

Serverless architecture is becoming a new standard in Backend application development due to its ability to optimize both costs and operational effort.

A popular technology stack includes the combination of **AWS Lambda**, **API Gateway**, and the **FastAPI (Python)** framework. However, for a traditional web framework like FastAPI to be compatible and run reliably on the AWS Lambda Serverless environment, the optimal solution is to use the **Mangum** library as an adapter.

**Advantages of this architecture:**
- **Zero-ops:** Completely eliminates the burden of operating system administration and server scaling. AWS Lambda automatically scales based on the actual traffic volume of the system.
- **Cost optimization:** For small to medium-scale applications or during the testing phase, operational costs are significantly minimized, largely covered by the AWS Free Tier. Costs are only incurred based on the execution time of the code in milliseconds.
- **Development efficiency:** Programming with FastAPI is straightforward and modern, supporting the automatic generation of API documentation according to the Swagger/OpenAPI standard.

The Serverless approach combining FastAPI and Mangum is strongly proving its effectiveness in building APIs on the AWS cloud.

---
**References:**
- [AWS Lambda](https://aws.amazon.com/lambda/)
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Mangum](https://mangum.io/)
