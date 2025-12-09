---
title: "Week 9 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

* Understand architecture and operating mechanism of **Amazon Route 53**, especially **Hybrid DNS** integrating with on-premise DNS systems.
* Proficiently use **CloudWatch** to:
  * Collect logs & metrics
  * Create alarms
  * Build monitoring dashboard
  * Monitor containers with Container Insights
* Master centralized monitoring model and automated reaction automation based on events.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Start Date | Completion Date | Reference Material |
|-----|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|------------------|----------------|
| 2   | **Route 53 – DNS Architecture & Hybrid DNS** <br> - Review traditional DNS model (Authoritative, Recursive). <br> - Learn overview of Amazon Route 53: <br> &emsp; • Public Hosted Zone <br> &emsp; • Private Hosted Zone <br> &emsp; • DNS resolution process on AWS. <br> - Analyze on-premise DNS and Hybrid DNS needs. <br> - Learn Route 53 Resolver and its role. <br> - Review common records: A, AAAA, CNAME, Alias… <br> - Draw DNS operation diagram before and after Route 53 integration.                                                | 03/11/2025 | 03/11/2025      | https://000010.awsstudygroup.com/ |
| 3   | **Route 53 – Hybrid DNS** <br> - Learn Outbound Endpoints: how AWS sends queries to on-premise. <br> - Learn Inbound Endpoints: point to receive queries from on-premise. <br> - Configure Route 53 Resolver Rules: <br> &emsp; • Forwarding rule <br> &emsp; • Conditional rule <br> - Demo: create trial Outbound + Inbound endpoint. <br> - Test name resolution between AWS ↔ on-premise. <br> - Summarize common errors: timeout, loop, rule conflict, network unreachable. | 04/11/2025 | 04/11/2025       | https://000010.awsstudygroup.com/ |
| 4   | **AWS CloudWatch Workshop – Metrics & Logs** <br> - Understand CloudWatch monitoring architecture. <br> - Analyze Metrics structure: Namespace, Dimension, Retention. <br> - Distinguish Logs: Log group, Log stream, Log event. <br> - Demo: <br> &emsp; • Install CloudWatch Agent on EC2. <br> &emsp; • Send system logs to CloudWatch. <br> &emsp; • View metrics CPU, RAM, Network. <br> - Learn how to optimize CloudWatch costs.                                                                                                                        | 05/11/2025 | 05/11/2025       | https://000008.awsstudygroup.com/ |
| 5   | **AWS CloudWatch Workshop – Alarms & Automation** <br> - Create Metric Alarm with custom threshold. <br> - Create Log Filter → Log Alarm. <br> - Integrate SNS to send notifications. <br> - Create Composite Alarm with multiple conditions. <br> - Real-world simulation exercises: <br> &emsp; • CPU > 70% → send alert → Auto Scaling scale-out. <br> &emsp; • EC2 log ERROR → send notification via email.                                                                       | 06/11/2025 | 06/11/2025       | https://000008.awsstudygroup.com/ |
| 6   | **AWS CloudWatch Workshop – Dashboard & Container Insights** <br> - Create CloudWatch Dashboard displaying: <br> &emsp; • CPU, RAM, Network <br> &emsp; • ALB request count <br> &emsp; • RDS metrics <br> - Design dashboard following best practice (group panels, annotate, colors). <br> - Learn EventBridge & its role in automation. <br> - Container Insights: <br> &emsp; • Collect metrics ECS/EKS. <br> &emsp; • Investigate container restart, OOMKilled errors. <br> - Clean up all resources. | 07/11/2025 | 07/11/2025       | https://000008.awsstudygroup.com/ |

### Week 9 Achievements:
**1. Route 53 & Hybrid DNS**

* Clearly understood traditional DNS model and DNS in AWS environment.
* Mastered components in Route 53:
  * Public Hosted Zone
  * Private Hosted Zone
  * Record types (A, AAAA, CNAME, Alias)
  * Route 53 Resolver
* Understood **Hybrid DNS** architecture between on-premise and AWS.
* Configured and tested:
  * **Outbound Endpoint** for AWS to send queries to on-premise DNS.
  * **Inbound Endpoint** for on-premise to send queries to AWS.
  * **Resolver Rules** (Forwarding rule / Conditional rule).
* Practiced bi-directional DNS resolution:
  * EC2 in VPC → DNS on-premise.
  * DNS on-premise → Private Hosted Zone of AWS.
* Know how to handle common errors:
  * DNS timeout
  * Forwarding loop
  * Wrong rule priority
  * Endpoint unable to attach to VPC
* Self-draw and analyze complete Hybrid DNS architecture diagram.

**2. CloudWatch Metrics & Logs**

* Understood CloudWatch monitoring architecture and its role in AWS system.
* Mastered how Metrics work:
  * Namespace
  * Dimension
  * Statistic (Average, Sum, Maximum)
  * Metric retention 15 months
* Collected Logs through:
  * CloudWatch Log Groups
  * Log Streams
  * Log Events
* Installed and configured **CloudWatch Agent** to send:
  * System logs
  * Application logs
  * Custom metrics (CPU, RAM, Disk, Network)

**3. CloudWatch Alarm & Automation**

* Created and configured:
  * **Metric Alarm** with CPU, Network thresholds…
  * **Log Metric Filter** to detect Error/Warning in logs.
  * **Log Alarm** based on filter pattern.
* Integrated Alarm with SNS:
  * Send email alerts.
  * Send notifications when resources exceed thresholds.
* Implemented Automation model:
  * CPU > 70% → send alert → trigger Auto Scaling Scale Out.
  * ERROR in application → send notification immediately.
* Able to analyze root cause via metrics/logs to reduce MTTR.

**4. CloudWatch Dashboard & Container Insights**

* Created and customized Dashboard to monitor:
  * EC2 (CPU, RAM, Network)
  * ALB (Request count, Target health)
  * RDS (Latency, Connections)
  * Custom metrics
* Knew how to organize widgets scientifically by module.
* Used Container Insights to monitor containers:
  * CPU/memory usage by pod/task
  * Container restart, OOMKilled errors
  * Deployment, node health statistics
* Understood standard DevOps/SRE monitoring operation:
  * Observability
  * Alerting
  * Distributed logs
  * Telemetry data pipeline

**5. Resource management skills**

* Performed resource cleanup correctly to avoid cost incurrence.
* Able to recognize resources causing CloudWatch cost:
  * Metric storage
  * Log ingestion
  * High-resolution metrics
  * Dashboard widgets
