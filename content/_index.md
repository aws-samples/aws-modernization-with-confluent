---
title: "Confluent Cloud Kafka Data in Motion Workshop"
chapter: true
weight: 1
---

# Workshop - Building Data in Motion applications with Confluent on AWS

![Confluent Inc Logo](/images/intro/Confluent-logo.png)

### Welcome

During this workshop you will learn how to use fully-managed Confluent Cloud on AWS to source historical data into Apache Kafka and how to use ksqlDB to process credit applications in real time using the sourced historical data combined with realtime events. Once our streaming applications is working, we will sink both approved and not approved events into Amazon Redshift and finally we will visualize this data using Amazon QuickSight.

### Learning Objectives

By the end of this workshop, you will be able to

- Signing Up for Confluent Cloud
- Creating a Confluent Cloud Kafka Cluster and Topics
- Deploy CloudFormation for completing workshop exercises.
- Configuring MySQL Source and Lambda function to simulate credit data
- Create ksqlDB App which create streams with credit application outcome
- Ingest result data into Amazon Redshift table
- Visualize the data using Amazon QuickSight

{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various AWS services, Confluent Cloud can be architected to build a solution while demonstrating best practices along the way. These examples are not intended for use in production environments. Content authored by Jobin George - jobigeor@amazon.com and Joseph Morais - jmorais@confluent.io
</p>
{{% /notice %}}