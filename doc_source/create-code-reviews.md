# Create code reviews in Amazon CodeGuru Reviewer<a name="create-code-reviews"></a>

Amazon CodeGuru Reviewer uses code reviews to provide [different kinds of recommendations](recommendations.md) to help improve your code\. These recommendations are focused on best practices and resolving potential defects in code that are difficult for developers to find\. After a code review is successfully completed on a full repository analysis or incremental code review, you can view recommendations\. You can then choose whether to incorporate the recommendations, and you can provide feedback about whether the recommendations were helpful\.

**Note**  
We recommend that you use both CodeGuru Reviewer and traditional peer review processes during the code review stage\. Using a combination of code review processes helps to identify more issues before they reach production\.

There are two different kinds of code reviews that CodeGuru Reviewer can do to provide recommendations\.
+  *Incremental code reviews* are created automatically when you create an pull request from your repository context on an associated repository\. These code reviews scan the changed code in a pull request\.
+ *Full repository analysis code reviews* scan all the code in a specified branch in the CodeGuru Reviewer console\.
+ *Full repository analysis code reviews for CI/CD workflows* scan all the source code in your CI/CD workflow\. For more information, see [Create code reviews with GitHub Actions](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/working-with-cicd.html)\.

For more information on the difference between incremental code reviews and full repository analysis code reviews, see [About full repository analysis and incremental code reviews](repository-analysis-vs-pull-request.md)\.

**Topics**
+ [Get recommendations using full repository analysis](#get-repository-scan)
+ [Get recommendations using incremental code reviews](#get-pull-request-scan)

## Get recommendations using full repository analysis<a name="get-repository-scan"></a>

To get recommendations on all the code in a branch, associate the repository with CodeGuru Reviewer and do the following:

1. Navigate to the **Code reviews** page in the console\.

1. On the **Full repository analysis** tab, choose **Create full repository analysis**\.

   A window opens for you to specify the location of the source code you wish to scan\.

1. On the **Create full repository analysis** page, choose the associated repository from the list, then choose the branch you want reviewed\.

1. \(Optional\) If you want to, you can provide a name for your code review\. If you don't, CodeGuru Reviewer provides a name for you\.

1. When you have specified the branch you want reviewed, choose **Create full repository analysis**\.

To view the recommendations, navigate to the **Code reviews** page in the console and choose the name of the code review to view the detailed code review page\. If you do not see the code review right away, try refreshing the page\. For more information, see [View code review details](view-code-review-details.md)\.

 If a repository contains Java and Python files, then CodeGuru Reviewer generates recommendations for the language for which there are more files\. For example, if there are five Java files and ten Python files in an associated repository, then recommendations for the Python code are generated and no recommendations for the Java code are generated\. If the number of Java and Python files is the same, then only Java recommendations are generated\. 

## Get recommendations using incremental code reviews<a name="get-pull-request-scan"></a>

To get recommendations from CodeGuru Reviewer after you associate a repository, use the repository source provider to make an incremental code review\. CodeGuru Reviewer then provides recommendations as incremental code review comments in the source provider to improve your code\. 

To view the recommendations in the CodeGuru Reviewer console, navigate to the **Code reviews** page in the console and choose the name of the code review to view the detailed code review page\.