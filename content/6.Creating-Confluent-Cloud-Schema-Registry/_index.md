+++
title = "Creating Confluent Cloud Schema registry"
weight = 6
chapter = true
pre = "<b>6. </b>"
+++

## Creating Confluent Cloud Schema registry 

On the left bottom, click on “Schema registry” 

![Subscribe](/images/createSR/1.png)

Click **Set up on my own** and on the next page, select **AWS** and Region as **US** then click continue. 

![Subscribe](/images/createSR/2.png)

Now the schema registry is created and you could see the API endpoint listed on the UI.  

![Subscribe](/images/createSR/3.png)

With this step, you have created all the confluent cloud resources needed for completing the workshop. But before we proceed to next step, lets note down the bootstrap URL for the cluster.

While you are in the Cluster Page, Select Settings from left panel and note down/copy the **Bootstrap server** URL, you would need it during next section.

![Subscribe](/images/createSR/4.png)

Now you have Bootstrap server URL, API Key and API Secret handy to proceed with next section, where you will pass those as inputs for CloudFormation Deployments in the later step.