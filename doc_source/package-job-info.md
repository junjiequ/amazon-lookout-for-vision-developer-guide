# Getting information about model packaging jobs<a name="package-job-info"></a>


|  | 
| --- |
| The model packaging feature is in preview release for Amazon Lookout for Vision and is subject to change\. | 

You can use the Amazon Lookout for Vision console and AWS SDK to get information about the model packaging jobs that you create\. 

**Topics**
+ [Getting model packaging job information \(Console\)](#package-job-info-console)
+ [Getting model packaging job information \(SDK\)](#package-job-info-console-sdk)

## Getting model packaging job information \(Console\)<a name="package-job-info-console"></a>



**To get model packaging job information \(console\)**

1. Open the Amazon Lookout for Vision console at [ https://console\.aws\.amazon\.com/lookoutvision/]( https://console.aws.amazon.com/lookoutvision/)\.

1. Choose **Get started**\. 

1. In the left navigation pane, choose **Projects**\.

1. In the **Projects** section, choose the project that contains the model packaging job you want to view\.

1. In the left navigation pane, under the project name, choose **Edge model packages**\.

1. In the **Model packaging job** section, choose the model packaging job that you want to view\. The details page for the model packaging job is shown\.

## Getting model packaging job information \(SDK\)<a name="package-job-info-console-sdk"></a>



You can use the AWS SDK to list the model packaging jobs in a project and get information about a specific model packaging job\.

### List model packaging jobs<a name="package-job-list-jobs"></a>

You can list the model packaging jobs in a project by calling the [ListModelPackages](https://docs.aws.amazon.com/lookout-for-vision/latest/APIReference/API_ListModelPackages) API\. The response includes a list of [ModelPackagingJobMetadata](https://docs.aws.amazon.com/lookout-for-vision/latest/APIReference/API_ModelPackagingJobMetadata) objects that provides information about each model packaging job\. Also included is a pagination token that you can use to get the next set of results, if the list is incomplete\.

**To list your model packaging jobs**

1. If you haven't already done so, do the following:

   1. Create or update an IAM user with permissions to access Amazon Lookout for Vision\. For more information, see [Step 3: Set up permissions](su-setup-permissions.md)\. 

   1. Install and configure the AWS CLI and the AWS SDKs\. For more information, see [Step 5: Set up the AWS CLI and AWS SDKs](su-awscli-sdk.md)\.

1. Use the following CLI command\. Change `project_name` to the name of the project that you want to use\.

   ```
   aws lookoutvision list-model-packaging-jobs \
    --project-name project_name
   ```

### Describe a model packaging job<a name="package-job-describe-job"></a>

Use the [DescribeModelPackagingJob](https://docs.aws.amazon.com/lookout-for-vision/latest/APIReference/API_DescribeModelPackagingJob) API to get information about a model packaging job\. The response is a [ModelPackagingDescription](https://docs.aws.amazon.com/lookout-for-vision/latest/APIReference/API_ModelPackagingDescription) object that includes the current status of the job and other information\.

**To describe a package**

1. If you haven't already done so, do the following:

   1. Create or update an IAM user with permissions to access Amazon Lookout for Vision\. For more information, see [Step 3: Set up permissions](su-setup-permissions.md)\. 

   1. Install and configure the AWS CLI and the AWS SDKs\. For more information, see [Step 5: Set up the AWS CLI and AWS SDKs](su-awscli-sdk.md)\.

1. Use the following CLI command\. Change the following:
   + `project_name` to the name of the project that you are using\.
   + `job_name` to the name of the job\. You get the job name \(`JobName`\) when you call [StartModelPackagingJob](https://docs.aws.amazon.com/lookout-for-vision/latest/APIReference/API_StartModelPackagingJob)\.

   ```
   aws lookoutvision describe-model-packaging-job \
       --project-name project_name \
       --job-name job_name
   ```