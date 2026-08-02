---
title : "Resource Cleanup"
date: 2026-07-25
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Cleanup Process

After completing the lab and report, if you do not intend to continue using the application in practice, please clean up the created resources to avoid incurring any unexpected charges on your AWS account.

> [!WARNING]
> Keeping the Domain Name on Route 53 will incur an annual maintenance fee (around $10 - $16/year). Other Serverless services (S3, Lambda, API Gateway, DynamoDB) only charge based on usage traffic; if there is no access, it will be nearly 0, but they should still be cleaned up to keep the account tidy.

1. **Amazon CloudFront:**
   - Select the Distribution, click **Disable**.
   - Wait until the status fully changes to Disabled, then click **Delete**.

2. **Amazon S3:**
   - Go to the S3 Bucket containing the static source code.
   - Select **Empty** (Empty all files) and type `permanently delete` to confirm.
   - Select **Delete bucket** to completely delete the Bucket.

3. **Amazon API Gateway:**
   - In the API Gateway interface, go to Custom domain names and **Delete** the mapped domain.
   - Return to the APIs list, select the created HTTP API, click the **Delete** button.

4. **AWS Lambda:**
   - Navigate to the `URLShortener` Function, under the Actions menu, select **Delete**.

5. **Amazon DynamoDB:**
   - Go to the Tables section, select the `URLShortener` table, and proceed to delete the table (**Delete table**).

6. **AWS Certificate Manager (ACM):**
   - Select the created certificates and perform the **Delete** action.

7. **Amazon Route 53 (Optional):**
   - Go to Hosted zones, manually delete records (except NS and SOA), then delete the Hosted zone.
   - *Note:* Deleting international domain registrations (delete registration) is not supported for refunds after purchase. You can disable auto-renew in the Registered domains section.
