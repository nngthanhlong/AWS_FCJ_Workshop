---
title: "Week 7 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Understand concepts and benefits of Amazon RDS compared to database on EC2.
* Deploy and manage DB instances with common engines (Aurora, MySQL, PostgreSQL, SQL Server, Oracle).
* Practice management features: Multi-AZ, Read Replicas, Snapshots, Backup & Restore.
* Manage security, data encryption, IAM Policy and VPC Subnet Group.
* Monitor, log and optimize DB performance.
* Clean up resources after hands-on practice.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                                                                       | Start Date | Completion Date | Reference Material                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Introduction to Amazon RDS and supported database management systems <br> - Understand benefits of RDS compared to DB on EC2 <br> - Initialize VPC and DB Subnet Group for DB instances                                                                                               | 20/10/2025   | 20/10/2025      | https://000005.awsstudygroup.com/   |
| 3   | - Create basic DB instance (MySQL or PostgreSQL) <br> - Deploy Multi-AZ deployment <br> - Test failover between AZs <br> - Set up automatic backup configuration and maintenance window                                                                                          | 21/10/2025   | 21/10/2025      | https://000005.awsstudygroup.com/   |
| 4   | - Create and manage Read Replicas <br> - Snapshot DB and restore from snapshot <br> - Expand storage and change instance type <br> - Check Multi-AZ and Read Replicas limitations                                                                                              | 22/10/2025   | 22/10/2025      | https://000005.awsstudygroup.com/   |
| 5   | - Set up DB security: IAM Role, KMS encryption, Security Group, Public/Private endpoints <br> - Practice data migration with AWS DMS & SCT                                                                                                                                | 23/10/2025   | 23/10/2025      | https://cloudjourney.awsstudygroup.com/   |
| 6   | - **Monitor and optimize RDS:** <br> &emsp; + CloudWatch Metrics & Alarms: monitor CPU, IOPS, Storage, DatabaseConnections <br> &emsp; + Enhanced Monitoring: detailed operating system monitoring <br> &emsp; + Performance Insights: analyze queries and optimize <br> &emsp; + Check logs, RDS Events & CloudTrail | 24/10/2025   | 24/10/2025      | https://000005.awsstudygroup.com/   |
| 6   | - **Clean up DB instances and resources:** <br> &emsp; + Delete DB instances, Multi-AZ, Read Replicas <br> &emsp; + Delete DB Snapshots (manual and automatic) <br> &emsp; + Delete DB Subnet Groups <br> &emsp; + Delete related Security Groups <br> &emsp; + Check on Console & CLI, document cleanup process | 24/10/2025   | 24/10/2025      | https://000005.awsstudygroup.com/   |

### Week 7 Achievements:

* Clearly understood Amazon RDS as a managed relational database service, different from DB on EC2.
* Proficiently deployed DB instances with common engines: MySQL, PostgreSQL, Aurora, SQL Server, Oracle.
* Used Multi-AZ to increase availability and successfully tested failover.
* Managed Read Replicas and Snapshots to expand read capability and data recovery.
* Practiced expanding storage and changing instance type without service interruption.
* Deployed DB security: IAM Role, KMS encryption, Security Group and managed Public/Private endpoints.
* Practiced data migration with AWS DMS & SCT.
* Monitored RDS performance and logs via CloudWatch, Performance Insights, Enhanced Monitoring and CloudTrail.
* Cleaned up resources and documented complete hands-on procedures.
