# Associate a repository<a name="step-one"></a>

 Associating a repository enables CodeGuru Reviewer to provide recommendations on pull requests\. When you associate a repository, you enable CodeGuru Reviewer to read the code in a pull request at the time of the request\. You also enable CodeGuru Reviewer to listen to pull request notifications so that a code review is created for every pull request\.

**Note**  
The source code reviewed by CodeGuru Reviewer is not stored\. For more information, see [Captured data in CodeGuru Reviewer](data-protection.md#data-captured)\.

**Topics**
+ [Step 1: Navigate to the Associate repositories page in the console](#navigate-to-associate-repositories-page)
+ [Step 2: Connect to a repository source provider](#select-repository-source-provider)
+ [Step 3: Finish associating a repository](#finish-associating-repository)
+ [Associate a CodeCommit repository and view associated repositories using the AWS CLI](#associate-repository-using-cli)
+ [Connect to Bitbucket to associate a repository with CodeGuru Reviewer](bitbucket-steps.md)
+ [Connect to GitHub to associate a repository with CodeGuru Reviewer](github-steps.md)
+ [Connect to GitHub Enterprise Server to associate a repository with CodeGuru Reviewer](github-enterprise-steps.md)

## Step 1: Navigate to the Associate repositories page in the console<a name="navigate-to-associate-repositories-page"></a>

To begin using CodeGuru Reviewer, you sign in to the CodeGuru [console](https://console.aws.amazon.com/codeguru) and then choose **Associate repositories** under **CodeGuru Reviewer**\. There you can connect to a source provider and associate your repositories\.  

## Step 2: Connect to a repository source provider<a name="select-repository-source-provider"></a>

### Prepare to associate a CodeCommit repository<a name="associate-codecommit-repository"></a>

If you choose CodeCommit, the repositories in your CodeCommit account are detected automatically, and the [`AmazonCodeGuruReviewerServiceRolePolicy`](auth-and-access-control-iam-identity-based-access-control.md#managed-policy-for-codecommit-and-codestar-connections) managed policy is added to your AWS account\. This enables CodeGuru Reviewer to comment on pull requests in your account\. 

If you have an AWS CodeCommit repository, you can also [connect to CodeGuru Reviewer directly from the CodeCommit console\.](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-amazon-codeguru-reviewer.html) 

### Prepare to associate a GitHub repository<a name="associate-github-repository"></a>

If you choose GitHub, you're asked to log in with your GitHub credentials, if you're not already logged in\. A pop\-up window opens, and you're prompted to authorize CodeGuru Reviewer with GitHub\. 

After you authorize the connection, your repositories on GitHub are detected and you can choose to associate one with CodeGuru Reviewer\. For a detailed procedure, follow the steps in [Connect to GitHub to associate a repository with CodeGuru Reviewer](github-steps.md)\. These steps also work for GitHub Enterprise Cloud\.

**Note**  
If you're using GitHub, we recommend creating a new GitHub user, for example, *MyCodeGuruUser*, and using that user to provide CodeGuru Reviewer with access to your GitHub repositories\. This ensures that the comments that CodeGuru Reviewer posts are posted on behalf of a unique user\. This will help avoid confusion and make the account more transferable, so that it doesn't belong to a single person who might not always be available to maintain it\. 

### Prepare to associate a GitHub Enterprise Server repository<a name="associate-github-enterprise-repository"></a>

If you choose GitHub Enterprise Server, you must create a host and a GitHub Enterprise Server connection\. You're asked to log in with your GitHub credentials, and are prompted to authorize CodeGuru Reviewer with GitHub Enterprise Server through an AWS CodeStar connection\. After you authorize the connection, your repositories on GitHub Enterprise Server are detected and you can choose to associate one with CodeGuru Reviewer\. For more information, see [Create a host](https://docs.aws.amazon.com/dtconsole/latest/userguide/connections-host-create.html) and [Create a connection](https://docs.aws.amazon.com/dtconsole/latest/userguide/connections-create.html)\. 

**Note**  
If you're using GitHub Enterprise Cloud, [follow this procedure instead](github-steps.md)\. 

### Prepare to associate a Bitbucket repository<a name="associate-bitbucket-repository"></a>

If you choose Bitbucket Cloud, you must create a Bitbucket Cloud connection\. For a detailed procedure, follow the steps in [Connect to Bitbucket to associate a repository with CodeGuru Reviewer](bitbucket-steps.md)\. You're asked to log in with your Bitbucket Cloud credentials and are prompted to authorize CodeGuru Reviewer with Bitbucket Cloud through an AWS CodeStar connection\. After you authorize the connection, your repositories on Bitbucket Cloud are detected and you can choose to associate one with CodeGuru Reviewer\.

## Step 3: Finish associating a repository<a name="finish-associating-repository"></a>

On the **Associate repository** page in the console, in the **Repository location** list, select the repository you want CodeGuru Reviewer to provide feedback on\. Then choose **Associate**\. This adds the repository to your list of CodeGuru Reviewer repositories\. The selected repository appears on the CodeGuru Reviewer **Associated repositories** page with the status **Associating**\. 

After a few minutes, the repository should finish connecting and the status should change to **Associated**\. If the status changes to **Failed** due to missing permissions or another problem, you can view the reason by going to the **Action** list in the upper right of the CodeGuru Reviewer **Associated repositories** page, and choosing **View repository details**\. You can then choose to disassociate the repository and attempt to associate the repository again\. To disassociate the repository, select it, and then choose **Disassociate repository** in the **Action** list\.

After you associate the repository with CodeGuru Reviewer, CodeGuru Reviewer provides recommendations as comments on all pull requests generated for the connected repository\. In CodeCommit you can view the recommendations on the **Activity** or **Changes** tab\. This continues to happen until the repository is disassociated\.

## Associate a CodeCommit repository and view associated repositories using the AWS CLI<a name="associate-repository-using-cli"></a>

To associate a CodeCommit repository using the AWS CLI, call `AssociateRepository` using a `Repository` object\. After you associate repositories, you can call `DisassociateRepository` to disassociate a repository\. You can also call `DescribeRepositoryAssociation` to find out information about an association, such as its state, and `ListRepositoryAssociations` to see summaries of repository associations\. For more information, see the [CodeGuru Reviewer API Reference](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/Welcome.html)\.