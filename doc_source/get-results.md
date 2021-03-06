# Step 3: Get recommendations<a name="get-results"></a>

Amazon CodeGuru Reviewer uses code reviews to provide [different kinds of recommendations](recommendations.md) to help improve your code\. These recommendations are focused on best practices and resolving potential defects in code that are difficult for developers to find\. After a code review is successfully completed on a repository analysis or pull request, you can view recommendations\. You can then choose whether to incorporate the recommendations, and you can provide feedback about whether the recommendations were helpful\.

**Note**  
We recommend that you use both CodeGuru Reviewer and traditional peer review processes during the code review stage\. Using a combination of code review processes helps to identify more issues before they reach production\.

 For more information, see: 
+ [View code review details](view-code-review-details.md)
+ [Get recommendations using repository analysis](create-code-reviews.md#get-repository-scan) 
+ [Get recommendations using pull requests](create-code-reviews.md#get-pull-request-scan)

## About repository analysis and pull request scans<a name="repository-analysis-vs-pull-request-getting-started"></a>

You can get recommendations in code reviews by using a repository analysis or a pull request\. After you associate a repository, you can choose when to have an entire branch get a code review, and every pull request in that repository receives a code review\.


| Type of code review | Is the review automatic after I associate the repository? | Where can I see recommendations? | What code is reviewed? | 
| --- | --- | --- | --- | 
|  Repository analysis  |  No\. You must request a repository analysis in the CodeGuru Reviewer console or by using the AWS CLI or AWS SDK\.  |  In the CodeGuru Reviewer console, or by using the AWS CLI or AWS SDK\.   |  All the code in the branch is reviewed\.  | 
|  Pull request  |  Yes\. After associating the repository, every time you do a pull request there is a code review\.  |  In the CodeGuru Reviewer console, in the AWS CLI or AWS SDK, or in pull request comments in the repository source provider\.  |  The code that is changed in the pull request is reviewed\.  | 