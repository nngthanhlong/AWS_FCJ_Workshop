---
title: "Week 11 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Understand and practice hosting static web content on S3, accelerate with CloudFront.
* Configure access permissions and optimize cache for CloudFront distribution.
* Familiarize with Amazon ElastiCache for Redis: create cluster, manage nodes and shards.
* Practice scaling cluster, manage parameter groups and run within VPC.
* Understand steps to clean up resources to avoid cost incurrence.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --------- | ------------ | --------------- | -------------- |
| 2   | - **CloudFront with S3 – Introduction & Requirements** <br>&emsp; + AWS account <br>&emsp; + IAM permission with S3 and CloudFront <br>&emsp; + Expected cost < $1/month <br> - **Hands-on** <br>&emsp; + Create S3 bucket <br>&emsp; + Upload `index.html` file | 17/11/2025 | 17/11/2025 | https://000094.awsstudygroup.com/ |
| 3   | - **Configure Amazon CloudFront** <br>&emsp; + Create distribution <br>&emsp; + Link with S3 bucket <br>&emsp; + Check access to static web content <br> - **Clean up resources** <br>&emsp; + Delete CloudFront distribution and S3 bucket when not needed | 18/11/2025 | 18/11/2025 | https://000094.awsstudygroup.com/ |
| 4   | - **Check, optimize & reference** <br>&emsp; + Check content load speed <br>&emsp; + Optimize cache and access permissions <br>&emsp; + Reference material: Amazon S3 & CloudFront | 19/11/2025 | 19/11/2025 | https://000094.awsstudygroup.com/ |
| 5   | - **Amazon ElastiCache for Redis – Introduction & Overview** <br>&emsp; + Set up and manage Redis cluster <br>&emsp; + Integrate with EC2, CloudWatch, CloudTrail, SNS <br>&emsp; + Automatic error detection and recovery <br> - **Clusters & Nodes** <br>&emsp; + Create cluster, choose instance, node type <br>&emsp; + Data stratification, Standard/Memory-optimized storage type | 20/11/2025 | 20/11/2025 | https://000061.awsstudygroup.com/ |
| 6   | - **ElastiCache for Redis – Advanced Practice** <br>&emsp; + Create and manage shards <br>&emsp; + Scale node and cluster <br>&emsp; + Manage parameter group <br>&emsp; + Run cluster within VPC, subnet, security group <br>&emsp; + Check number of nodes, shards and available IP addresses | 21/11/2025 | 21/11/2025 | https://000061.awsstudygroup.com/ |

### Week 11 Achievements:

**CloudFront with S3**
  * Understood how S3 and CloudFront work.
  * Created S3 bucket and uploaded `index.html` file.
  * Configured access permissions for bucket.
  * Created CloudFront distribution and linked S3.
  * Verified access to static web content via CloudFront.
  * Optimized cache and load speed.
  * Cleaned up S3 and CloudFront to avoid costs.
  * Used IAM to assign access permissions.

**Amazon ElastiCache for Redis**
  * Understood cluster, node and shard concepts.
  * Created Redis cluster and chose appropriate node type.
  * Practiced scaling cluster and shards.
  * Managed basic parameter groups.
  * Deployed cluster within VPC and configured security groups.
  * Verified automatic error recovery capability.
  * Cleaned up cluster after hands-on practice.
