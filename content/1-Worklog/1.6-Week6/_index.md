---
title: "Week 6 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Understand and proficiently use **AWS CLI** to manage AWS resources.
* Master the mechanism of profile, region configuration, output format.
* Practice interaction with:
  * S3
  * SNS
  * IAM
  * VPC
  * EC2
* Understand basics of **Amazon DynamoDB**, NoSQL model, table, partition key, sort key.
* Practice complete CRUD and GSI on DynamoDB using Console & CloudShell.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --------- | ------------ | --------------- | -------------- |
| 2   | - **Install AWS CLI** <br>&emsp; + Download AWS CLI from AWS homepage <br>&emsp; + Install on Windows/macOS/Linux <br> - **Configure AWS CLI basic** <br>&emsp; + Run `aws configure` command <br>&emsp; + Enter Access key ID, Secret access key, Region, Output format <br>&emsp; + Verify connection with `aws s3 ls` | 13/11/2025 | 13/11/2025 | https://000011.awsstudygroup.com/ |
| 3   | - **Create and use profiles** <br>&emsp; + Create additional profile besides default using `--profile` <br>&emsp; + Specify profile via `AWS_PROFILE` environment variable <br>&emsp; + Check profile with `aws s3 ls --profile <profile_name>` <br> - **Test AWS CLI with S3** <br>&emsp; + List buckets: `aws s3 ls` <br>&emsp; + Upload file: `aws s3 cp file.txt s3://bucket-name/` <br>&emsp; + Download file: `aws s3 cp s3://bucket-name/file.txt ./` | 14/11/2025 | 14/11/2025 | https://000011.awsstudygroup.com/ |
| 4   | - **Practice AWS CLI with SNS** <br>&emsp; + Create SNS topic: `aws sns create-topic --name MyTopic` <br>&emsp; + Subscribe subscriber: `aws sns subscribe --topic-arn <ARN> --protocol email --notification-endpoint example@gmail.com` <br>&emsp; + Send notification: `aws sns publish --topic-arn <ARN> --message "Hello SNS"` <br> - **AWS CLI with IAM** <br>&emsp; + Create IAM user and group <br>&emsp; + Assign policy and access permissions <br>&emsp; + Check permissions with AWS CLI command | 15/11/2025 | 15/11/2025 | https://000011.awsstudygroup.com/ |
| 5   | - **Amazon DynamoDB – Introduction** <br>&emsp; + Create DynamoDB table <br>&emsp; + Add, edit, delete item <br>&emsp; + Enable automatic item deletion after expiration <br> - **DynamoDB – Backup & Restore** <br>&emsp; + Create table backup <br>&emsp; + Restore table at specific point in time <br>&emsp; + Verify successful data restoration | 16/11/2025 | 16/11/2025 | https://000060.awsstudygroup.com/ |
| 6   | - **Amazon DynamoDB – Advanced / Practice** <br>&emsp; + Add secondary indexes (Global/Local Secondary Index) <br>&emsp; + Optimize query & scan <br>&emsp; + Check TTL (Time To Live) feature <br> - **Clean up DynamoDB resources** <br>&emsp; + Delete unnecessary test tables <br>&emsp; + Ensure no cost incurrence | 17/11/2025 | 17/11/2025 | https://000060.awsstudygroup.com/ |

### Week 6 Achievements:
**AWS CLI**
  * Installed and configured basic AWS CLI.
  * Entered Access Key ID, Secret Access Key, Region and Output format.
  * Verified AWS connection with `aws s3 ls`.
  * Created and used profiles, specified profile via environment variable.
  * Practiced S3 management: list buckets, upload/download files.
  * Practiced SNS: create topic, subscribe subscriber, send notification.
  * Practiced IAM: create user and group, assign policy, check access permissions.

**Amazon DynamoDB**
  * Familiarized with table, partition key, sort key.
  * Practiced CRUD: add, edit, delete item.
  * Enabled TTL (automatic item deletion after expiration).
  * Created table backup and restored data.
  * Added Global/Local Secondary Index.
  * Optimized query & scan.
  * Cleaned up test tables, ensured no cost incurrence.
