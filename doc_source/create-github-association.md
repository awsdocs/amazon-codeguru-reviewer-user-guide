# Create a GitHub or GitHub Enterprise Cloud repository association in Amazon CodeGuru Reviewer<a name="create-github-association"></a>

You can create a GitHub or GitHub Enterprise Cloud repository association using the Amazon CodeGuru Reviewer console\. You cannot create a GitHub or GitHub Enterprise Cloud repository association using the AWS CLI or the CodeGuru Reviewer SDK\. Before you create a GitHub or GitHub Enterprise Cloud repository association, you must have a GitHub or GitHub Enterprise Cloud repository\. 

**Note**  
We recommend creating a new GitHub user \(for example, *MyCodeGuruUser*\) and using that user to provide CodeGuru Reviewer with access to your GitHub repositories\. This ensures that CodeGuru Reviewer posts comments on behalf of a unique user\. This helps avoid confusion and make the account more transferable, so that it doesn't belong to a single person who might not always be available to maintain it\. 

**To create a GitHub repository association**

1. Open the Amazon CodeGuru Reviewer console at [https://console\.aws\.amazon\.com/codeguru/reviewer/home](https://console.aws.amazon.com/codeguru/reviewer/home)\.

1. In the navigation pane, choose **Repositories**\. 

1. Choose **Associate repository**\. 

1. Choose **GitHub**\. 

1. If you are not connected to GitHub, choose **Connect to GitHub** and follow the prompts to connect\. 

1. From **Repository location**, choose your repository\.

1. \(Optional\) Expand **Encryption key \- optional** to use your own AWS Key Management Service key \(KMS key\) to encrypt your associated repository\. For more information, see [Encrypting a repository association in Amazon CodeGuru Reviewer](encrypt-repository-association.md)\.

   1. Select **Customize encryption settings \(advanced\)**\.

   1. Do one of the following: 
      + If you already have a KMS key that you manage, enter its Amazon Resource Name \(ARN\)\. For information about finding the ARN of your key using the console, see [Finding the key ID and ARN](https://docs.aws.amazon.com/kms/latest/developerguide/find-cmk-id-arn.html) in the *AWS Key Management Service Developer Guide*\.
      + If you want to create a new KMS key, choose **Create an AWS KMS key** and follow the steps in the AWS KMS console\. For more information, see [Creating keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.

1. \(Optional\) Expand **Tags** to add one or more tags to your repository association\. For more information, see [Tagging a repository association in Amazon CodeGuru Reviewer](tag-repository-association.md)\.

   1. Choose **Add new tag**\.

   1. In **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. 

   1. \(Optional\) To add another tag, choose **Add tag** again\.

1. Choose **Associate**\. On the **Repositories** page, the **Status** is **Associating**\. When the association is complete, the status changes to **Associated** and you can create a pull request or a repository analysis to get recommendations\. Refresh the page to check for the status change\. 