---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Why I chose Amazon DynamoDB for my URL Shortener application?

When building a URL Shortener application, one of the most critical challenges is data retrieval speed: "How can the system immediately find the original link and redirect in less than 1 second when a user clicks on a short link?"

I tested with **Amazon DynamoDB** and was truly impressed for the following reasons:

🔹 **Perfect Key-Value architecture:** A URL Shortener essentially just maps a `short_id` to a `long_url`. DynamoDB is a NoSQL database built to handle such Key-Value queries extremely optimally.
🔹 **Single-digit millisecond latency:** Read/write speeds are consistently maintained at single-digit milliseconds at any scale.
🔹 **Serverless Database:** No installation, no database cluster maintenance (like RDS). Just create a table and use it, it scales automatically.

Configuring AWS Lambda to communicate with DynamoDB using `boto3` is also very straightforward. However, I learned that you must pay attention to configuring the IAM Role correctly (least privilege) so that Lambda only has permission to operate on that specific table.

If you were building a similar system, would you choose RDS, ElastiCache (Redis), or DynamoDB? Let's discuss! 🚀

---
**References:**
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
- [Boto3 DynamoDB Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html)
