---
title : "Frontend Deployment"
date : 2026-08-30 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### 1. Completing Frontend Source Code

- The user interface is simply and modernly designed using **Tailwind CSS**.
- In the `script.js` file, you need to update the `API_BASE_URL` variable to point to the **API Gateway** Invoke URL initialized in the previous step.
```javascript
const API_BASE_URL = 'https://<api-id>.execute-api.<region>.amazonaws.com';
```

#### 2. Hosting Static Web on Amazon S3

- Create a new **S3 Bucket**. Uncheck "Block all public access" to allow internet access to the data.
- Open the **Properties** tab, scroll down to the **Static website hosting** section, select **Enable**, and enter `index.html` in the Index document box.
- Configure **Bucket Policy** granting `s3:GetObject` permission to allow anyone to view web content.
- Upload the entire Frontend source code (`index.html`, `script.js`, `style.css`) to the root directory of the Bucket. The web is now accessible via the S3 Website Endpoint.

#### 3. Accelerating Distribution with Amazon CloudFront

- Access **Amazon CloudFront** and create a new Distribution.
- In the **Origin domain** section, select the newly created S3 bucket.
- Keep default settings (the included default basic WAF configuration will automatically protect the web from common attacks).
- Set the **Default root object** to `index.html`.
- Wait for CloudFront to finish Deploying, after which you will receive a URL ending in `.cloudfront.net`. This is the global web path with secured HTTPS protocol, providing optimal page load speeds for users worldwide.
