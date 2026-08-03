---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Easily deploy FastAPI (Python) to AWS Lambda with Mangum!

[EXPERIENCE SHARING] Building a fully Serverless Backend, fast and cost-effective! ☁️

While working on my URL Shortener project, I decided to use a fully Serverless architecture for the Backend instead of provisioning an EC2 instance.

The stack I chose is **AWS Lambda** + **API Gateway** combined with **FastAPI (Python)**. But how can a web framework like FastAPI run smoothly on Lambda? The answer is using the **Mangum** library.

✨ **Benefits of this stack:**
- **Zero-ops:** No OS management, no worrying about scaling servers. Lambda scales automatically based on traffic.
- **Cost-effective:** During development and for small applications, the running cost is close to $0 thanks to the AWS Free Tier. You only pay for the compute time you consume.
- **Development speed:** Coding with FastAPI is fast, modern, and it automatically generates Swagger/OpenAPI documentation.

Are there any other developers in the group who love the AWS Serverless ecosystem as much as I do? Do you usually use API Gateway or ALB to trigger Lambda? Let's share your thoughts below! 👇

---
**References:**
- [AWS Lambda](https://aws.amazon.com/lambda/)
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Mangum](https://mangum.io/)
