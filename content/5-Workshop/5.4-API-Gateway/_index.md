---
title: "API Gateway"
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

## Objectives

Publish Lambda via API Gateway (REST), create resources/methods, and test GET/POST using curl or Postman.

![image](/images/5-Workshop/Api_lambda.png)

## Steps

- Create REST API, resource `/hello`, enable CORS if needed.  
- Add GET/POST methods, map to Lambda (proxy integration).  
- Deploy stage `dev`, note the Invoke URL.  
- Test GET/POST, handle errors (400) when data is missing.  
- Optional: enable CORS or custom domain.
