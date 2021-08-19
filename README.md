# Introduction to Confluent Horizontal Workshop - FSI

![Confluent Inc Logo](https://github.com/aws-samples/aws-modernization-with-confluent/blob/main/static/images/intro/Confluent-logo.png)
## Introduction

Making decisions in near-realtime is a challenge many of us are looking to solve.  Confluent offers a number of data connectors and simplified stream processing that can make this less complicated and more reliable.  During this workshop you will learn how to use fully-managed **Confluent Cloud** on **AWS** to source historical data into Kafka, use ksqlDB to process credit applications in real time using the sourced historical data together with generated events.  Once our streaming applications is working we will sink the approved and not approved events into Amazon Redshift and finally we will visualize this data using Amazon QuickSight.

Below is how the typical use case flow looks like. As new credit applications comes through how the processing happens, decision is made with a logic and reporting is done:

![Architecture](https://github.com/aws-samples/aws-modernization-with-confluent/blob/main/static/images/intro/GenericFlow.png)

And for this workshop how the architecture looks like and AWS Services used along with Confluent Cloud:

![Architecture](https://github.com/aws-samples/aws-modernization-with-confluent/blob/main/static/images/intro/Arch.png)

