+++
title = "Creating a Confluent Cloud Kafka Cluster"
weight = 4
chapter = true
pre = "<b>4. </b>"
+++

## Creating a Confluent Cloud Kafka Cluster

Once you Log in, you will see a pop-up asking few details regarding your Kafka experience and roles. Click skip and go ahead. 

On the next page, it will show options to configure your Confluent Cloud Kafka Cluster. Select Cluster Type as **Basic** and click **Begin Configurations**

![Subscribe](/images/createCC/1.png)

On the next page, Select AWS and choose **Region** as any from the below 3 and **Availability** as Single zone for the workshop and click **Continue**: 

| Region      | us-west-2 | us-east-2 | us-east-1 |
| ----------- | --------- | --------- | --------- |

![Subscribe](/images/createCC/2.png)

On the next page, you will be asked to provide a credit card number to keep on file, provide that and click **Review**. But note that you will have $200 USD free usage balance which will be more than enough to complete this workshop and hence you won’t be charged.

![Subscribe](/images/createCC/3.png)

Click Review and proceed to next page. On the next page, provide a name for your cluster, say **Confluent Workshop** and click **Launch cluster**. The cluster will be created instantly.

![Subscribe](/images/createCC/4.png)

within a few seconds you will have a Confluent Cloud Kafka cluster up and running. Lets proceed with next steps