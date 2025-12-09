---
title : "Overview"

weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

## Objectives

Introduce the serverless workshop: creating Lambda functions (Node.js/Python), receiving input parameters, integrating API Gateway, and deploying an in-app purchase recommendation API. Emphasize how to reduce deployment time using Lambda without requiring server management.

## General Architecture

- Lambda receives events, processes logic, returns JSON.  
- API Gateway acts as the REST front door, maps methods → Lambda.  
- Optional: custom domain/stage for multiple environments.

## Expected Results

- 2 Hello World functions (Node.js/Python) with parameters.  
- 1 REST endpoint (GET/POST) via API Gateway.  
- 1 business logic function (purchase recommendation) returning JSON.

## Duration and Structure

- Part 1: Lambda basics, test in console.  
- Part 2: API Gateway, mapping input, testing.  
- Part 3: In-app purchase exercise, cleanup resources.

![image](/images/5-Workshop/Api_lambda.png)
