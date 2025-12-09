---
title: "Week 2 Worklog"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* This week focuses on a deeper understanding of AWS networking services, starting from VPC and foundational components to advanced connectivity solutions and load balancing systems.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                      | Start Date | Completion Date | Reference Material                          |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | --------------------------------------- |
| 2   | - Understand VPC concepts and how AWS organizes virtual networks <br> - Create a new VPC <br> - Create public/private subnets <br> - Set up Route Table and assign appropriate routes                   | 15/09/2025   | 15/09/2025      | https://000003.awsstudygroup.com/ |
| 3   | - Attach Internet Gateway to VPC <br> - Configure routes for public subnet to Internet <br> - Create NAT Gateway for private subnet <br> - Check EC2 connectivity for public/private       | 16/09/2025   | 16/09/2025      | https://000003.awsstudygroup.com/ |
| 4   | - Understand Security Group & Network ACL <br> - Compare SG and NACL <br> - Experiment: SG allow but NACL deny to observe results                                          | 17/09/2025   | 17/09/2025      | https://000003.awsstudygroup.com/ |
| 5   | - Understand ALB, NLB, GWLB <br> - Create ALB <br> - Create 2 EC2 running simple web servers <br> - Attach EC2 to Target Group <br> - Check load balancing operations                  | 18/09/2025   | 18/09/2025      | https://000003.awsstudygroup.com/ |
| 6   | - Understand VPC Peering <br> - Create 2 VPCs and establish Peering <br> - Check communication between 2 EC2 in two VPCs <br> - Learn more about Transit Gateway                         | 19/09/2025   | 19/09/2025      | https://000003.awsstudygroup.com/ |


### Week 2 Achievements:

* Understood what VPC is and mastered the basic network components in AWS including:
  * VPC
  * Subnet (Public / Private)
  * Route Table
  * Internet Gateway (IGW)
  * NAT Gateway

* Successfully created and configured a complete VPC:
  * Created a new VPC
  * Created public and private subnets
  * Assigned Route Tables to each subnet
  * Set up routes to the Internet

* Connected VPC to the Internet through:
  * Internet Gateway for public subnet
  * NAT Gateway for private subnet
  * Verified connectivity between EC2 instances in both subnets

* Understood AWS network security model:
  * Difference between Security Group and Network ACL
  * How to configure inbound/outbound rules
  * Tested scenarios where SG allows but NACL blocks and vice versa

* Deployed basic load balancing system:
  * Created Application Load Balancer (ALB)
  * Created 2 EC2 instances serving as web servers
  * Created and configured Target Group
  * Verified traffic distribution across EC2 instances

* Understood advanced VPC connectivity solutions:
  * Learned about VPC Peering
  * Created and configured Peering between 2 VPCs
  * Verified communication between EC2 in different VPCs
  * Grasped the role of Transit Gateway in large systems

* Able to build network architecture diagrams:
  * Draw VPC diagrams
  * ALB + EC2 diagrams
  * VPC Peering diagrams

* Gained a comprehensive view of AWS networking and confident in operating important networking services.

