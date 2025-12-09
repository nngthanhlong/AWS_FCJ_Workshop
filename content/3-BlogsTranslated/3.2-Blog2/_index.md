---
title: "Blog 2"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Announcing Amazon EC2 M4 and M4 Pro Mac instances

By [Sébastien Stormacq](https://aws.amazon.com/blogs/aws/author/stormacq/) on September 12, 2025 in [Amazon EC2 Mac Instances](https://aws.amazon.com/blogs/aws/category/compute/amazon-ec2-mac-instances/), [Launch](https://aws.amazon.com/blogs/aws/category/news/launch/), [News](https://aws.amazon.com/blogs/aws/category/news/) [Permalink](https://aws.amazon.com/blogs/aws/announcing-amazon-ec2-m4-and-m4-pro-mac-instances/) [Comments](https://aws.amazon.com/blogs/aws/announcing-amazon-ec2-m4-and-m4-pro-mac-instances/)

[Permalink](https://aws.amazon.com/blogs/aws/announcing-amazon-ec2-m4-and-m4-pro-mac-instances/) Comments Share
Voiced by Polly

Having used macOS since 2001 and [Amazon EC2 Mac instances](https://aws.amazon.com/ec2/instance-types/mac/) since they launched 4 years ago, I have helped many customers scale their continuous integration & deployment (CI/CD) pipelines on AWS. Today, I am thrilled to share that **M4** and **M4 Pro** Mac Amazon EC2 instances are now officially available.

Development teams building applications for Apple platforms need powerful computing resources to handle complex build processes and run multiple iOS simulators simultaneously. As development projects grow increasingly larger and sophisticated, teams need higher performance and memory capacity to maintain fast development cycles.

**Apple M4 Mac mini at the Core**

The EC2 M4 Mac instances (called mac-m4.metal in the API) are built on the [Apple M4 Mac mini](https://www.apple.com/mac-mini/specs/) and use the [AWS Nitro System](https://aws.amazon.com/ec2/nitro/). They feature Apple silicon M4 chip with 10 CPU cores (four performance and six efficiency cores), 10-core GPU, 16-core Neural Engine, and 24 GB unified memory, delivering improved performance for iOS and macOS application build workloads. When building and testing applications, M4 Mac instances deliver up to 20% better application build performance compared to EC2 M2 Mac instances.

The EC2 M4 Pro Mac instance (mac-m4pro.metal in the API) is equipped with Apple silicon M4 Pro chip with 14 CPU cores, 20 GPU cores, 16-core Neural Engine, and 48 GB unified memory. These instances provide up to 15% better application build performance compared to EC2 M2 Pro Mac instances. The increased memory capacity and compute power enable running multiple test iterations in parallel with multiple device simulators.

Each M4 and M4 Pro Mac instance now comes with 2 TB of local storage, providing low-latency storage to improve caching and build & test performance.

Both instance types support macOS **Sonoma version 15.6 and newer** as [Amazon Machine Images (AMIs)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html). The AWS Nitro system provides [Amazon Virtual Private Cloud (Amazon VPC)](https://aws.amazon.com/vpc/) network bandwidth up to 10 Gbps and [Amazon Elastic Block Store (Amazon EBS)](https://aws.amazon.com/ebs/) storage bandwidth of 8 Gbps over high-speed Thunderbolt connections.

EC2 Mac instances integrate seamlessly with AWS services, meaning you can:

* Build automated CI/CD pipelines using AWS CodeBuild and AWS CodePipeline

* Store and manage multiple versions of your build secrets, such as Apple development certificates and keys, on AWS Secrets Manager

* Manage your development infrastructure using AWS CloudFormation

* Monitor instance performance with Amazon CloudWatch

**How to Get Started**

You can launch an EC2 M4 or M4 Pro Mac instance through the [AWS Management Console](https://console.aws.amazon.com/), [AWS Command Line Interface (AWS CLI)](https://aws.amazon.com/cli/), or [AWS SDKs](https://aws.amazon.com/tools/).

In the demo example, I will start an M4 Pro instance from the console. I first allocate a **dedicated host** to run my instances. On the [AWS Management Console](https://console.aws.amazon.com/) I go to EC2, then **Dedicated Hosts**, and select **Allocate Dedicated Host**.

Then, I enter a Name tag and select the instance Family (mac‑m4pro) and instance type (mac‑m4pro.metal). I select an Availability Zone and uncheck Host maintenance.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a1.png)

EC2 Mac M4 – Dedicated hosts

Or I can use CLI:

**aws ec2 allocate-hosts                          \
        --availability-zone-id "usw2-az4"       \
        --auto-placement "off"                  \
        --host-recovery "off"                   \
        --host-maintenance "off"                \
        --quantity 1                            \
        --instance-type "mac-m4pro.metal"**

After the dedicated host is allocated to my account, I select the newly allocated host, then select the Actions menu and choose Launch instance(s) onto host.

Note that the console provides you, among other information, the latest supported macOS versions for this host type. In this case, macOS 15.6.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a2.png)

On the Launch an instance page, I enter the Name. I select a macOS Sequoia AMI. I ensure the Architecture is Arm 64-bit and the instance type is mac-m4pro.metal.

The remaining parameters are not specific to EC2 Mac: network configuration and storage. When launching an instance for development, be sure to select a volume of at least 200 GB or more. The default 100 GB volume is not enough to download and install Xcode.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a3.png)

When ready, I click the orange Launch instance button at the bottom of the page. The instance will quickly appear in the Running state in the console. However, it may take up to 15 minutes before you can connect via SSH.

Or I can use this command:

**aws ec2 run-instances \
    --image-id "ami-000420887c24e4ac8" \  # AMI ID varies by region !
    --instance-type "mac-m4pro.metal"   \
    --key-name "my-ssh-key-name"        \
    --network-interfaces '{"AssociatePublicIpAddress":true,"DeviceIndex":0,"Groups":["sg-0c2f1a3e01b84f3a3"]}' \ # Security Group ID depends on your config \
    --tag-specifications '{"ResourceType":"instance","Tags":[{"Key":"Name","Value":"My Dev Server"}]}' \
    --placement '{"HostId":"h-0e984064522b4b60b","Tenancy":"host"}' \ # Host ID depends on your config  
    --private-dns-name-options '{"HostnameType":"ip-name","EnableResourceNameDnsARecord":true,"EnableResourceNameDnsAAAARecord":false}' \
    --count "1"**

**Installing Xcode from Terminal**

After the instance is accessible, I can connect via SSH and install development tools. I use [xcodeinstall](https://github.com/sebsto/xcodeinstall) to download and install [Xcode 16.4](https://developer.apple.com/documentation/Xcode-Release-Notes/xcode-16_4-release-notes).

From my laptop, I open a session with Apple developer credentials:

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a4.png)

I connect to the EC2 Mac instance I just launched. Then, I download and install Xcode:

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a5.png)

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a6.png)

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a7.png)

**Things to Know**

* Select an EBS volume of at least 200 GB for development purposes. The default 100 GB volume is not enough to install Xcode. I typically choose 500 GB. When increasing EBS size after instance launch, remember to resize the APFS filesystem.

* Alternatively, you can choose to install your development tools and frameworks on the 2 TB low-latency internal SSD available in Mac mini. Note that the contents of this volume are attached to the instance lifecycle, not the dedicated host. This means everything will be deleted from the internal SSD when you stop and restart the instance.

* The mac-m4.metal and mac-m4pro.metal instances support macOS Sequoia 15.6 and newer versions.

* You can migrate existing EC2 Mac instances when the migration instance is running macOS 15 (Sequoia). Create a custom AMI from your existing instance and launch an M4 or M4 Pro instance from that AMI.

Finally, I suggest you check the guides I wrote to help you get started with EC2 Mac:

* [Launch an EC2 Mac instance](https://builder.aws.com/content/2duUEgh4u4TIDqfECiDkEbrn2Iw/start-an-amazon-ec2-mac-instance)

* [Connect to an EC2 Mac instance](https://builder.aws.com/content/2duUtYq4ENzOLGLdEg0A3aeyCuj/connect-to-an-amazon-ec2-mac-instance) (I show you three different ways to connect)

* [Build your iOS applications faster with a CI/CD pipeline on EC2 Mac](https://builder.aws.com/content/2duRxOl9WuYETq6dMhAQQ1kDZLr/build-your-ios-applications-faster-with-a-cicd-pipeline)

**Pricing and Availability**

EC2 M4 and M4 Pro Mac instances are now available in **US East (N. Virginia)** and **US West (Oregon)**, with plans to expand to other regions in the future.

EC2 Mac instances can be purchased as **Dedicated Hosts** under On-Demand pricing and [Savings Plans](https://aws.amazon.com/savingsplans/). EC2 Mac billing is per second with a minimum of 24 hours allocation to comply with Apple's macOS software license agreement. After the 24-hour minimum, the host can be released at any time without further commitment.

As someone working closely with Apple developers, I am curious to see how you will use these new instances to accelerate your development cycle. The combination of increased performance, improved memory capacity, and integration with AWS services opens up many possibilities for teams building applications for iOS, macOS, iPadOS, tvOS, watchOS, and visionOS. Beyond application development, the Neural Engine of Apple silicon makes these instances a cost-effective candidate for running machine learning (ML) inference workloads. I will discuss this topic in detail at AWS re:Invent 2025, where I will share benchmarks and best practices to optimize ML workloads on EC2 Mac.

To learn more about EC2 M4 and M4 Pro Mac instances, you can visit the [Amazon EC2 Mac Instances](https://aws.amazon.com/ec2/instance-types/mac/) page or consult the [EC2 Mac documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-mac-instances.html). You can start using these instances today to modernize your Apple development workflows on AWS.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.2-Blog2/a8.png)

[Sébastien Stormacq](https://linktr.ee/sebsto)

Seb has been writing code since the Commodore 64 in the eighties. He inspires builders to unlock the value of AWS cloud, using a secret blend of passion, enthusiasm, customer advocacy, curiosity, and creativity. He is interested in software architecture, developer tools, and mobile computing. If you want to sell him something, make sure it has an API. Follow @sebsto on Bluesky, X, Mastodon, and other platforms.


---
