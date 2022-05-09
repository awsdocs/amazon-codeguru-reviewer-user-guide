# Add or update tags for a CodeGuru Reviewer associated repository \(AWS CLI\)<a name="how-to-tag-associated-repository-update-cli"></a>

Follow these steps to use the AWS CLI and the tag\-resource command to add or update the AWS tags for an associated repository\. This command adds a new tag or, if you pass in a tag with an existing key, updates the value associated with that key\. If you want to use the AWS CLI to update the key of a tag, use untag\-resource to remove it, then use tag\-resource to add a new tag with the updated key and its value\.

**To add or update tags for an associated repository**

1. Make sure that you have configured the AWS CLI with the AWS Region in which you want to create your code reviews\. To verify the Region, run the following command at the command line or terminal and review the information for the default name\. 

   ```
   aws configure
   ```

   The default Region name must match the AWS Region for the repository in CodeCommit\. 

1. Run the tag\-resource command\. Use `--resource-arn` to specify the Amazon Resource Name \(ARN\) of the associated repository that contains the tags you want to update or add\. Use the `--tags` argument to specify the tags you want to update or add\. The following command specifies 3 tags\. If one of the keys already exists, its value is updated\. If not, a new key is added\.

   ```
   aws codeguru-reviewer tag-resource /
     --resource-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid /
     --tags key1=value1,key2=value2,key3=value3
   ```

1. If successful, there is no output and no error\. If you want to verify the tags were added correctly, use the describe\-repository\-association command and use `--association-arn` to specify the ARN of the associated repository\. 

   ```
   aws codeguru-reviewer describe-repository-association /
     --association-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid
   ```

   The output is a [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html) object that includes an array with the 3 added or updated tags\. 

   ```
   {
       "RepositoryAssociation": {
           "AssociationId": "repository-association-uuid",
           "Name": "my-repository-name",
           "LastUpdatedTimeStamp": 1603493340.035,
           "ProviderType": "CodeCommit",
           "CreatedTimeStamp": 1603493328.512,
           "Owner": "123456789012",
           "State": "Associated",
           "StateReason": ""Pull Request Notification configuration successful",
           "AssociationArn": "arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid"
       },
       "Tags": {
           "key3": "value3",
           "key2": "value2",
           "key1": "value1"        
       }
   }
   ```