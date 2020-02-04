# Modern Data Engineering Bootcamp

## Lab 01: Stream Analytics

### Introduction
The aim of this lab is to setup and configure the basics of a Stream Analytics setup. This means creating a Stream Analytics job, configuring both input and output, writing a transformation query ending in starting the job and reviewing results. 

### Setting Up Resources

1. Open the Azure portal  and sign in to your account.
2. In the left pane, select All services.
3. In the search box, type Stream Analytics and select Stream Analytics jobs from the results.
4. On the Stream Analytics jobs page, select Add.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/3-add-jobs.png)

5. Enter a job name, such as **Bootcamp**.
6. Create a new resource group named **bootcamp-streamanalytics**.
7. Note the **Location** setting. Ideally, you should create your job in the same location as any storage accounts you use as a source or destination.
8. Ensure that the hosting environment is Cloud.
9. Set the streaming units to 1 to minimize the cost for this test.
10. Select Create to create the new job.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/3-create-new-job.png)

11. After a few moments, select **Refresh** to see your new Stream Analytics job.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/3-created-jobs.png)

Now that we have a Stream Analytics job, we're ready to set up the job to serve a streaming workload. We'll start with the input.

### Configure Input
When configuring the imput a choice can be made between three different input types:
- Azure Event Hubs
- Azure IoT Hub
- Azure Blob storage

For the purpose of this exercise we will use blob storage as input.

1. Start in the main azure screen to create a storage account.
2. On the Basics tab, select the new bootcamp-streamanalytics resource group.
3. Give the Azure Storage account a unique name. Try using the prefix streamsrc with your initials or a numeric value. This value has to be unique across all Azure storage accounts, so you might have to try a few combinations to find one that works for you. The portal displays a green check mark next to the name if it's valid.
4. Check the location. To avoid paying to transfer data between regions, set the location to the same one as the job. Altough not necessary it is best practice to safe costs as long as there is no specific business case.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/4-add-storage-account.png)

5.  **Review + Create**
6.  Navigate to the created Stream Analytics Job you created in the previous section.
7.  Under Job topology, select Inputs.
8.  Select Add stream input and select Blob storage from the list.
9.  In Input alias field, type **streaminput**. This display name identifies the input.
10. Select the storage account you created earlier. Remember, it starts with streamsrc.
11. Under Container, select Create new. Give the container a unique name, such as **bootcamp-container**.
12. Under Path pattern, enter **input/**.
13. Leave the default values in the rest of the fields.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/4-create-blob-input.png)

14. **Save**

### Configure Output
Stream Analytics jobs support various output sinks, such as Azure Blob storage, SQL Database, and Event Hubs. The documentation lists all output types.

In this exercise, we'll use Blob storage as the output sink for our Stream Analytics job.

1. In the Azure portal , create a new storage account, just like you did in the previous exercise.
2. On the **Basics** tab, select your new **bootcamp-streamanalytics** resource group.
3. For the account name, use the prefix **streamsink**, and add a numeric suffix. You might need to try a few combinations to find a unique name in Azure.
4. Use default values for all other fields.
5. **Review + Create**
6. Go to output section of your Stream Analytcs Jobs
7. Under Job topology, select Outputs.
8. Select Add, and from the list select Blob storage.
9. In the Output alias field, type **streamoutput**. This is your own name for the output.
10. Select the streamsink storage account you created in the previous section.
11. Under Container, select Create new. Give the container a unique name, such as **bootcamp-container**.
12. Under Path pattern, enter **output/**.
13. Leave the default values in the rest of the fields.
14. Select Save.

### Data
In order to test your Stream Analytics job you will have to create some sample data. 

#### Create Sample File
Start by creating a simple input file named input.json on your local computer. The file has these contents:

```
{
    "City" : "Maassluis",
    "Coordinates" :
    {
        "Latitude": 51,
        "Longitude": 4
    },
    "Census" :
    {
        "Population" : 33000,
        "Municipality" : "Maassluis",
        "Region" : "Zuid-Holland"
    }
}
```
#### Upload Sample File
Next, upload the JSON file to a Blob storage container:

1. Open the Azure portal.
2. Go to your source Blob storage account.
3. Select the streamsource Blob storage account you created earlier.
4. Under Blob service, select Blobs.
5. Select the bootcamp-container container you created. It should be empty.
6. Select Upload. Next to the Files input, select the folder icon, and then select the JSON file.
7. Expand the Advanced options if they're not expanded already.
8. In the Upload to folder field, enter input/[YYYY-MM-DD]. Here, YYYY-MM-DD is the current date and needs to be entered using the data format you noted in the exercise "Configure the Azure Stream Analytics job input". **Example: input/2020/01/01**
9. Leave the default values in the other fields.
10. Select Upload.

After the file is uploaded, you should see the input folder in the container. Select it to explore the blob hierarchy and see the data.

#### Set up Output Folder
1. Go to your destination Blob storage account.
2. From the choices on the overview page, select Storage Explorer (preview).
3. On the right, go to BLOB CONTAINERS.
4. Select the container you created.
5. From the menu above the container details, select New Folder. If you don't see this option, open the More list to find it.
6. For the folder name, type **output**, and then select Create. Here you're creating a placeholder. Azure won't show the folder until you add a file to it.

### Write Transformation Query
An Azure Stream Analytics query transforms an input data stream and produces an output. Queries are written in a language like SQL that's a subset of the Transact-SQL (T-SQL) language.

In this exercise, we'll transform the input data in a simple way to demonstrate the transformation-query capabilities that Stream Analytics exposes.

Now you're ready to write your transformation query. You'll need to pull the coordinates from the input data and write them to the output. You'll do that by using a `SELECT` statement. Find the query options online or by using the link in this module's summary.

1. Use the search field to find your Stream Analytics job in the Azure portal. Its name is **Bootcamp**(Unless you named it different).
2. Under Job topology, select Query.
3. In the Query pane, add this query:

```
SELECT City,
    Coordinates.Latitude,
    Coordinates.Longitude
INTO streamoutput
FROM streaminput
```
![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/6-write-query.png)

4. **Save**
5. Test the query -> Select **Test**

### Start Stream Analytics Job
1. On your job menu, select Overview to go back to the main overview page.
2. From the menu at the top of the page, select Start.
3. Select Now > Start.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/7-run-job.png)

The job should transition to the Starting state. After a few seconds, it will move to the Running state. The job will run for a few minutes and then finish in the Completed state. You can watch these transitions on the job's Overview page.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/7-running-job.png)

### Review Your Results
After a Stream Analytics job finishes, you can view the results in the Azure portal. On the job's Overview pane, you see the status information, the location and resource group where the service is provisioned, and the subscription details. Here you can also confirm when the service was created and started.

To see the job's results:

1. In the Azure portal, go to your output storage account.
2. Select Storage Explorer (preview).
3. On the right, under BLOB CONTAINERS, open your container.
4. Go to the output folder and select Download.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/8-query-result.png)

```
{
    "city" : "Maassluis",
    "latitude" : 51,
    "longitude" : 4
}
```
Keep all the files and resources, you will need the output 

**END OF LAB01**

## Lab 02: Azure SQL - Load external data
In this lab we will setup a SQL database to load in data stored on a blob. First step is to import data from a CSV file. For this we can re-use part of the resources from the previous lab. For the blob use the output blob or container. 

### Setting up Azure Resources
1. 1. Open the Azure portal  and sign in to your account.
2. In the left pane, select All services.
3. In the search box, type SQL Database and select Azure SQL Database from the results.
4. On the Stream Analytics jobs page, select Add.
5. Select the resource group you created in Lab 02.
6. Enter a database name, for instance with prefix **mdebootcamp**.
7. Create a sql server to host your database. 
    - Insert SQL servername, for instance with prefix **mdebootcamp**.
    - Insert Login name
    - Insert and confirm password
    - Set location to West Europe
    - Press OK.
8. In the Compute + storage section select **Basic**
9. Review + Create 

### Create flatfile on blob
1. Open text editor en create a .csv file with city, latitude, longtitude as headers
2. Create 3 or 4 sample rows.

### Configuring SQL
First step in the proces is setting up a Master Key.

1. Go to your azure portal
2. Login into your SQL database
    - You might need to whitelist your IP to login into your database
    - You might want to configure a SQL admin for your Azure SQL server
3. After you have loggedin trough the portal or management studio use the following code to create a Master Key:
```
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MDEb00tcamp';
```
```
CREATE DATABASE SCOPED CREDENTIAL bootcampblob
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'sv=2019-02-02&ss=bfqt&srt=sco&sp=rwdlacup&se=2020-02-04T02:27:48Z&st=2020-02-03T18:27:48Z&spr=https&sig=jdKQk5IfGg0EVt%2F17oAv%2FDnZHHyFS1xdZO2Pa8vWfq0%3D';
```
```
CREATE EXTERNAL DATA SOURCE xxxstor
WITH (  TYPE = BLOB_STORAGE, 
        LOCATION = 'https://streamsinkblboutput.blob.core.windows.net', 
        CREDENTIAL= bootcampblob);
```
```
BULK INSERT City
FROM 'bootcamp-container/output.csv' --random is the container name
WITH (  DATA_SOURCE = 'xxxstor',
        FORMAT='CSV', CODEPAGE = 65001, --UTF-8 encoding
        FIRSTROW=2,
        TABLOCK); 
```
