# Create code reviews in Amazon CodeGuru Reviewer<a name="create-code-reviews"></a>

Amazon CodeGuru Reviewer uses code reviews to provide [different kinds of recommendations](recommendations.md) to help improve your code\. These recommendations are focused on best practices and resolving potential defects in code that are difficult for developers to find\. After a code review is successfully completed on a repository analysis or pull request, you can view recommendations\. You can then choose whether to incorporate the recommendations, and you can provide feedback about whether the recommendations were helpful\.

**Note**  
We recommend that you use both CodeGuru Reviewer and traditional peer review processes during the code review stage\. Using a combination of code review processes helps to identify more issues before they reach production\.

There are two different kinds of code reviews that CodeGuru Reviewer can do to provide recommendations\.
+ *Pull request code reviews* are created automatically when you create a pull request from your repository context on an associated repository\. These code reviews scan the changed code in a pull request
+ *Repository analysis code reviews* are done when you create a repository analysis code review in the CodeGuru Reviewer console\. These code reviews scan all the code in a specified branch\.

For more information on the difference between pull request and repository analysis code reviews, see [About repository analysis and pull request code reviews](repository-analysis-vs-pull-request.md)\.

**Topics**
+ [Get recommendations using repository analysis](#get-repository-scan)
+ [Get recommendations using pull requests](#get-pull-request-scan)

## Get recommendations using repository analysis<a name="get-repository-scan"></a>

To get recommendations on all the code in a branch, associate the repository with CodeGuru Reviewer and do the following:

1. Navigate to the **Code reviews** page in the console\.

1. On the **Repository analysis** tab, choose **Create repository analysis**\.

   A window opens for you to specify the location of the source code you wish to scan\.

1. On the **Create repository analysis** page, choose the associated repository from the list, then choose the branch you want reviewed\.

1. \(Optional\) If you want to, you can provide a name for your code review\. If you don't, CodeGuru Reviewer provides a name for you\.

1. When you have specified the branch you want reviewed, choose **Create repository analysis**\.

To view the recommendations, navigate to the **Code reviews** page in the console and choose the name of the code review to view the detailed code review page\. If you do not see the code review right away, try refreshing the page\. For more information, see [View code review details](view-code-review-details.md)\.

## Get recommendations using pull requests<a name="get-pull-request-scan"></a>

To get recommendations from CodeGuru Reviewer after you associate a repository, use the repository source provider to make a pull request\. CodeGuru Reviewer then provides recommendations as pull request comments in the source provider to improve your code\. 

To view the recommendations in the CodeGuru Reviewer console, navigate to the **Code reviews** page in the console and choose the name of the code review to view the detailed code review page\.