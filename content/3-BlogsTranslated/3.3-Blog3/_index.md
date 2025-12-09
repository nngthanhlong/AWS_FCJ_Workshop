---
title: "Blog 3"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Harnessing the Power of AWS IoT Rules with Substitution Templates

By Andrea Sichel and Avinash Upadhyaya on September 17, 2025 in [Advanced (300)](https://aws.amazon.com/blogs/iot/category/learning-levels/advanced-300/), [Architecture](https://aws.amazon.com/blogs/iot/category/architecture/), [AWS IoT Core](https://aws.amazon.com/blogs/iot/category/internet-of-things/aws-iot-platform/), [AWS Lambda](https://aws.amazon.com/blogs/iot/category/compute/aws-lambda/), [Best Practices](https://aws.amazon.com/blogs/iot/category/post-types/best-practices/), [Intermediate (200)](https://aws.amazon.com/blogs/iot/category/learning-levels/intermediate-200/), [Internet of Things](https://aws.amazon.com/blogs/iot/category/internet-of-things/), [Technical How-to](https://aws.amazon.com/blogs/iot/category/post-types/technical-how-to/)

[AWS IoT Core](https://aws.amazon.com/iot-core/) is a managed service that helps you securely connect billions of Internet of Things (IoT) devices to AWS cloud. The [AWS IoT rules engine](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rules.html) is a component of AWS IoT core that provides SQL-like capabilities to filter, transform, and decode your IoT device data. You can use AWS IoT rules to route over 20 AWS services and HTTP endpoints by using [AWS IoT rule actions](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rule-actions.html). [Substitution templates](https://docs.aws.amazon.com/iot/latest/developerguide/iot-substitution-templates.html) are a capability in IoT rules that help enrich the JSON data returned when an IoT rule is triggered and AWS IoT performs an action. This blog post explores how AWS IoT rule actions with substitution templates unlock simpler, more powerful IoT architectures. You will learn proven ways to cut costs and increase scalability. Through real-world examples of message routing and load balancing, you will build smarter, more efficient IoT solutions.

**Understanding the Basic Components**

Each AWS IoT rule is built on three basic components: an SQL-like statement that handles message filtering and transformation, one or more AWS IoT rule actions that run and route data to other various AWS services and third-party services, and optional functions that can be used in both the SQL statement and rule actions.

Here's an example of an AWS IoT rule and its components.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.3-Blog3/a1.png)

The SQL statement acts as the rule processing gateway and determines which MQTT messages will be processed based on specific topic patterns and conditions. This rule uses a SQL-like statement and supports SELECT, FROM, and WHERE clauses (for more information, see [AWS IoT SQL reference](https://docs.aws.amazon.com/iot/latest/developerguide/iot-sql-reference.html)). In this structure, the FROM clause defines the MQTT topic filter, while the SELECT and WHERE clauses specify which data elements will be extracted or transformed from incoming messages.

Functions are essential to both SQL statements and rule actions in IoT rules. AWS IoT rules provide a rich collection of [built-in functions](https://docs.aws.amazon.com/iot/latest/developerguide/iot-sql-functions.html) designed to transform data types, manipulate strings, perform mathematical operations, process timestamps, and much more. Additionally, AWS IoT rules also provide external functions that help you retrieve data from AWS services (such as Amazon DynamoDB, AWS Lambda, Amazon Secrets Manager, and AWS IoT Device Shadow) and embed that data in your message payload. These functions support complex data transformations directly within the rule processing pipeline and eliminate the need for external processing.

Rule actions determine the destination and how processed data is handled. AWS IoT rules support a library of [built-in rule actions](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rule-actions.html) that can transmit data to AWS services such as AWS Lambda, Amazon Simple Storage Service (Amazon S3), Amazon DynamoDB, and Amazon Simple Queue Service (Amazon SQS). These rule actions can also transmit data to third-party services like Apache Kafka. Each rule action can be configured with specific parameters that govern how data is delivered or processed by the destination service.

**Substitution Templates: The Hidden Gem**

You can implement functions in the SELECT and WHERE clauses of AWS IoT rules to transform and prepare message data. However, if you apply this approach too frequently, you might miss the powerful option of using substitution templates and performing transformations directly in the action of your IoT rule.

Substitution templates support dynamic insertion of rule values and functions into rule action JSON using the ${expression} syntax. These templates support many of the same functions as SQL statements, such as timestamp manipulation, encoding/decoding operations, string processing, and topic extraction. By using substitution templates in AWS IoT rule actions, you can implement sophisticated routing that significantly reduces complexity in other layers of your architecture, delivering simpler, more powerful AWS IoT solutions.

**Real-World Implementation Patterns**

Let's explore some real-world examples that demonstrate the flexibility and power of using substitution templates in AWS IoT rule actions. These examples will illustrate how this feature can simplify IoT data processing workflows and unlock new possibilities for your IoT applications.

**Example 1: Conditional Message Distribution Using AWS IoT Registry Attributes**

Consider a common IoT scenario where a message distribution platform delivers device messages to different business partners, and each partner has their own SQS message processing queue. Different partners own each device in the fleet, and their relationship is maintained in the registry as an attribute called partnerId.

The traditional approach involves the following:

* **Option 1** – Maintain partner routing logic on the device. Multiple AWS IoT rules based on WHERE conditions to input payload:
  * Requires the device to know the partner's ID.
  * Increases device complexity and maintenance.
  * Creates security concerns when exposing partner identifiers.
  * Makes managing partner changes difficult.

* **Option 2** – Use an intermediate Lambda function to retrieve the partner ID value associated with the device from the AWS IoT registry and then deliver the message to the partner's specific SQS queue:
  * Adds unnecessary compute and registry query costs.
  * May increase message latency.
  * Creates additional points of failure.
  * Requires maintaining routing logic.
  * May encounter Lambda concurrency limits.

Here is a more sophisticated solution and process using substitution templates and the new AWS IoT [attribute propagation feature](https://docs.aws.amazon.com/iot/latest/developerguide/thing-types-propagating-attributes.html):

Insert Partner ID as an attribute in the AWS IoT registry.

* Use the attribute propagation feature to enrich your MQTTv5 user properties and dynamically build Amazon SQS queue URLs using the device's partnerId. See the example below:

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.3-Blog3/a2.png)

Using this solution, a device with partnerId="partner123″ will publish a message. This message will automatically be routed to the SQS queue "partner-queue-partner123".

Benefits of this solution:

The use of substitution templates significantly simplifies architecture and provides a scalable and maintainable solution for partner-specific message distribution. This solution,

  * Eliminates the need for additional compute resources.
  * Provides instant routing without increasing latency.
  * Simplifies managing partner relationships through updates in the AWS IoT registry. For example, introducing a new partner can be updated by modifying registry attributes. This update does not require any updates or changes to the device or routing logic.
  * Maintains security by not exposing queue information to devices.

**Example 2: Intelligent Load Balancing with Amazon Kinesis Data Firehose**

Consider a scenario where millions of devices publish telemetry measurement data to the same topic. It is also necessary to distribute this large volume of data across multiple Amazon Data Firehose streams to avoid congestion issues when buffering data into Amazon S3.

The traditional approach includes:

* Device-side load balancing:
  * Deploy configuration management to provide different stream IDs across devices.
  * Require devices to include the target stream in their messages.
  * Create multiple AWS IoT rules to match specific stream IDs.
  
* AWS Lambda-based routing:
  * Deploy a Lambda function to distribute messages across streams.
  * Implement custom load balancing logic.
  
Traditional approaches also create similar negative impacts as mentioned in the previous example (maintenance costs, security vulnerabilities, device complexity, additional costs, increased latency, and points of failure). Moreover, they pose specific challenges in large workload scenarios, such as the risk of high bandwidth throttling and complex stream management.

By leveraging AWS IoT rule substitution templates, you can implement a serverless, streamlined load balancing solution that dynamically assigns messages to different Firehose distribution streams by:

1. Creating a random number from 0-100000 using rand()*100000.
2. Converting (casting) this random number to an integer.
3. Using the modulo (mod) operation to get the remainder when dividing by 8.
4. Adding this remainder (0-7) to the "firehose_stream_" base name.
   
The result is that messages are randomly distributed across eight different Amazon Data Firehose streams (firehose_stream_0 through firehose_stream_7). See the example below:

```json
{ 
  "ruleArn": 
    "arn:aws:iot:us-east-1:123456789012:rule/testFirehoseBalancing", 
  "rule": { 
    "ruleName": "testFirehoseBalancing", 
    "sql": "SELECT * FROM 'devices/+/telemetry'", 
    "description": "", 
    "createdAt": "2025-04-11T11:09:02+00:00", 
    "actions": [ 
        { "firehose": { 
            "roleArn": "arn:aws:iam::123456789012:role/service-role/firebaseDistributionRoleDemo", 
            "deliveryStreamName": "firehose_stream_${mod(cast((rand()*100000) as Int),8)}", 
            "separator": ",",
            "batchMode": false 
        } 
     } 
    ], 
  "ruleDisabled": false, 
  "awsIotSqlVersion": "2016-03-23" 
  }
}
```

Benefits of this solution:

This flexible load balancing model helps process large volumes of messages by distributing the load across multiple streams. The key advantage of this approach lies in its scalability. By modifying the modulo function (which determines the remainder of division, for example: 5 mod 3 = 2), the divisor (currently set to 8) can be adjusted to match the desired number of streams. For example:

* Change to mod(…, 4) to distribute across 4 streams.
* Change to mod(…, 16) to distribute across 16 streams.
  
Using this pattern makes it easy to scale your architecture up or down without changing the core logic of the rule.

**Example 3: Using CASE Statements in Substitution Templates to Build Conditional Routing Logic**

Consider a situation where you need to route your IoT device data, depending on the specific device, to either a production Lambda function or a development/testing (Dev/Test) Lambda function.

The traditional approach includes the following:

Device-side load balancing:

* Deploy configuration management to provide different environment IDs across devices.
* Require devices to include the environment ID in their messages.
* Create multiple AWS IoT rules to match specific environment IDs.
  
AWS Lambda-based routing:

* Deploy a Lambda function to distribute messages to different AWS Lambda functions across environments after checking with the AWS IoT registry (or alternative database).

Traditional approaches also have similar negative impacts as mentioned in previous examples.

Here is a more sophisticated solution and process using substitution templates and the new AWS IoT [attribute propagation feature](https://docs.aws.amazon.com/iot/latest/developerguide/thing-types-propagating-attributes.html):

* Associate environment ID as an attribute to all devices in AWS IoT Registry
* Use the attribute propagation feature to enrich your MQTTv5 user properties
* Use propagated attributes to dynamically build the AWS Lambda function ARN in a CASE statement embedded in the AWS IoT Rule action definition.

See the example below:

```json
{ 
  "ruleArn": 
    "arn:aws:iot:us-east-1:123456789012:rule/ConditionalActions", 
  "rule": { 
    "ruleName": "testLambdaConditions", 
    "sql": "SELECT * FROM 'devices/+/telemetry'", 
    "description": "", 
    "createdAt": "2025-04-11T11:09:02+00:00", 
    "actions": [ 
        { "lambda": { 
            "functionArn": 
                "arn:aws:lambda:us-east-1:123456789012:function:${CASE get(get_user_properties('environment'),0) 
                    WHEN \"PROD\" THEN \"message_handler_PROD\" 
                    WHEN \"DEV\" THEN \"message_handler_DEV\" 
                    WHEN NULL THEN \"message_handler_PROD\" 
                    ELSE \"message_handler_PROD\" END }",  
        } 
     } 
  ], 
  "ruleDisabled": false, 
  "awsIotSqlVersion": "2016-03-23" 
 }
}
```

Benefits of this solution:

The use of substitution templates significantly simplifies architecture and provides a scalable and maintainable solution for partner-specific message distribution. This solution,

* Eliminates the need to define separate IoT rules and rule actions for each condition.
* Helps you reduce the cost of using IoT rules and rule actions.

**Conclusion:**

This blog post has explored how substitution templates for AWS IoT rules can transform complex IoT architectures into sophisticated and efficient solutions. The examples have demonstrated that substitution templates are not just a feature – they are a powerful architectural tool that leverages the capabilities of AWS IoT to effectively solve complex challenges without adding complexity or cost. Substitution templates provide a serverless, scalable approach that eliminates the need for additional computing resources or complex client-side logic. This approach not only reduces operational costs but also delivers immediate cost benefits by eliminating unnecessary computing resources and simplifying the overall architecture.

The next time you find yourself designing AWS IoT message routing patterns or facing scalability challenges, consider how substitution templates can provide a simpler and more efficient solution. By leveraging the powerful features of AWS IoT, you can create IoT solutions that are more maintainable, cost-effective, and scalable, truly serving your business needs.

Remember: The simplest solution is often the most sophisticated one. With AWS IoT rule substitution templates, that simplicity is built in.


---
