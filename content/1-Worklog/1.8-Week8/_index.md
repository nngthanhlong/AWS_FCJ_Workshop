---
title: "Week 8 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Clearly understand the architecture and operating mechanism of Amazon S3 (Bucket – Object – Storage Class).
* Master important S3 features: Versioning, Encryption, Lifecycle, Replication.
* Practice data management on S3: upload, permission assignment, public/private, static website hosting.
* Apply best practices for security and cost optimization when working with S3.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | -------- | ------------ | --------------- | -------------- |
| 2 | - Learn overview of Amazon S3: <br>&emsp; + What is S3 <br>&emsp; + Bucket – Object architecture <br>&emsp; + Availability and storage models | 27/10/2025   | 27/10/2025 | https://000057.awsstudygroup.com/1-introduce/ |
| 3 | - Analyze S3 Bucket vs Object <br>&emsp; + URL structure <br>&emsp; + Prefix & virtual folder <br>&emsp; + Metadata, Key, ACL <br> - Classify Storage Classes | 28/10/2025   | 28/10/2025 | https://000057.awsstudygroup.com/1-introduce/ |
| 4 | - Research S3 security features: <br>&emsp; + Encryption (SSE-S3, SSE-KMS) <br>&emsp; + IAM Policy, Bucket Policy <br>&emsp; + Block Public Access <br> - Understand Versioning | 29/10/2025   | 29/10/2025 | https://000057.awsstudygroup.com/1-introduce/ |
| 5 | - Learn about Lifecycle Rules & Replication: <br>&emsp; + Change storage class <br>&emsp; + CRR & SRR <br>&emsp; + Delete Marker <br> - S3 Storage Lens & cost analysis | 30/10/2025   | 31/10/2025 | https://000057.awsstudygroup.com/1-introduce/ |
| 6 | **Hands-on Practice:** <br>&emsp; + Create bucket <br>&emsp; + Upload & manage objects <br>&emsp; + Enable/disable public access <br>&emsp; + Static website hosting <br>&emsp; + Configure versioning & lifecycle <br>&emsp; + Test object access | 31/10/2025   | 31/10/2025 | https://000057.awsstudygroup.com/1-introduce/ |

### Week 8 Achievements:

* Clearly understood Amazon S3 foundation, including:
  * Bucket–object architecture
  * Object metadata, prefix, virtual folder
  * URL structure to access objects

* Mastered S3 storage classes:
  * Standard
  * Standard-IA
  * Intelligent-Tiering
  * Glacier / Deep Archive

* Applied important features proficiently:
  * Versioning
  * Lifecycle Management
  * Replication (CRR, SRR)
  * Block Public Access
  * Encryption (SSE-S3, SSE-KMS)

* Complete hands-on practice on S3:
  * Create bucket
  * Upload & assign permissions to objects
  * Static website hosting
  * Configure versioning, lifecycle
  * Verify public/private object access via URL

* Mastered best practices:
  * Don't make buckets public
  * Use default encryption
  * Optimize costs with lifecycle & storage class
  * Organize data by prefix to increase performance
