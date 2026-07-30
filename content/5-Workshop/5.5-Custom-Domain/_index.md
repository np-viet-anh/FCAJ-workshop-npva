---
title : "Custom Domain Configuration"
date : 2026-08-30 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### 1. Significance of Custom Domain

By default, AWS API Gateway issues a rather long path such as `https://d-xxxx.execute-api.ap-southeast-2.amazonaws.com`. For a link shortening system to truly be "short", we need to map a really short domain (e.g., `nuguseyo.com`) directly to API Gateway. Then, generated links will have a professional format: `https://nuguseyo.com/10Ugru`.

#### 2. Acquiring a Domain via Amazon Route 53

- Access the **Route 53** -> **Registered domains** service to purchase and register the desired domain.
- After payment, you must verify your Email address with ICANN (via the link sent to your registered email) to ensure the domain is not locked (ClientHold).

#### 3. Requesting SSL/TLS Certificate (AWS Certificate Manager - ACM)

- Switch to the **AWS Certificate Manager (ACM)** service, select **Request a public certificate**.
- Enter the domain name (e.g., `nuguseyo.com` and `*.nuguseyo.com`).
- Choose the DNS validation method. AWS will automatically generate CNAME records, you just need to click **Create records in Route 53** to automatically add them to DNS. Wait for the status to change to **Issued**.

#### 4. Configuring Custom Domain in API Gateway

- In the API Gateway console, select **Custom domain names** -> **Create**.
- Declare the domain name, choose Endpoint Type as `Regional`, attach the requested ACM certificate, and select TLS 1.2 security policy.
- Switch to the **API mappings** tab, configure the mapping of this Domain to the HTTP API created at the `$default` Stage.

#### 5. DNS Routing at Route 53

- In the Hosted zone of Route 53, create an **A (Alias)** record.
- Turn on the Alias switch, point to **API Gateway API**, and select the correct region as well as the provided Custom Domain Name ID.
- *Note:* Disable the **Evaluate target health** option to prevent Route 53 from refusing to return an IP address when the system does not support traditional Health check mechanisms.
- Wait a few minutes for the DNS to update, and the ultra-short shortening system is 100% complete!
