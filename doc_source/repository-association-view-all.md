# View all repository associations in CodeGuru Reviewer<a name="repository-association-view-all"></a>

 You can view all the associated repositories in your AWS Region and your AWS account using the console or the AWS CLI\. 

**Topics**
+ [View all associated repositories in CodeGuru Reviewer \(console\)](#repository-association-view-all-console)
+ [View all repository associations in CodeGuru Reviewer \(AWS CLI\)](#repository-association-view-all-cli)

## View all associated repositories in CodeGuru Reviewer \(console\)<a name="repository-association-view-all-console"></a>

**View all associated repositories**

1. Open the Amazon CodeGuru Reviewer console at [https://console\.aws\.amazon\.com/codeguru/reviewer/home](https://console.aws.amazon.com/codeguru/reviewer/home)\.

1. In the navigation pane, choose **Associated repositories**\. 

## View all repository associations in CodeGuru Reviewer \(AWS CLI\)<a name="repository-association-view-all-cli"></a>

 For information about using the AWS CLI with CodeGuru Reviewer, see the [CodeGuru Reviewer section](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/codeguru-reviewer/index.html) and [list\-repository\-associations](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/codeguru-reviewer/list-repository-associations.html) in the *AWS CLI Command Reference*\. 

**View all repository associations**

1. Make sure that you have configured the AWS CLI with the AWS Region that contains the repository associations you want to view\. Run the following command at the command line or terminal and review or configure the Region for the AWS CLI\. 

   ```
   aws configure
   ```

1. Run list\-repository\-associations\. 

   ```
   aws codeguru-reviewer list-repository-associations
   ```

1. If successful, this command outputs one [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociationSummary.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociationSummary.html) object for each of your associated repositories\. 

   ```
   {
       "RepositoryAssociationSummaries": [
           {
               "LastUpdatedTimeStamp": 1595886609.616,
               "Name": "test",
               "AssociationId": "0bdac454-f6af-4adf-a625-de4db4b4bca1",
               "Owner": "123456789012",
               "State": "Associated",
               "AssociationArn": "arn:aws:codeguru-reviewer:us-west-2:123456789012:association:0bdac454-f6af-4adf-a625-de4db4b4bca1",
               "ProviderType": "Bitbucket"
           },
           {
               "LastUpdatedTimeStamp": 1595636969.035,
               "Name": "CodeDeploy-CodePipeline-ECS-Tutorial",
               "AssociationId": "eb2f7513-a132-47ad-81dc-bd718468ee1e",
               "Owner": "123456789012",
               "State": "Associated",
               "AssociationArn": "arn:aws:codeguru-reviewer:us-west-2:123456789012:association:eb2f7513-a132-47ad-81dc-bd718468ee1e",
               "ProviderType": "CodeCommit"
           },
           {
               "LastUpdatedTimeStamp": 1595634785.983,
               "Name": "My-ecs-beta-repo",
               "AssociationId": "d79156d7-6297-4b08-ba5a-f05b274e3518",
               "Owner": "123456789012",
               "State": "Associated",
               "AssociationArn": "arn:aws:codeguru-reviewer:us-west-2:123456789012:association:d79156d7-6297-4b08-ba5a-f05b274e3518",
               "ProviderType": "CodeCommit"
           }
       ]
   }
   ```