+++
title = "Visualization using Amazon QuickSight"
weight = 14
chapter = true
pre = "<b>14. </b>"
+++

## Visualizing Application Status using Amazon QuickSight

Navigate to [Amazon QuickSight](https://quicksight.aws.amazon.com/sn/start/data-sets) dataset page to start create a dataset from Amazon Redshift. click on  **New dataset** on the right top corner. 
![Subscribe](/images/quicksight/1.png)

Select **Redshift Auto-discovered** from the option, like shown below:

![Subscribe](/images/quicksight/2.png)

On the next page, provide below details and make sure validation is successful and then click “Create data source”

| Key                    |  Value                                        |
| ---------------------  | --------------------------------------------- |
| Data source name       | Confluent_Workshop_Data                       |
| Instance ID            | *Select Your Cluster from Dropdown*           |
| Connection type        | Public Network                                |
| Database name          | streaming-data                                |
| Username               | awsuser                                       |
| Password               | Awsuser01                                     |

![Subscribe](/images/quicksight/3.png)

On the next page, select **pksql-xxxxxapproved_application** from the list and click **Select**

![Subscribe](/images/quicksight/4.png)

Select **Directly query the data** and click Visualize button to start some basic **visualization** creation using Amazon QuickSight:

![Subscribe](/images/quicksight/5.png)

On the next page, Click on Pie Chart to create a basic visualization, for **Group**, drag and drop **credit_type** and for **Value** drag and drop **amount** to get a visualization which shows different types of Credit application types and sum of the amount approved. Hove over the pie will show you the total amount like show in the screenshot below:

![Subscribe](/images/quicksight/6.png)

We are just creating a sample visualization as above, you can repeat the steps for visualizing rejected applications similarly.  

Also, you can learn more about how to create multi visual analysis and dashboards using Amazon QuickSight with the help of this [Tutorial](https://docs.aws.amazon.com/quicksight/latest/user/example-analysis.html)

This is the last section of this workshop, now lets go ahead and clean-up.