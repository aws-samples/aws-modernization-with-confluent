+++
title = "Creating AWS resources required"
weight = 8
chapter = true
pre = "<b>8. </b>"
+++

## Launching CloudFormation to create AWS resources needed for the Workshop

Now while logged into your AWS account, click on the **Launch Stack** button below on the region you have selected while creating Confluent Cloud cluster.

{{% notice warning %}}
<p style='text-align: left;'>
It is very important to deploy CloudFormation and creating AWS resources in the same region as Confluent Cloud Cluster for this workshop to function properly.
</p>
{{% /notice %}}

|            us-west-2                |            us-east-2                |          us-east-1            |
| ----------------------------------- | ----------------------------------- | ----------------------------- |
| [![I](/images/cft/ls.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/review?stackName=ConfluentWorkshop&templateURL=https://cloudformation-template-repo.s3.amazonaws.com/ConfluentWorkshop-west2.json)   | [![I](/images/cft/ls.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/create/review?stackName=ConfluentWorkshop&templateURL=https://cloudformation-template-repo.s3.amazonaws.com/ConfluentWorkshop-east2.json)     |[![I](/images/cft/ls.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=ConfluentWorkshop&templateURL=https://cloudformation-template-repo.s3.amazonaws.com/ConfluentWorkshop-east1.json)|

When clicked on the launch stack button, it will take you to CloudFormation create Stack page, Provide **API Key**, **Api Secret** and **BootStrap Server** , acknowledge the capabilities and click **Create Stack** button.  

![Subscribe](/images/cft/1.png)
This will start creating the AWS resources required and will take about 10minutes to complete the creation. 

Once completed, navigate to the **outputs** tab and make a note of ApiGatewayInvokeURL, MySqlEndpoint, RedshiftEndpoint and keep them handy for using in following sections: 
![Subscribe](/images/cft/2.png)

Navigate to **Resources** Tab and click on **GatewayApiKey** physical id

![Subscribe](/images/cft/3.png)

It will take you to the **GatewayAPIKey** resource, click on the **show** button near **API Key** to reveal the key, and make a note of it to use in the next session. 

![Subscribe](/images/cft/4.png)

Once you have noted down the **GatewayAPIKey**, **ApiGatewayInvokeURL**, **MySqlEndpoint** and **RedshiftEndpoint**, lets navigate back to Confluent Cloud UI for next steps.
