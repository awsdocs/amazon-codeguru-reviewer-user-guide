# Working with repository associations in Amazon CodeGuru Reviewer<a name="working-with-repositories"></a>

Amazon CodeGuru Reviewer requires a repository that contains the source code you want it to review\. To add a repository with your source code to CodeGuru Reviewer, you create a *repository association*\. 



Immediately after you create the repository association, its status is **Associating**\. A repository association with this status is doing the following\. 
+ Setting up pull request notifications\. This is required for pull requests to initiate a CodeGuru Reviewer review\. For GitHub, GitHub Enterprise Server, and Bitbucket repositories, the notifications are webhooks created in your repository to initiate CodeGuru Reviewer reviews\. If you delete these webhooks, reviews of code in your repository cannot be initiated\. 
+ Setting up source code access\. This is required for CodeGuru Reviewer to securely clone the code in your repository\. 

When the pull request notifications, source code access, and creation of required permissions are complete, the status changes to **Associated**\. The association is now complete and CodeGuru Reviewer performs its first full scan of the repository\. You can later create incremental code reviews or full repository analysis code reviews to get recommendations\. For more information, see [About full repository analysis and incremental code reviews](repository-analysis-vs-pull-request.md)\.

 CodeGuru Reviewer supports associations with repositories from the following source providers: 
+  AWS CodeCommit 
+  Bitbucket 
+  GitHub and GitHub Enterprise Cloud \(These are listed together because you work with them identically using CodeGuru Reviewer\.\) 
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