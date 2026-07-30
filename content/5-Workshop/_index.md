---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Building a Serverless URL Shortener on AWS

#### Overview

In this workshop, we will build a complete URL shortener application, similar to bit.ly or tinyurl.
The project is 100% deployed on AWS **Serverless** architecture, optimizing costs (nearly $0 with Free Tier), automatically scaling smoothly without having to manage any virtual servers (EC2).

The application is divided into two separate parts:
+ **Frontend:** Built with HTML, Javascript, and Tailwind CSS, hosted as a static website on **Amazon S3** and globally distributed via **Amazon CloudFront** CDN.
+ **Backend:** Written in Python (FastAPI), packaged via the Mangum library to run on **AWS Lambda**, using **Amazon API Gateway** as the HTTP API entry point, and storing data in **Amazon DynamoDB**.

#### Contents

1. [System Overview](5.1-Overview/)
2. [Environment Preparation](5.2-Preparation/)
3. [Database & Backend Deployment](5.3-Database-and-Backend/)
4. [Frontend Deployment](5.4-Frontend-Deployment/)
5. [Custom Domain Configuration](5.5-Custom-Domain/)
6. [Resource Cleanup](5.6-Cleanup/)
