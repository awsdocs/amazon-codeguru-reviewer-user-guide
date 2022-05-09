# Remove tags from a CodeGuru Reviewer associated repository \(AWS CLI\)<a name="how-to-tag-associated-repository-remove-cli"></a>

You can remove a tag from an associated repository using the console or the AWS CLI\.

**Important**  
Removing a tag from an associated repository can impact access to that associated repository\. Before you remove a tag from an associated repository, make sure to review any IAM policies that might use its key or value to control access to resources such as associated repositories\. For examples of tag\-based access policies, see [Using tags to control access to Amazon CodeGuru Reviewer associated repositories](auth-and-access-control-using-tags.md)\.

**To remove tags from an associated repository**

1. Make sure that you have configured the AWS CLI with the AWS Region in which you want to create your code reviews\. To verify the Region, run the following command at the command line or terminal and review the information for the default name\. 

   ```
   aws configure
   ```

    The default Region name must match the AWS Region for the repository in CodeCommit\. 

1. Run the untag\-resource command\. Use `--resource-arn` to specify the Amazon Resource Name \(ARN\) of the associated repository that contains the tags you want to update or add to\. Use the `--tag-keys` argument to specify the *key* of the tags you want to remove\. The following command removes 3 tags\.

   ```
   aws codeguru-reviewer untag-resource /
     --resource-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid /
     --tag-keys key1 key2 key3
   ```

1. If successful, there is no output and no error\. If you want to verify the tags were removed correctly, use the describe\-repository\-association command and use `--association-arn` to specify the ARN of the associated repository\.

   ```
   aws codeguru-reviewer describe-repository-association /
     --association-arn arn:aws:codeguru-reviewer:us-west-2:123456789012:association:repository-association-uuid
   ```

   The output is a [https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_RepositoryAssociation.html) object that includes an array that does not contain the keys you removed\. In the following output example, all tags were removed so the tags array is empty\.

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
       "Tags": {}
   }
   ```