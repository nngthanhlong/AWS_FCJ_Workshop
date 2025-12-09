---
title: "Lambda Basics"
weight: 3
chapter: false
pre : " <b> 5.3. </b> "
---

## Objectives

Create and test Lambda Hello World (Node.js/Python), pass input parameters, and fine-tune configuration (memory, timeout, logs).

![image](/images/5-Workshop/5.3-Lambda-basics/Lambda_hello_world.png)

## Key Steps

1) **Create a Node.js Function**  
   - Runtime: Node.js 18.x (example).  
![image](/images/5-Workshop/5.3-Lambda-basics/Lambda_nodejs_test.png)
   - Sample handler returns JSON `{ message: "hello" }`.  
![image](/images/5-Workshop/5.3-Lambda-basics/Lambda_nodejs_handler.png)
   - Test event with `name` parameter, log results in CloudWatch.
![image](/images/5-Workshop/5.3-Lambda-basics/Lambda_nodejs_cloudwatch.png)

2) **Create a Python Function**  
   - Runtime: Python 3.12 (example).
   - Handler reads `event["name"]` and returns customized response.
![image](/images/5-Workshop/5.3-Lambda-basics/Alice_test.png)

3) **Parameterization & Common Errors**  
   - Read `event` (query/body will be added by API Gateway in the next step).  
   - Catch missing key errors, return appropriate status codes.
![image](/images/5-Workshop/5.3-Lambda-basics/404_not_name.png)

4) **Light Optimization**  
   - Adjust `Memory` and `Timeout` to balance cost/performance.  
   - Set CloudWatch retention.
![image](/images/5-Workshop/5.3-Lambda-basics/cloudwatch_retention.png)
