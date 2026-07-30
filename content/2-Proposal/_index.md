---
title: "Proposal"
date: 2026-08-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Serverless URL Shortener
## A cost-effective, auto-scaling URL shortening solution on AWS

### 1. Executive Summary
The **Serverless URL Shortener** project is designed to provide a link shortening service (similar to bit.ly) for internal or community use with extremely low operational costs. By fully embracing the AWS Serverless architecture, the system automatically scales to handle large traffic volumes without the need to maintain virtual servers (Zero-Ops).

### 2. Problem Statement
*Current Problem*
Businesses or individuals often rely on third-party URL shortening services, which come with limitations on link counts, high maintenance fees for custom domains, and risks of account suspensions or leaked marketing campaign data.

*Solution*
Build an in-house URL Shortener system utilizing **AWS Lambda** (logic processing), **Amazon API Gateway** (HTTP routing), **Amazon DynamoDB** (link storage), and **Amazon S3 + CloudFront** (web interface hosting and distribution). The entire system runs on a pay-as-you-go model.

*ROI & Benefits*
Monthly operational costs are near $0 due to AWS Free Tier (costing only about $10-$15/year for domain renewal). The system offers full data control and can be easily extended to integrate Analytics features later.

### 3. Solution Architecture
The platform adopts an AWS Serverless architecture to serve both Frontend (static UI) and Backend (dynamic APIs).

*AWS Services Used*
- *Amazon S3*: Hosts static source code (HTML, CSS, JS).
- *Amazon CloudFront*: Global CDN, reduces latency and provides SSL/TLS.
- *Amazon API Gateway*: The entry point (HTTP API) for backend communication and custom domains.
- *AWS Lambda*: Runs Python (FastAPI) code for shortening logic and URL redirection.
- *Amazon DynamoDB*: NoSQL database storing mappings between short IDs and original URLs.
- *Amazon Route 53 & ACM*: Manages DNS resolution and HTTPS certificates.

### 4. Technical Implementation
*Implementation Phases*
The project is divided into 4 main phases over an 8-week internship:
1. *Architecture Research*: Learn Serverless models and select appropriate services.
2. *Backend Development*: Write Python FastAPI code, package with Mangum, create DynamoDB tables, and deploy to Lambda.
3. *Frontend Development*: Build a user-friendly web interface with TailwindCSS and Fetch API.
4. *Deployment & Custom Domain*: Host Frontend on S3 & CloudFront. Configure Custom Domain for API Gateway via Route 53.

### 5. Roadmap & Milestones
- *Week 1-4*: Learn core AWS foundations (IAM, EC2, S3, Networking, Serverless).
- *Week 5-6*: Program and test the Backend (Lambda + DynamoDB).
- *Week 7-8*: Integrate Frontend, configure Custom Domain, and write the final report.

### 6. Budget Estimation
*Monthly Infrastructure Cost (Estimated at 100,000 visits/month)*
- AWS Lambda: $0.00 (Within 1 million free requests).
- Amazon DynamoDB: $0.00 (Within 25GB free tier).
- API Gateway: $0.10 (Very small fee for HTTP API).
- CloudFront & S3: ~$0.50 (Low bandwidth traffic).
- Route 53 (Domain): ~$10 - $15 / year (ICANN fixed fee).
*Total Maintenance*: ~ $1/month (excluding annual domain fee).

### 7. Risk Assessment
*Risk Matrix*
- Backend Code Bugs: Medium impact, low probability (Tested locally).
- Exceeding Free Tier: Low impact, very low probability.
- DNS Configuration Errors: High impact, medium probability.

*Mitigation Strategies*
- Use API Gateway Throttling to prevent DDoS.
- Set AWS Budgets to receive email alerts.
- Disable "Evaluate target health" in Route 53 to avoid mapping errors.

### 8. Expected Outcomes
A URL shortening system running smoothly 24/7 under a custom domain. This project not only proves the practical application of Serverless architecture but also serves as a solid foundation for developing a commercial SaaS in the future.