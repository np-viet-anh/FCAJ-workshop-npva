---
title : "Database & Backend"
date: 2026-07-25
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### 1. Initializing Amazon DynamoDB

DynamoDB is a NoSQL database service with automatic scaling capabilities.
- Access **Amazon DynamoDB** on the AWS Console, select **Create table**.
- **Table name**: `URLShortener`
- **Partition key**: `short_id` (String type).
- Keep the default settings and create the table.

#### 2. Developing Backend with FastAPI

- Install necessary Python libraries: `fastapi`, `uvicorn`, `boto3`, `mangum`, `pydantic`.
- The `Mangum` function acts as an adapter, converting API Gateway request formats to ASGI compatible with FastAPI.
- DynamoDB connection code (`database.py`):
```python
import boto3
dynamodb = boto3.resource('dynamodb', region_name='ap-southeast-2')
table = dynamodb.Table('URLShortener')
# put_item and get_item functions
```
- Logic endpoint (`main.py`): Contains `POST /api/shorten` API to create short links and `GET /{short_id}` API to redirect users to the original page.

#### 3. Deploying to AWS Lambda

- Package the source code along with dependencies into `function.zip`.
  *Note for Windows users: You need to use the parameter `--platform manylinux2014_x86_64` when running `pip install` to ensure compatibility with AWS Lambda's Linux environment.*
- Create a new Lambda function with **Python 3.10** Runtime.
- Grant DynamoDB access to Lambda (Add `AmazonDynamoDBFullAccess` policy to the Execution Role).
- Upload `function.zip` to Lambda. Configure **Handler** to `main.handler`.

#### 4. Configuring Amazon API Gateway

- Create an **HTTP API** in API Gateway.
- Add a Route with **ANY** method and path `/{proxy+}`.
- Integrate this Route with the newly created Lambda function.
- Declare **CORS** allowing all Origins (`*`), Methods (`*`), and Headers (`*`).
- Retrieve the **Invoke URL** of the API Gateway to provide to the Frontend.
