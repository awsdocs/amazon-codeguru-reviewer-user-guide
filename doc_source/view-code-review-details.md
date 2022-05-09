# View code review details<a name="view-code-review-details"></a>

You can view a summary of code review details or a code review details page in Amazon CodeGuru Reviewer\. This allows you to get information about a code review's status and generated recommendations\.

**Topics**
+ [Information in code review details](#information-in-code-review-details)
+ [View code review details by using the AWS CLI](#view-details-cli)

## Information in code review details<a name="information-in-code-review-details"></a>

You might want to use code review details to get more information about a code review, to provide feedback on recommendations in a code review, or to troubleshoot a **Failed** code review status\. 

There are three possible code review statuses: 
+ **Pending** – CodeGuru Reviewer has received the incremental code review notification or the full repository analysis request and a code review is scheduled\. Make sure you maintain access permissions to your source branch while CodeGuru Reviewer processes the request\. If the code review is for a pull request, keep the pull request open\.
+ **Completed** – CodeGuru Reviewer successfully finished reviewing the source code\.
+ **Failed** – The code review has failed to finish reviewing the source code\. This could be because of a problem with source code access permissions or a transient exception that occurred:
  + If the problem is due to source code access permissions, the easiest way to fix it is to disassociate the repository and then associate the repository again\. If the error persists, contact AWS Support\.
  + If the problem is due to a transient exception, the code review request is retried\.
  + If the problem is due to an analysis configuration file error, then review the errors with the file, fix the file, and initiate an incremental code review or a full repository analysis\. For more information, see [Error handling for the aws\-codeguru\-reviewer\.yml file](recommendation-suppression.md#error-handling-yml)\. 

   When you retry the operation, be sure to keep relevant incremental code reviews open and the source branch available while CodeGuru Reviewer processes the request\. 

You can view code review details by choosing the name of the code review\. 

## View code review details by using the AWS CLI<a name="view-details-cli"></a>

You can also use the AWS CLI or the AWS SDK to view the details of a code review\. 

If you have the code review ARN, you can call [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_DescribeCodeReview.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_DescribeCodeReview.html)\. Alternatively, you can call [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_ListCodeReviews.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_ListCodeReviews.html) and filter using `ProviderType` and `RepositoryName`\. 