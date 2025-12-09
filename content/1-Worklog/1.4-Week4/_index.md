---
title: "Week 4 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Grant application permissions to access AWS services with IAM Role

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Overview of how to grant access permissions to applications on AWS <br> - Understand why you should not use access key/secret access key directly in applications                                   | 29/09/2025   | 29/09/2025      | https://000048.awsstudygroup.com/   |
| 3   | - Hands-on practice using access key and secret access key in applications <br> - Check ability to access AWS services (S3, EC2) from applications                                                   | 30/09/2025   | 30/09/2025      | https://000048.awsstudygroup.com/   |
| 4   | - Understand IAM Role on EC2 <br> - Create IAM Role with appropriate policy <br> - Attach IAM Role to EC2 instance <br> - Experiment accessing AWS services without needing direct access key                       | 01/10/2025   | 01/10/2025      | https://000048.awsstudygroup.com/   |
| 5   | - Configure application to use IAM Role <br> - Experiment accessing S3, DynamoDB or other services from application running on EC2 <br> - Observe logs and confirm access permissions                           | 02/10/2025   | 02/10/2025      | https://000048.awsstudygroup.com/   |
| 6   | - Clean up resources created this week: delete IAM Role, policies, test EC2 <br> - Document the entire permission granting process and lessons learned <br> - Prepare knowledge for next week | 03/10/2025   | 03/10/2025      | https://000048.awsstudygroup.com/   |

### Week 4 Achievements:

* Understood the mechanism of granting application access permissions on AWS:
  * IAM Role concept and role in security
  * Difference between using access key/secret access key and IAM Role
  * Recognize risks when using access key directly in applications

* Practiced using access key/secret access key:
  * Configure in application
  * Access AWS services like S3, EC2
  * Observe logs and debug when access permissions are insufficient

* Practiced IAM Role on EC2:
  * Create IAM Role with appropriate policy
  * Attach IAM Role to EC2 instance
  * Configure application to use IAM Role to access AWS services without access key
  * Verify successful access and document results

* Managed permissions and policies:
  * Understand how to create properly standards least-privilege policy
  * Practice assigning policy to IAM Role
  * Check access permissions for each service from the application

* Comprehensive skills:
  * Confident in deploying applications on EC2 with secure access permissions
  * Master best practices in managing AWS access permissions
  * Document and clean up resources: delete IAM Role, policies, test EC2

