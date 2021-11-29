# Step 2: Associate a repository<a name="getting-started-associate-repository"></a>

 You must create a repository association to grant CodeGuru Reviewer access to read your source code and create notifications on your repository\. The notifications trigger analysis on updated source code every time you create a pull request\. When you create your repository association, CodeGuru Reviewer performs its first full repository analysis for you\. You must initiate subsequent full repository analysis code reviews\. For more information, see [Working with repository associations in Amazon CodeGuru Reviewer](working-with-repositories.md)\.

**Note**  
The source code reviewed by CodeGuru Reviewer is not stored\. For more information, see [Captured data in CodeGuru Reviewer](data-protection.md#data-captured)\.

 To create a repository association, choose one of the following\. 
+  If your repository type is AWS CodeCommit, see [ Create a CodeCommit repository association](create-codecommit-association.md)\. 
+  If your repository type is Bitbucket, see [ Create a Bitbucket repository association](create-bitbucket-association.md)\. 
+  If your repository type is GitHub or GitHub Enterprise Cloud, see [ Create a GitHub or GitHub Enterprise Cloud repository association](create-github-association.md)\. 
+  If your repository type is GitHub Enterprise Server, see [ Create a GitHub Enterprise Server repository association](create-github-enterprise-association.md)\. 