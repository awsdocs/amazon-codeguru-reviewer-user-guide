# Working with code reviews<a name="code-reviews"></a>

You can create an incremental code review or a full repository analysis code review\. For more information about the types of code reviews, see [About full repository analysis and incremental code reviews](repository-analysis-vs-pull-request.md)\.

When you create a code review, CodeGuru Reviewer reviews your code and provides recommendations about how to improve the code\. You can see these recommendations directly in the CodeGuru Reviewer console **Code reviews** page\. For incremental code reviews, you can also see these recommendations as comments on a pull request\. 

 If a repository contains Java and Python files, then CodeGuru Reviewer generates recommendations for the language for which there are more files\. For example, if there are five Java files and ten Python files in an associated repository, then CodeGuru Reviewer generates recommendations for the Python code and does not generate recommendations for the Java code\. If the number of Java and Python files is the same, then only Java recommendations are generated\. 

If you want to suppress recommendations from CodeGuru Reviewer, you can create and add to the root directory of your repository an `aws-codeguru-reviewer.yml` file that lists files and directories to exclude from analysis\. For more information, see [Suppress recommendations](recommendation-suppression.md)\. 

You can do the following on the **Code reviews** page in the CodeGuru console: 
+ Create full repository analysis code reviews\.
+ View all code reviews from the past 90 days\.
+ Navigate directly to incremental code reviews and repositories on which the code reviews were performed\.
+ View details about code reviews and whether they are completed\.
+ Check whether CodeGuru Reviewer used your `aws-codeguru-reviewer.yml` file for an analysis and review any error messages about the file\.
+ View all the recommendations of each code review directly in the console\.
+ Provide feedback to indicate which recommendations were helpful and which recommendations were not helpful\.

Your feedback on recommendations is crucial to helping CodeGuru Reviewer improve its recommendations\. You can use the **Code Reviews** page to give feedback on recommendations by choosing the name of the repository and then choosing thumbs\-up or thumbs\-down icons\.

**Topics**
+ [About full repository analysis and incremental code reviews](repository-analysis-vs-pull-request.md)
+ [Suppress recommendations from Amazon CodeGuru Reviewer](recommendation-suppression.md)
+ [Create code reviews in Amazon CodeGuru Reviewer](create-code-reviews.md)
+ [View all code reviews](view-all-code-reviews.md)
+ [View code review details](view-code-review-details.md)
+ [View recommendations and provide feedback](give-feedback-from-code-review-details.md)