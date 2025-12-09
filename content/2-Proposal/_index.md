---
title: "Proposal"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# **Online Library - Serverless Content Platform For Small Groups**

## **1. Executive Summary**

The **Online Library** project aims to build a serverless, **low-cost** platform for storing and distributing content (PDF/ePub) to a small group of users (initially **~100 people**, a group comprising students/lab members who need to share moderated internal research documents). This solution prioritizes security, content approval workflow (Admin Approval), and **transparent, linear operational costs** as it scales. The architecture uses **completely AWS Serverless** (Amplify, Cognito, API Gateway, Lambda, S3, CloudFront, DynamoDB). Estimated MVP cost (not counting Free Tier) **≈ $9.80/month**, ensuring scalability to 5,000 to 50,000 users with predictable costs.

## **2. Problem**

### **What's the Problem?**

Documents and books are scattered; lack of a **secure content delivery system** with **access control**; adding or **content approval processes** are time-consuming and involve various legal issues.

### **Solution**

Build a serverless pipeline on AWS: Users upload via **Presigned PUT URL** (to temporary S3); Admin approves → Lambda moves file to public folder (but protected); Readers access via **Signed GET URL** (from CloudFront/CDN) to ensure speed and access control.

### **Benefits and Return on Investment**

- **Business Value:** Centralize content; quality control through approval workflow; rapid deployment with CI/CD.
- **Technical Benefits:** Low operational cost (**≈ $9.80/month** at MVP, not counting Free Tier); Serverless architecture can **easily scale large** ; secure content access.

---

## **3. Solution Architecture**

### **A. High-level**

![A) High level](/images/2-Proposal/Architect.jpeg)

### **B. Request Processing Flow**
![B) Request flow](/images/2-Proposal/Request_flow.jpeg)

### **AWS Services Used**

| Service | Primary Role | Specific Operations |
| --- | --- | --- |
| **Amplify Hosting** | CI/CD + FE Hosting | Build & Deploy Next.js, manage domain |
| **Cognito** | Authentication | Sign up/Login, issue JWT, refresh token |
| **API Gateway** | API Entry Point | Receive request, authenticate JWT, route to Lambda |
| **Lambda** | Business Logic | Handle upload, approval, create signed URL, write metadata |
| **S3** | Object Storage | Store original file, approved file, downloaded via Cloudfront Signed URL |
| **CloudFront** | CDN | Fast content distribution, block direct access via OAC |
| **DynamoDB** | Database | Store metadata (book name, uploader, approval status) |
| **Route 53** | DNS | Point domain to Amplify Hosting, API Gateway, CloudFront |
| **CloudWatch** | Monitoring | Store Lambda logs, alert on errors or unusual costs |

> **Search:**
> 
- Simple search by field (ex: book name, author), use **DynamoDB GSIs** for these attributes and query by GSI.

### **Request Processing Flow**

- **User Upload:** Presigned PUT to S3 `uploads/` folder.
- **Admin Approval:** Lambda copies file from `uploads/` to `public/books/` when approved.
- **Reader Security:** CloudFront uses **Origin Access Control (OAC)** to block direct S3 access and only allow reading via **Signed URL** (short-lived) created by Lambda.

### **Search Architecture**

- **Simple Search:**
    - Design **GSI** for `title` and `author` (example: `GSI1: PK=TITLE#{normalizedTitle}, SK=BOOK#{bookId}`; `GSI2: PK=AUTHOR#{normalizedAuthor}, SK=BOOK#{bookId}`).
    - Add `GET /search?title=...&author=...` endpoint to query by GSI instead of `Scan`.

![Search Architecture](/images/2-Proposal/SearchArchitecture.jpeg)

### **Admin Permissions**

- Use **Cognito User Groups** with an `Admins` group in User Pool.
- When Admin logs in, JWT contains `cognito:groups: ["Admins"]`.
- Admin business Lambda functions (e.g., `approveBook`, `takedownBook`) must check this claim; if missing group, return `403 Forbidden`.
- Can use **JWT Authorizer (API Gateway HTTP API)** for authentication, with detailed authorization handled in Lambda based on claims.

---

## **4. Technical Implementation**

### **Deployment**

1. **Design & IaC (Infrastructure-as-Code):** Build CDK stacks (Cognito, DDB, S3, Amplify, Lambda, API).
2. **Upload & Approval Flow:** Implement Presigned PUT, save metadata (status: `pending`), and Admin approval logic (copy file).
3. **Book Reading Flow:** Implement Signed GET endpoint, and reading interface (FE stream via CloudFront).
4. **Operations:** Setup CloudWatch logs (short retention), Budget Alerts, IAM hardening.
5. **Search:**
    - MVP: add GSI for `title`, `author` and `GET /search` endpoint query by GSI.

### **Technical Requirements**

- Use **CDK** to define entire infrastructure.
- API Gateway must be **HTTP API** for cost optimization.
- Lambda (Python) handles business logic and DynamoDB/S3 interactions.
- S3 Bucket Policy must **block public access** and only allow CloudFront OAC.

---

## **5. Timeline and Milestones**

---

### **Project Timeline**

### **Foundation & Authentication (Weeks 1-2)**

Goal: set up infrastructure and enable user login.

- **Backend Tasks (CDK/DevOps):**
    - Write CDK stack for **Cognito** (User Pool, App Client).
    - Write CDK stack for **DynamoDB** (main table, no GSI yet).
    - Write CDK stack for **S3** (Buckets `uploads`, `public`, `logs`) and configure **OAC** (Origin Access Control).
    - Deploy **API Gateway** (HTTP API) and a "hello world" Lambda to test.
- **Frontend Tasks (Amplify):**
    - Configure **Amplify Hosting** and connect to GitHub repo (CI/CD).
    - Integrate Amplify UI / Cognito SDK for pages: Sign Up, Email Verification, Login, Forgot Password.
- **Milestone:**
    - Developer can `git push` and FE auto-deploys.
    - Users can sign up/login and receive JWT token.

### **Upload & Approval Flow (Weeks 2-3)**

Goal: enable signed-in users to upload files and Admin to approve them.

- **Backend Tasks (CDK/Lambda):**
    - Write Lambda `createUploadUrl`:
        - Authenticate JWT (must be logged in).
        - Create **Presigned PUT URL** pointing to S3 `uploads/` folder.
        - Write metadata to DynamoDB (status: `PENDING`).
    - Write Lambda `approveBook`:
        - Authenticate JWT (must be Admin).
        - Copy file from `uploads/` to `public/books/`.
        - Update status in DynamoDB (status: `APPROVED`).
- **Frontend Tasks:**
    - Build Upload Form (drag-drop, file selection).
    - Call API `createUploadUrl` to get URL.
    - Perform file upload (HTTP PUT) directly to S3 Presigned URL.
    - Build Admin Interface:
        - Get list of books with status `PENDING`.
        - Have "Approve" button (calls API `approveBook`).

### **Reading & Search Flow (Weeks 3-4)**

Goal: enable users to read and search approved books.

- **Backend Tasks (CDK/Lambda):**
    - Write Lambda `getReadUrl`:
        - Authenticate JWT (must be logged in).
        - Check book has status `APPROVED`.
        - Create **Signed GET URL** (short-lived) via CloudFront pointing to file in `public/books/`.
    - Update CDK: Add **GSI (Global Secondary Index)** for `title` and `author` to DynamoDB table.
    - Write Lambda `searchBooks`: Query DynamoDB by GSI (no `Scan`).
- **Frontend Tasks:**
    - Build Home Page: Display book list (from API, no URLs).
    - Build Search Bar (call API `searchBooks`).
    - Build Reading Interface (Reader):
        - When clicking "Read", call API `getReadUrl`.
        - Use received URL to render file (e.g., use `react-pdf`).

### **Operations & Security (Weeks 5-6)**

Goal: harden the system, make it safe and easy to monitor.

- **Backend Tasks (CDK/Lambda):**
    - Setup **S3 Event Notification** (for `uploads/`).
    - Write Lambda `validateMimeType`: Trigger on new file, read "magic bytes" to validate PDF/ePub. If wrong, update status: `REJECTED_INVALID_TYPE`.
    - Write Lambda `takedownBook` (API for Admin) and `deleteUpload` (delete `PENDING` files after 72h).
- **DevOps Tasks (AWS Console/CDK):**
    - Setup **AWS Budget Alerts** (alert when cost exceeds $X).
    - Setup **CloudWatch Alarms** (e.g.: Lambda error rate > 5%).
    - Review **IAM** (ensure "least-privilege"), **CORS** (only allow Amplify domain).

## **6. Budget Estimation**

You can find the budget estimation on the: [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=45ebafb3c3a0ff07b7c21970b2287f1a06f2a460)

Below is a strict monthly cost estimate (assuming no AWS Free Tier applied) at MVP scale (100 users).

| # | AWS Service | Region | Monthly (USD) | Notes |
| --- | --- | --- | --- | --- |
| 0 | **Amazon CloudFront** | Asia Pacific (Singapore) | **0.86** | 10 GB data egress + 10,000 HTTPS requests |
| 1 | **AWS Amplify** | Asia Pacific (Singapore) | **1.31** | 100 build min + 0.5 GB storage + 2 GB served |
| 2 | **Amazon API Gateway** | Asia Pacific (Singapore) | **0.01** | ~10,000 HTTP API calls/month |
| 3 | **AWS Lambda** | Asia Pacific (Singapore) | **0.00** | 128 MB RAM × 100 ms × 10,000 invokes |
| 4 | **Amazon S3 (Standard)** | Asia Pacific (Singapore) | **0.05** | 2 GB object storage for books/images |
| 5 | **Data Transfer** | Asia Pacific (Singapore) | **0.00** | Included in CloudFront cost |
| 6 | **DynamoDB (On-Demand)** | Asia Pacific (Singapore) | **0.03** | Light metadata table (0.1 GB, few reads/writes) |
| 7 | **Amazon Cognito** | Asia Pacific (Singapore) | **5.00** | 100 MAU, Advanced Security enabled |
| 8 | **Amazon CloudWatch** | Asia Pacific (Singapore) | **1.64** | 5 metrics + 0.1 GB logs/month |
| 9 | **Amazon Route 53** | Asia Pacific (Singapore) | **0.90** | 1 Hosted Zone + DNS queries |
|  |  |  | **≈ 9.80 USD / month** | **No Free Tier applied** |

### **Infrastructure Cost**

This cost model demonstrates serverless architecture efficiency: costs focus mainly on **value delivered to users** (Cognito MAU) rather than paying for "idle servers".

---

## **7. Risk Assessment**

### **Risk Matrix**

| Risk | Impact | Mitigation Strategy |
| --- | --- | --- |
| Cost increases with user surge | High | Limit MAU, cache metadata via CloudFront |
| Upload abuse | Medium | Limit ≤ 50MB/file, auto-delete after 72h |
| Fake/malicious files | Medium | S3 Event → Lambda validate MIME (magic bytes) |
| Monitoring overload | Low | CloudWatch alert, 14-day log retention |

### **Mitigation Strategies**

- **Costs:**
    - Set **AWS Budget Alerts** for CloudFront and Cognito.
    - Understand **Signed URL** has short TTL so no long-term public cache; instead, **cache metadata/API response** (book list, details) on CloudFront 3–5 min to reduce API load.
    - Only create Signed URL when user actually clicks read (on‑demand), not pre-create for entire list.
- **Uploads:**
    - Limit file size **≤ 50MB** for MVP. (Can increase to 200MB later, use multipart upload in FE to avoid timeout.)
    - Apply **Rate Limit/Throttling** on API Gateway for Presigned URL creation endpoints.
    - Set **S3 Lifecycle Policy** to auto-delete unapproved files in `uploads/` after 72h.
    - Add **Server‑side Validation**: S3 Event Notifications → Lambda read **magic bytes** (e.g., `file-type` library) to validate PDF/ePub; if invalid, auto-delete and set status `REJECTED_INVALID_TYPE` in DynamoDB.
- **Copyright (DMCA):**
    - Store **Audit Log** in DynamoDB: `uploaderID`, `uploadTimestamp`, `adminApproverID`, `approvalTimestamp` for traceability.
    - Build **Takedown API** (Admin only): update status `TAKEDOWN`; optionally move object from `public/books/` to `quarantine/books/` (don't delete) to keep records.

### **Contingency Plan**

If costs exceed budget, can temporarily limit new users via invite system to control Cognito MAU and optimize file size.

---

## **8. Expected Results**

### **Technical Improvements:**

- Ensure **fast content delivery speed** and **security** (CDN + Signed URL).
- Create a **standard Serverless architecture** on AWS, easily scalable to 50,000 users without core architecture changes.
- **Fully automated CI/CD** for both Frontend and Backend (CDK/Amplify).

### **Long-term Value**

- Establish a **centralized, structured data platform** for book content.
- Provide a **living reference documentation** for E2E Serverless implementation.
- Potential to integrate analytics services (like Amazon QuickSight) or AI/ML in the future.

This system demonstrates the ability to build secure, cost-efficient, and easily scalable content platforms using AWS Serverless — suitable for real-world deployment in small groups.

### **9. Attached Documents**
- [Online Library](https://docs.google.com/document/d/1Wf70Iif5duHvM_0IDd3TpI8vLsMkgIZZ8XsJ02B6BKI/edit?tab=t.0)
