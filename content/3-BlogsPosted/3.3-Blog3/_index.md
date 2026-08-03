---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# High-performance and cost-optimized static Web hosting solution with Amazon S3 and CloudFront

For the Frontend component of modern static web applications, systems often utilize client-side compiled technologies like React, Vue, or simply HTML, Javascript, and CSS. Deploying these static files on a traditional EC2 server would fail to maximize performance and result in a waste of compute resources.

Therefore, the standard architecture typically applied on the AWS cloud is a combination of **Amazon S3** and **Amazon CloudFront**:

1. **Amazon S3 (Storage):** The S3 service provides the Static Website Hosting feature, serving as a secure and durable storage space for the entire compiled user interface source code of the application.
2. **Amazon CloudFront (Content Delivery Network - CDN):** CloudFront handles the distribution and caching of content at Edge Locations globally. This significantly reduces network latency, ensuring the website loads rapidly regardless of the user's geographical location.
3. **Security and Custom Domain:** CloudFront facilitates the establishment of encrypted HTTPS connections via a free SSL/TLS security certificate issued by AWS Certificate Manager (ACM), while easily integrating with Amazon Route 53 to route traffic to a custom domain.

**Result:** This solution provides a frontend platform capable of handling high concurrent traffic volumes with excellent performance, while monthly maintenance costs are optimized to the lowest possible level thanks to the pay-as-you-go pricing mechanism.

---
**References:**
- [Host a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
- [Amazon CloudFront](https://aws.amazon.com/cloudfront/)
- [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/)
