---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Reasons for choosing Amazon DynamoDB for a URL Shortener application

When designing a URL Shortener system, one of the most rigorous technical requirements is data retrieval speed. The system must ensure the rapid lookup of the original link from the shortened code and execute the redirection in minimal time.

The project selected **Amazon DynamoDB** as the primary database based on the following technical factors:

- **Suitable Key-Value architecture:** A URL Shortener application fundamentally performs a mapping operation from a `short_id` to a `long_url`. DynamoDB is a NoSQL database specifically optimized for such Key-Value queries.
- **Single-digit millisecond latency:** Read and write speeds are consistently maintained at under 10 milliseconds, regardless of how much the system scales.
- **Serverless Database:** Completely minimizes the effort of installing and maintaining database cluster configurations (compared to solutions like Amazon RDS). Resource scaling is performed entirely automatically.

The integration between AWS Lambda and DynamoDB using the `boto3` library was straightforward. However, an important consideration during deployment is strictly adhering to the principle of least privilege when configuring the IAM Role, ensuring AWS Lambda only has permission to operate on the designated data table.

---
**References:**
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
- [Boto3 DynamoDB Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html)
