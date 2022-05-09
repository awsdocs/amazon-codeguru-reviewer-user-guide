# Create a GitHub or GitHub Enterprise Cloud repository association in Amazon CodeGuru Reviewer<a name="create-github-association"></a>

You can create a GitHub or GitHub Enterprise Cloud repository association using the Amazon CodeGuru Reviewer console\. You cannot create a GitHub or GitHub Enterprise Cloud repository association using the AWS CLI or the CodeGuru Reviewer SDK\. Before you create a GitHub or GitHub Enterprise Cloud repository association, you must have a GitHub or GitHub Enterprise Cloud repository\. 

**Note**  
We recommend creating a new GitHub user \(for example, *MyCodeGuruUser*\) and using that user to provide CodeGuru Reviewer with access to your GitHub repositories\. This ensures that CodeGuru Reviewer posts comments on behalf of a unique user\. This helps avoid confusion and make the account more transferable, so that it doesn't belong to a single person who might not always be available to maintain it\. 

**To create a GitHub repository association**

1. Open the Amazon CodeGuru Reviewer console at [https://console\.aws\.amazon\.com/codeguru/reviewer/home](https://console.aws.amazon.com/codeguru/reviewer/home)\.

1. In the navigation pane, choose **Repositories**\. 

1. Choose **Associate repository and run analysis**\. 

1. Choose **GitHub or GitHub Enterprise Cloud**\. 

1. If you are not connected to GitHub, choose **Connect to GitHub or GitHub Enterprise Cloud** and follow the prompts to connect\. 

1. From **Repository location**, choose the name of your GitHub repository that contains the source code you want CodeGuru Reviewer to analyze\.

1. \(Optional\) Expand **Encryption key \- optional** to use your own AWS Key Management Service key \(KMS key\) to encrypt your associated repository\. For more information, see [Encrypting a repository association in Amazon CodeGuru Reviewer](encrypt-repository-association.md)\.

   1. Select **Customize encryption settings \(advanced\)**\.

   1. Do one of the following: 
      + If you already have a KMS key that you manage, enter its Amazon Resource Name \(ARN\)\. For information about finding the ARN of your key using the console, see [Finding the key ID and ARN](https://docs.aws.amazon.com/kms/latest/developerguide/find-cmk-id-arn.html) in the *AWS Key Management Service Developer Guide*\.
      + If you want to create a KMS key, choose **Create an AWS KMS key** and follow the steps in the AWS KMS console\. For more information, see [Creating keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.

1. In **Run a repository analysis**, specify information for your associated repository's first full scan\. This scan generates your repository's initial code review\. For more information, see [Get recommendations using full repository analysis](create-code-reviews.md#get-repository-scan)\.

   1. From **Source branch**, choose the branch to use\.

   1. \(Optional\) In **Code review name**, type a name for your code review\.

   1. \(Optional\) Expand **Analysis configuration file \- optional** to download a sample `aws-codeguru-reviewer.yml` file to use as a template\. Modify the file and upload it to the root directory of your repository\. For more information about the analysis configuration file, see [Suppress recommendations](recommendation-suppression.md)\.  
![\[The Run a repository analysis section with settings and sample YAML file information.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/run-repo-analysis-config-file.png)

1. \(Optional\) Expand **Tags** to add one or more tags to your repository association\. For more information, see [Tagging a repository association in Amazon CodeGuru Reviewer](tag-repository-association.md)\.

   1. Choose **Add new tag**\.

   1. In **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. 

   1. \(Optional\) To add another tag, choose **Add new tag**\.

1. Choose **Associate repository and run analysis**\. On the **Repositories** page, the **Status** is **Associating**\. When the association is complete, the status changes to **Associated** and a full repository analysis begins\. Refresh the page to check for the status change\. 