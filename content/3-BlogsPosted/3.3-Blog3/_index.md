---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Hosting a Static Website at near-zero cost with lightning speed using Amazon S3 and CloudFront!

After finishing the Backend, let's talk about the Frontend of the URL Shortener application. My UI is simply HTML, Javascript, and TailwindCSS. Running an EC2 server just to host these static files would be a waste of resources.

Therefore, the "standard" solution on AWS that I used is combining **Amazon S3** and **Amazon CloudFront**:

1️⃣ **Amazon S3 (Storage):** Enable Static Website Hosting on the S3 bucket. This acts as the hard drive containing my UI source code.
2️⃣ **Amazon CloudFront (CDN):** This is the "secret weapon". CloudFront distributes (caches) the content to Edge Locations worldwide. Whether a user accesses from the US or Vietnam, the web loads instantly.
3️⃣ **Security & Custom Domain:** CloudFront helps me easily force HTTPS connections using a free SSL/TLS certificate from AWS Certificate Manager (ACM) and map my custom domain using Route 53.

💡 **Result:** I have a frontend website capable of handling tens of thousands of concurrent requests without crashing, while the monthly cost is incredibly low.

What services on AWS do you usually use to host your static React/Vue/HTML projects? 👇

---
**References:**
- [Host a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
- [Amazon CloudFront](https://aws.amazon.com/cloudfront/)
- [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/)
