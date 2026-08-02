---
title : "Environment Preparation"
date: 2026-07-25
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Necessary Tools and Services

Before starting the project deployment, we need to prepare the following environments and resources:

1. **AWS Account:**
   - An active AWS account (a new account is recommended to utilize the Free Tier).
   - Create an IAM User with administrative privileges (AdministratorAccess) or at least access to S3, Lambda, API Gateway, DynamoDB, CloudFront, Route 53, and ACM.

2. **Local Development Environment:**
   - **Visual Studio Code (VS Code):** Or any IDE that supports Python and Web development.
   - **Python 3.10+**: Installed and configured in environment variables (PATH) on your PC (Windows/Mac/Linux).
   - It is recommended to install the **AWS CLI** and configure `aws configure` with an Access Key/Secret Key to test local DynamoDB connections.

3. **Source Code:**
   - The project structure consists of two main folders: `backend` (containing FastAPI code) and `frontend` (containing HTML/JS/CSS code).

4. **Custom Domain (Optional but recommended):**
   - A short domain name (e.g., `domain.link`, `abc.to`) registered through Amazon Route 53 or a third-party provider (Namecheap, Hostinger) to act as the actual shortening domain.
