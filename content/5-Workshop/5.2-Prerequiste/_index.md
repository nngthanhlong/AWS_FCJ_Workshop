---
title: "Prerequisites"
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

## Account & Permissions

- AWS account with permissions to create Lambda, CloudWatch Logs, API Gateway (minimum IAM: `AWSLambdaBasicExecutionRole`).  
- No advanced EC2/VPC permissions needed for this workshop.

## Tools

- Browser for AWS Console operations.  
- curl/Invoke-RestMethod or Postman to call API Gateway.  
- Optional: local editor to write Node.js/Python code before pasting into console.

## Quick Setup

- Select a nearby region (e.g., us-east-1 or ap-southeast-1).  
- Create an IAM role for Lambda with trust policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["sts:AssumeRole"],
      "Principal": { "Service": ["lambda.amazonaws.com"] }
    }
  ]
}
```
- Attach the `AWSLambdaBasicExecutionRole` policy to the role.  
- Set CloudWatch Logs retention (e.g., 7–14 days) to control costs: CloudWatch → Log groups → `/aws/lambda/<function-name>` → Actions → Edit retention.

![image](/images/5-Workshop/5.2-Prerequisite/Iamrole_for_lambda.png)
