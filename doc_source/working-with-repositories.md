# Working with repository associations in Amazon CodeGuru Reviewer<a name="working-with-repositories"></a>

Amazon CodeGuru Reviewer requires a repository that contains the source code you want it to review\. To add a repository with your source code to CodeGuru Reviewer, you create a *repository association*\. When you associate a repository, you can enable a code review\.

There are two different kinds of code reviews that CodeGuru Reviewer can do to provide recommendations\.
+ *Pull request code reviews* are created automatically when you create a pull request from your repository context on an associated repository\. These code reviews scan the changed code in a pull request
+ *Repository analysis code reviews* are done when you create a repository analysis code review in the CodeGuru Reviewer console\. These code reviews scan all the code in a specified branch\.

For more information, see [About full repository analysis and incremental code reviews](repository-analysis-vs-pull-request.md)\.

 If a repository contains Java and Python files, then CodeGuru Reviewer generates recommendations for the language for which there are more files\. For example, if there are five Java files and ten Python files in an associated repository, then recommendations for the Python code are generated and no recommendations for the Java code are generated\. If the number of Java and Python files is the same, then only Java recommendations are generated\. 

 Immediately after you create the repository association, its status is **Associating**\. A repository association with this status is doing the following\. 
+ Setting up pull request notifications\. This is required for pull requests to trigger a CodeGuru Reviewer review\. For GitHub, GitHub Enterprise Server, and Bitbucket repositories, the notifications are webhooks created in your repository to trigger CodeGuru Reviewer reviews\. If you delete these webhooks, reviews of code in your repository cannot be triggered\. 
+ Setting up source code access\. This is required for CodeGuru Reviewer to securely clone the code in your repository\. 

When the pull request notifications, source code access, and creation of required permissions are complete, the status changes to **Associated**\. After its status changes to **Associated**, the association is complete and you can create a pull request or a repository analysis to get recommendations\. 

 CodeGuru Reviewer supports associations with repositories from the following source providers: 
+  AWS CodeCommit 
+  Bitbucket 
+  GitHub 
+  GitHub Enterprise Cloud 
+  GitHub Enterprise Server 

**Note**  
 The source code reviewed by CodeGuru Reviewer is not stored\. For more information, see [Captured data in CodeGuru Reviewer](data-protection.md#data-captured)\. 

**Topics**
+ [Create an AWS CodeCommit repository association in Amazon CodeGuru Reviewer](create-codecommit-association.md)
+ [Create a Bitbucket repository association in Amazon CodeGuru Reviewer](create-bitbucket-association.md)
+ [Create a GitHub or GitHub Enterprise Cloud repository association in Amazon CodeGuru Reviewer](create-github-association.md)
+ [Create a GitHub Enterprise Server repository association in Amazon CodeGuru Reviewer](create-github-enterprise-association.md)
+ [View all repository associations in CodeGuru Reviewer](repository-association-view-all.md)
+ [Disassociate a repository in CodeGuru Reviewer](disassociate-repository-association.md)
+ [Encrypting a repository association in Amazon CodeGuru Reviewer](encrypt-repository-association.md)
+ [Tagging a repository association in Amazon CodeGuru Reviewer](tag-repository-association.md)