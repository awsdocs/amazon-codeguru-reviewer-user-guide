# Step 3: Get recommendations<a name="get-results"></a>

 CodeGuru Reviewer uses code reviews to provide [different kinds of recommendations](recommendations.md) to help improve your code\. These recommendations are focused on best practices and resolving potential defects in code that are difficult for developers to find\. After CodeGuru Reviewer completes an incremental code review or a full repository analysis code review, you can view recommendations\. You can then choose whether to incorporate the recommendations, and you can provide feedback about whether the recommendations were helpful\.

**Note**  
We recommend that you use both CodeGuru Reviewer and traditional peer review processes during the code review stage\. Using a combination of code review processes helps to identify more issues before they reach production\.

 For more information, see the following topics: 
+ [View code review details](view-code-review-details.md)
+ [Get recommendations using full repository analysis](create-code-reviews.md#get-repository-scan) 
+ [Get recommendations using incremental code reviews](create-code-reviews.md#get-pull-request-scan)
+ [Get recommendations using GitHub Actions and a CI/CD workflow](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/working-with-cicd.html)

## About full repository analysis and incremental code reviews<a name="repository-analysis-vs-pull-request-getting-started"></a>

You can receive recommendations in code reviews by creating a full repository analysis or submitting a pull request\. After you associate a repository, CodeGuru Reviewer automatically creates a full repository analysis code review, and every pull request in that repository creates an incremental code review\. You can also choose to create subsequent full repository analysis code reviews\.


| Type of code review | Is the review automatic after I associate the repository? | Where can I see recommendations? | What code is reviewed? | 
| --- | --- | --- | --- | 
|  Full repository analysis  |  Your first full repository analysis is done automatically when you associate your repository\. After that, you must request a full repository analysis in the CodeGuru Reviewer console or by using the AWS CLI or AWS SDK\.  |  In the CodeGuru Reviewer console, or by using the AWS CLI or AWS SDK\.   |  All the code in the branch is reviewed\.  | 
|  Incremental code review  |  Yes\. After associating the repository, every time you do a pull request there is a code review\.  |  In the CodeGuru Reviewer console, in the AWS CLI or AWS SDK, or in pull request comments in the repository source provider\.  |  The code that is changed in the pull request is reviewed\.  | 
|  GitHub Actions code review in a CI/CD workflow  |  Yes\. After enabling CodeGuru Reviewer on your GitHub repository, for every push, pull, or scheduled repository scan there is a code review\.  |  In the GitHub **Security** tab\.  |  The code that is changed in the push, pull, or scheduled repository scan\.  | 