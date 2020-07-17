# View code review details<a name="view-code-review-details"></a>

You can view a summary of code review details or a code review details page to get information about a code review's status and generated recommendations\.

**Topics**
+ [Information in code review details](#information-in-code-review-details)
+ [View a summary of code review details](#view-details-summary)
+ [View the Code review details page](#view-details-page)
+ [View code review details by using the AWS CLI](#view-details-cli)

## Information in code review details<a name="information-in-code-review-details"></a>

You might want to use code review details to get more information about a code review, to provide feedback on recommendations in a code review, or to troubleshoot a **Failed** code review status\. 

There are three possible code review statuses: 
+ **Pending** – CodeGuru Reviewer has received the pull request notification and a code review is scheduled\. Keep the pull request open and the source branch available while CodeGuru Reviewer processes the request\.
+ **Completed** – CodeGuru Reviewer successfully finished reviewing the pull request source code\.
+ **Failed** – The code review has failed to finish reviewing the pull request source code\. This could be because of a problem with source code access permissions or a transient exception that occurred\. Two kinds of failure messages can be listed in the status details:
  + **“CodeGuru Reviewer failed with a transient exception while reviewing the pull request source code\. Your request will be retried\."** 

    This is due to a transient exception, and the code review request will be retried\.
  + **“CodeGuru Reviewer was unable to retrieve information necessary to process your request\. This usually indicates a problem with source code access permissions\. If the error persists, contact AWS Support\.”** 

    This is due to source code access permissions, and the easiest way to fix this is to disassociate the repository and then associate the repository again\.

   When you retry the operation, be sure to keep the pull request open and the source branch available while CodeGuru Reviewer processes the request\. 

You can view code review details by choosing the name of the code review\. Or select a code review, and then choose **Action**, **View code review details**\. 

![\[Navigating to the Code review details window in the CodeGuru Reviewer console\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

## View a summary of code review details<a name="view-details-summary"></a>

If you select the code review and then choose **Action**, **View code review details**, the Code review details window opens, showing the name of the repository, the repository source provider, the status, and details about the status\.

![\[The Code review details window in the CodeGuru Reviewer console\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

## View the Code review details page<a name="view-details-page"></a>

If you choose the name of the code review from the **Code reviews** page, a detailed code review page opens\. 

This page contains a **Details** section, where you can view the status, details about the status, the Amazon Resource Name \(ARN\), number of recommendations, number of lines of code, and more\. 

Below that section is a **Recommendations** section that lists each recommendation with the file and line number it addresses\. This is also a place where you can provide feedback by choosing a thumbs\-up or thumbs\-down icon\.

![\[The Code review details page in the CodeGuru Reviewer console\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

## View code review details by using the AWS CLI<a name="view-details-cli"></a>

You can also use the AWS CLI or the AWS SDK to view the details of a code review\. 

If you have the code review ARN, you can call `DescribeCodeReview`\. Alternatively, you can call `ListCodeReviews` and filter using `ProviderType` and `RepositoryName`\. 