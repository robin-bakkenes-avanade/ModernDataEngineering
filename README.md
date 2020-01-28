# ModernDataEngineering

## Lab 01: Streaming Analytics

### Introduction
The aim of this lab is to setup and configure the basics of a Stream Analytics setup. This means creating a Stream Analytics job, configuring both input and output, writing a transformation query ending in starting the job and reviewing results. 

### Setting Up Resources

1. Open the Azure portal  and sign in to your account.
2. In the left pane, select All services.
3. In the search box, type Stream Analytics and select Stream Analytics jobs from the results.
4. On the Stream Analytics jobs page, select Add.

![Alt text](https://docs.microsoft.com/en-us/learn/data-ai-cert/transform-data-with-azure-stream-analytics/media/3-add-jobs.png)

5. Enter a job name, such as **Bootcamp**.
6. Create a new resource group named bootcamp-streamanalytics.
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
9.  In Input alias field, type streaminput. This display name identifies the input.
10. Select the storage account you created earlier. Remember, it starts with streamsrc.
11. Under Container, select Create new. Give the container a unique name, such as learn-container.
12. Under Path pattern, enter input/.
13. Leave the default values in the rest of the fields.





