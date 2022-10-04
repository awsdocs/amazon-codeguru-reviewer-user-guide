# Disassociate a repository in CodeGuru Reviewer<a name="disassociate-repository-association"></a>

 You can disassociate any associated repository you create\. After you disassociate a repository, Amazon CodeGuru Reviewer no longer has permission to read code in the repository's pull requests and doesn't have access to your repository's source code\. This means that CodeGuru Reviewer does not have permission to perform operations such as cloning or publishing comments in source code\. A disassociated repository does not send pull request notifications to Amazon CodeGuru Reviewer\. You cannot create code reviews of any kind for a disassociated repository\.

 Immediately after you choose to disassociate a repository, its status changes to `Disassociating`\. If you want to review code in your disassociated repository later, you can create a new repository association\. 

**Note**  
Charges are not incurred for disassociated repositories\.

**Topics**
+ [Disassociate a repository in CodeGuru Reviewer \(console\)](#disassociate-repository-association-console)
+ [Disassociate a repository in CodeGuru Reviewer \(AWS CLI\)](#disassociate-repository-association-cli)

## Disassociate a repository in CodeGuru Reviewer \(console\)<a name="disassociate-repository-association-console"></a>

**To disassociate a repository**

1. Open the Amazon CodeGuru Reviewer console at [https://console\.aws\.amazon\.com/codeguru/reviewer/home](https://console.aws.amazon.com/codeguru/reviewer/home)\.

1. In the navigation pane, choose **Repositories**\. 

1. Do one of the following:
   + Choose the radio button next to the repository you want to disassociate, then choose **Disassociate repository**\. 
   + Choose the association ID of the repository you want to disassociate\. On its **Repository** page, choose **Disassociate repository**\. With this option, you can view details about your repository before you disassociate it\. 

## Disassociate a repository in CodeGuru Reviewer \(AWS CLI\)<a name="disassociate-repository-association-cli"></a>

For information about using the AWS CLI with CodeGuru Reviewer, see the [CodeGuru Reviewer section of the AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/codeguru-reviewer/index.html) 

**Disassociate a repository association**

1. Make sure that you have configured the AWS CLI with the AWS Region in which you want to create your code reviews\. To verify the Region, run the following command at the command line or terminal and review the information for the default name\. 

   ```
   aws configure
   ```

   The default Region name must match the AWS Region for the repository in CodeCommit\. 

1. Run the disassociate\-repository command specifying the Amazon Resource Name \(ARN\) of your associated repository\. 

   ```
   aws codeguru-reviewer disassociate-repository --association-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid
   ```

1. If successful, this command outputs a [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html) object with a state of `Disassociating`\. 

   ```
   {
       "RepositoryAssociation": {
           "AssociationId": "repository_association_uuid",
           "Name": "repository-name",
           "LastUpdatedTimeStamp": 1602119553.692,
           "ProviderType": "CodeCommit",
           "CreatedTimeStamp": 1590712779.949,
           "Owner": "123456789012",
           "State": "Disassociating",
           "AssociationArn": ""arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid"
       }
   }
   ```

1. When the disassociate\-repository command completes, the repository is not associated with Amazon CodeGuru Reviewer\. You can check if your repository association successfully disassociated using the `describe-repository` command with its Amazon Resource Name \(ARN\)\. 

   ```
   aws codeguru-reviewer describe-repository-association --association-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid
   ```

1. If successful, the repository association is deleted and the command correctly outputs the following: 

   ```
   An error occurred (NotFoundException) when calling the DescribeRepositoryAssociation operation: The requested resource arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid is not found.
   ```