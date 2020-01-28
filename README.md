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

1. Make 
