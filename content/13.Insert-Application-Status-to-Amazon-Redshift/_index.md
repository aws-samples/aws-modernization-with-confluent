+++
title = "Insert Application Status to Amazon Redshift"
weight = 13
chapter = true
pre = "<b>13. </b>"
+++

## Insert Application Status to Amazon Redshift

Now lets create another connector, Navigate to connectors page and search for **Redshift**
![Subscribe](/images/redshift/1.png)

And Click on the Redshift connector:
![Subscribe](/images/redshift/2.png)

On the configuration page, enter the below details, for topics, select the ones starts with 'pksqlc', click review and Launch:

| Key                    |  Value                                        |
| ---------------------  | --------------------------------------------- |
| Topics                 | *pksqlc-xxxxxAPPROVED_APPLICATIONS*,*plsqlc-xxxxxREJECTED_APPLICATIONS* |
| Name                   | RedshiftConnector                             |
| Kafka API Key          | *Your Kafka API Key*                          |
| Kafka API Secret       | *Your Kafka API Secret*                       |
| Input Message Format   | Avro                                          |
| Amazon Redshift Domain | *redshift host from AWS CloudFormation output*|
| Amazon Redshift Port   | 5439                                          |
| Connection user        | awsuser                                       |
| Connection password    | Awsuser01                                     |
| Database name          | streaming-data                                |
| Database Timezone      | America/Los_Angeles                           |
| Auto Create Table      | TRUE                                          |
| Auto Add Columns       | TRUE                                          |
| Tasks                  | 1                                             |

Within a few minutes, the connector would be provisioned and up and running. Once it start, it automatically consumes all the messages in both the topics and insert them into Redshift Cluster.

Now, lets move to next section inorder to validate the records inserted.