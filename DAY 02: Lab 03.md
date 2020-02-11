# Modern Data Engineering Bootcamp

## Lab 03: Databricks exercise & Hands-on labs

### Deploy an Azure Databricks workspace
Open the *Azure portal*.

Click *Create a Resource* in the top left

Search for "Databricks"

Select Azure Databricks

On the *Azure Databricks* page select *Create*

Provide the required values to create your Azure Databricks workspace:

1. **Workspace Name**: Provide a name for your workspace.
2. **Subscription**: Choose the Azure subscription in which to deploy the workspace.
3. **Resource Group**: Use Create new and provide a name for the new resource group.
4. **Location**: Select a location near you for deployment. For the list of regions that are supported by Azure Databricks, see Azure services available by region.
5. **Pricing Tier**: Trial (Premium - 14 days Free DBUs). You must select this option when creating your workspace or you will be charged. The workspace will suspend automatically after 14 days. When the trial is over you can convert the workspace to Premium but then you will be charged for your usage.
6. **Accept the terms and conditions.**

Select **Create.**

The workspace creation takes a few minutes. During workspace creation, the Submitting deployment for Azure Databricks tile appears on the right side of the portal. You might need to scroll right on your dashboard to see the tile. There's also a progress bar displayed near the top of the screen. You can watch either area for progress.



### Create Cluster

1. In the **Azure portal**, click All resources menu on the left side navigation and select the **Databricks workspace** you created in the last unit.

2. Select Launch Workspace to open your **Databricks workspace** in a new tab.

3. In the left-hand menu of your Databricks workspace, select **Clusters**.

4. Select **Create Cluster** to add a new cluster.

![alt](https://docs.microsoft.com/nl-nl/learn/databricks/intro-to-azure-databricks/media/create-a-cluster.png)


5. Enter a **name** for your cluster. Use your name or initials to easily differentiate your cluster from your coworkers.

6. Select the Databricks RuntimeVersion. **YOU NEED TO USE 5.5**

7. Specify your cluster configuration. While on the 14 day free trial, the **defaults will be sufficient**. When the trial is ended, you may prefer to change Min Workers to zero. That will allow the compute resources to shut down when you are not in a coding exercise and reduce your charges.

Select Create Cluster.


### Clone the Databricks archive
1. From the **Azure portal**, go to your Databricks workspace and select Launch workspace.

2. In the left pane, select Workspace, select Users, and then select your username (the entry with the house icon).

3. In the pane that appears, select the downward-pointing chevron next to your name, and then select **Import**.

4. In the **Import Notebooks** pane, select URL, and paste in the following URL:  https://github.com/MicrosoftDocs/mslearn-perform-basic-data-transformation-in-azure-databricks/blob/master/DBC/05.1-Basic-ETL.dbc?raw=true

5. Select **Import**.

6. A folder named after the archive should appear. Select that **05.1-Basic-ETL** folder. The folder contains one or more notebooks that you'll use in completing this lab.

#### Complete the following notebooks
To complete the labs, continue working within your Azure Databricks workspace and open the new **05.1-Basic-ETL** folder. Within the folder, you'll find **Python**, Scala, and Spark subfolders.

Choose the folder for the language you prefer to use (**Python**), open the corresponding folder, and then open the notebook.

Follow the instructions within the notebook until you've completed the entire notebook. Then continue with the remaining notebooks in order:

01-Course-Overview-and-Setup: This notebook gets you started with your Databricks workspace.

02-ETL-Process-Overview: This notebook contains exercises to help you query large data files and visualize your results.

03-Connecting-to-Azure-Blob-Storage: You do basic data aggregation and joins in this notebook.

04-Connecting-to-JDBC: This notebook lists the steps for accessing data from various sources by using Databricks.

05-Applying-Schemas-to-JSON: In this notebook, you learn how to query JSON and hierarchical data with DataFrames.

06-Corrupt-Record-Handling: This notebook lists exercises that help you create an Azure Data Lake Storage Gen2 storage account and use Databricks DataFrames to query and analyze this data.

07-Loading-Data-and-Productionalizing: Here you use Databricks to query and analyze data stores in Azure Data Lake Storage Gen2.

Parsing-Nested-Data: This notebook is in the Optional subfolder. It includes a sample project you can explore later.


