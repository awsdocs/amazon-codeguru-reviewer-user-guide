# Connect to GitHub to associate a repository with CodeGuru Reviewer<a name="github-steps"></a>

You can connect to GitHub directly through the CodeGuru Reviewer console\. This enables you to associate repositories in a GitHub account with CodeGuru Reviewer to receive [recommendations](recommendations.md) for improvements in your Java code\.

**Note**  
GitHub Enterprise Cloud repositories are associated using this procedure, but GitHub Enterprise Server has a different procedure\.

## Connect to GitHub<a name="create-new-github-connection"></a>

Connect to your GitHub account to associate GitHub repositories with CodeGuru Reviewer\. When you're connected, you stay connected until you log out of your GitHub account or until you choose **Disconnect from GitHub** in the CodeGuru Reviewer console\.

1. On the CodeGuru console **Associate repository** page, choose **GitHub** as the source provider\. Then choose **Connect to GitHub**\.  
![\[Choose a source provider on the Associate repository page\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. If you're not currently logged in to your GitHub account, a window opens prompting you for your GitHub credentials\. Provide your information and choose **Sign in** to log in to GitHub\.   
![\[Log in to GitHub\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. After you are logged in to GitHub, a window opens for you to allow CodeGuru Reviewer to access your GitHub account\. If you're using GitHub Enterprise Cloud, choose **Grant** to allow access to an organization\. Choose **Authorize aws\-codesuite** to enable CodeGuru Reviewer to provide recommendations on your code\.  
![\[Grant access to your GitHub account for CodeGuru Reviewer\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. Return to the [Associate repository page](https://console.aws.amazon.com/codeguru/reviewer/#/configure) in the CodeGuru Reviewer console and verify that your account is connected\.   
![\[The GitHub account is connected to CodeGuru Reviewer\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

After you connect to GitHub, proceed to [Step 3: Finish associating a repository](step-one.md#finish-associating-repository)\. 