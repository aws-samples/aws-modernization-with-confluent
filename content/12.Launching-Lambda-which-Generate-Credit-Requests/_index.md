+++
title = "Launching Lambda which Generate Credit requests"
weight = 12
chapter = true
pre = "<b>12. </b>"
+++

## Launching Lambda which Generate Credit requests

While we wait for the MySQL source connector to complete provisioning, lets go ahead and start Lambda function which stream credit request data into Confluent Cloud Kafka topic.

Lets Navigate to your terminal and execute below commands.

```
$ export APIKEY= <GatewayAPIKey noted down in previous section>
$ export URL= < ApiGatewayInvokeURL noted down from CloudFormation in previous section>
$ curl -H "x-api-key: $APIKEY" -X POST $URL
```
![Subscribe](/images/lambda/1.png)

Once you execute the command, it will timeout after a few seconds, by which the lambda function which generate and produce credit application request data to a new Kafka topic named credit_applications we created in the previous section.

Now, lets move to next section.