# Create an AWS CodeCommit repository association in Amazon CodeGuru Reviewer<a name="create-codecommit-association"></a>

You can create an AWS CodeCommit repository association using the Amazon CodeGuru Reviewer console, the AWS CodeCommit console, the AWS CLI, or the CodeGuru Reviewer SDK\. Before you create a CodeCommit repository association, you must have a CodeCommit repository in the same AWS account and Region in which you want your CodeGuru Reviewer code reviews\. For more information, see [Create an AWS CodeCommit repository](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-create-repository.html) in the *AWS CodeCommit User Guide*\. 

**Topics**
+ [Create a CodeCommit repository association \(CodeGuru Reviewer console\)](#create-codecommit-association-console)
+ [Create a CodeCommit repository association \(CodeCommit console\)](#create-codecommit-association-other-console)
+ [Create a CodeCommit repository association \(AWS CLI\)](#create-codecommit-association-cli)
+ [Create a CodeCommit repository association \(AWS SDKs\)](#create-codecommit-association-sdk)

## Create a CodeCommit repository association \(CodeGuru Reviewer console\)<a name="create-codecommit-association-console"></a>

**To create a CodeCommit repository association**

1. Open the Amazon CodeGuru Reviewer console at [https://console\.aws\.amazon\.com/codeguru/reviewer/home](https://console.aws.amazon.com/codeguru/reviewer/home)\.

1. In the navigation pane, choose **Repositories**\. 

1. Choose **Associate repository and run analysis**\. 

1. Choose **AWS CodeCommit**\. 

1. From **Repository location**, choose the name of your CodeCommit repository that contains the source code you want CodeGuru Reviewer to analyze\. 

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

## Create a CodeCommit repository association \(CodeCommit console\)<a name="create-codecommit-association-other-console"></a>

You can [connect to CodeGuru Reviewer directly from the CodeCommit console\.](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-amazon-codeguru-reviewer.html#how-to-amazon-codeguru-reviewer-associate) This allows you to create a CodeCommit repository association with CodeGuru Reviewer without leaving your CodeCommit repository context\. 

## Create a CodeCommit repository association \(AWS CLI\)<a name="create-codecommit-association-cli"></a>

 For information about using the AWS CLI with CodeGuru Reviewer, see the [CodeGuru Reviewer section of the AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/codeguru-reviewer/index.html)\. 

**To create a CodeCommit repository association**

1. Make sure that you have configured the AWS CLI with the AWS Region in which you want to create your code reviews and in which your CodeCommit repository exists\. To verify the Region, run the following command at the command line or terminal and review the information for the default name\. 

   ```
   aws configure
   ```

   The default Region name must match the AWS Region for the repository in CodeCommit\. 

1. Run the associate\-repository command specifying the name of the CodeCommit repository you want to associate\. 

   ```
   aws codeguru-reviewer associate-repository --repository CodeCommit={Name=my-codecommit-repo}
   ```

1. If successful, this command outputs a [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html) object\. 

   ```
   {
       "RepositoryAssociation": {
           "AssociationId": "repository-association-uuid",
           "Name": "my-codecommit-repo",
           "LastUpdatedTimeStamp": 1595634764.029,
           "ProviderType": "CodeCommit",
           "CreatedTimeStamp": 1595634764.029,
           "Owner": "123456789012",
           "State": "Associating",
           "StateReason": "Pending Repository Association",
           "AssociationArn": "arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid",
       }
   }
   ```

1. When the associate\-repository command succeeds, the status in the returned output is **Associating**\. When the association is complete, the status changes to **Associated** and you can create a pull request or a full repository analysis to get recommendations\. You can check your repository association's status using the `describe-repository` command with its Amazon Resource Name \(ARN\)\. 

   ```
   aws codeguru-reviewer describe-repository-association --association-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid
   ```

1. If successful, this command outputs a [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html) object which shows its status\. 

   ```
   {
       "RepositoryAssociation": {
           "AssociationId": "repository-association-uuid",
           "Name": "my-codecommit-repo",
           "LastUpdatedTimeStamp": 1595634764.029,
           "ProviderType": "CodeCommit",
           "CreatedTimeStamp": 1595634764.029,
           "Owner": "123456789012",
           "State": "Associated",
           "StateReason": ""Pull Request Notification configuration successful",
           "AssociationArn": "arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid"
       }
   }
   ```

## Create a CodeCommit repository association \(AWS SDKs\)<a name="create-codecommit-association-sdk"></a>

To create a CodeCommit repository association with the AWS SDKs, use the `AssociateRepository` API\. For more information, see [AssociateRepository](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_AssociateRepository.html) in the *Amazon CodeGuru Reviewer API Reference*\. 