# Using identity\-based policies for CodeGuru Reviewer<a name="auth-and-access-control-iam-identity-based-access-control"></a>

By default, IAM users and roles don't have permission to create or modify Amazon CodeGuru Reviewer resources\. They also can't perform tasks using the AWS Management Console, AWS CLI, or AWS API\. An IAM administrator must create IAM policies that grant users and roles permission to perform specific API operations on the specified resources they need\. The administrator must then attach those policies to the IAM users or groups that require those permissions\. To learn how to attach policies to an IAM user or group, see [Adding and Removing IAM Identity Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the *IAM User Guide*\.

To learn how to create an IAM identity\-based policy using these example JSON policy documents, see [Creating Policies on the JSON Tab](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

**Topics**
+ [Policy best practices](#security_iam_service-with-iam-policy-best-practices)
+ [Permissions required to use the CodeGuru Reviewer console](#console-permissions)
+ [AWS managed \(predefined\) policies for CodeGuru Reviewer](#managed-policies)
+ [CodeGuru Reviewer updates to AWS managed policies](#security-iam-awsmanpol-updates)
+ [Customer managed policy examples](#security_iam_id-based-policy-examples)

## Policy best practices<a name="security_iam_service-with-iam-policy-best-practices"></a>

Identity\-based policies determine whether someone can create, access, or delete CodeGuru Reviewer resources in your account\. These actions can incur costs for your AWS account\. When you create or edit identity\-based policies, follow these guidelines and recommendations:
+ **Get started with AWS managed policies and move toward least\-privilege permissions** – To get started granting permissions to your users and workloads, use the *AWS managed policies* that grant permissions for many common use cases\. They are available in your AWS account\. We recommend that you reduce permissions further by defining AWS customer managed policies that are specific to your use cases\. For more information, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) or [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.
+ **Apply least\-privilege permissions** – When you set permissions with IAM policies, grant only the permissions required to perform a task\. You do this by defining the actions that can be taken on specific resources under specific conditions, also known as *least\-privilege permissions*\. For more information about using IAM to apply permissions, see [ Policies and permissions in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *IAM User Guide*\.
+ **Use conditions in IAM policies to further restrict access** – You can add a condition to your policies to limit access to actions and resources\. For example, you can write a policy condition to specify that all requests must be sent using SSL\. You can also use conditions to grant access to service actions if they are used through a specific AWS service, such as AWS CloudFormation\. For more information, see [ IAM JSON policy elements: Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) in the *IAM User Guide*\.
+ **Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions** – IAM Access Analyzer validates new and existing policies so that the policies adhere to the IAM policy language \(JSON\) and IAM best practices\. IAM Access Analyzer provides more than 100 policy checks and actionable recommendations to help you author secure and functional policies\. For more information, see [IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html) in the *IAM User Guide*\.
+ **Require multi\-factor authentication \(MFA\)** – If you have a scenario that requires IAM users or root users in your account, turn on MFA for additional security\. To require MFA when API operations are called, add MFA conditions to your policies\. For more information, see [ Configuring MFA\-protected API access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_configure-api-require.html) in the *IAM User Guide*\.

For more information about best practices in IAM, see [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\.

## Permissions required to use the CodeGuru Reviewer console<a name="console-permissions"></a>

A user who uses the CodeGuru Reviewer console must have a minimum set of permissions that allows the user to describe other AWS resources for the AWS account\. You must have permissions from the following services:
+ CodeGuru Reviewer
+ AWS CodeCommit \(if your source code is in a CodeCommit repository\)
+ AWS CodeStar connections \(if your source code is in a repository managed by AWS CodeStar connections, such as Bitbucket\)
+ AWS Identity and Access Management \(IAM\)

 If your source code is in a GitHub repository, you must have an OAuth token to connect to it\. Associated GitHub repositories are not managed by AWS CodeStar connections\. For more information, see [Git automation with OAuth tokens](https://help.github.com/en/github/extending-github/git-automation-with-oauth-tokens#step-1-get-an-oauth-token) on the GitHub website\. 

If you create an IAM policy that is more restrictive than the minimum required permissions, the console won't function as intended\.

The following shows an example of a permissions policy that allows a user to get information about a repository association only in the `us-east-2` Region for account `123456789012` for any repository association with a universally unique identifier \(UUID\) that starts with `12345`\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "codeguru-reviewer:DescribeRepositoryAssociation",
      "Resource": "arn:aws:codeguru-reviewer:us-east-2:123456789012:association:12345*"      
    }
  ]
}
```

## AWS managed \(predefined\) policies for CodeGuru Reviewer<a name="managed-policies"></a>

AWS addresses many common use cases by providing standalone IAM policies that are created and administered by AWS\. These AWS managed policies grant necessary permissions for common use cases so you can avoid having to investigate what permissions are needed\. For more information, see [AWS Managed Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

To create and manage CodeGuru Reviewer service roles, you must also attach the AWS managed policy named `IAMFullAccess`\.

You can also create your own custom IAM policies to allow permissions for CodeGuru Reviewer actions and resources\. You can attach these custom policies to the IAM users or groups that require those permissions\.

The following AWS managed policies, which you can attach to users in your account, are specific to CodeGuru Reviewer\.

**Topics**
+ [AmazonCodeGuruReviewerFullAccess](#managed-full-access)
+ [AmazonCodeGuruReviewerReadOnlyAccess](#managed-read-only-access)
+ [AmazonCodeGuruReviewerServiceRolePolicy](#managed-policy-for-codecommit-and-codestar-connections)

### AmazonCodeGuruReviewerFullAccess<a name="managed-full-access"></a>

`AmazonCodeGuruReviewerFullAccess` – Provides full access to CodeGuru Reviewer, including permissions to tag repository associations and to create, update, and delete code reviews and repository associations\. It also grants permission to related resources in other services that integrate with CodeGuru Reviewer, such as Amazon CloudWatch, AWS CodeStar connections, and CodeCommit\. Apply this only to administrative\-level users to who you want to grant full control over CodeGuru Reviewer repository associations, code reviews, and related resources in your AWS account, including the ability to delete code reviews and repository associations\. 

The `AmazonCodeGuruReviewerFullAccess` policy contains the following statement\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AmazonCodeGuruReviewerFullAccess",
            "Effect": "Allow",
            "Action": [
                "codeguru-reviewer:*"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AmazonCodeGuruReviewerSLRCreation",
            "Action": "iam:CreateServiceLinkedRole",
            "Effect": "Allow",
            "Resource": "arn:aws:iam::*:role/aws-service-role/codeguru-reviewer.amazonaws.com/AWSServiceRoleForAmazonCodeGuruReviewer",
            "Condition": {
                "StringLike": {
                    "iam:AWSServiceName": "codeguru-reviewer.amazonaws.com"
                }
            }
        },
        {
            "Sid": "AmazonCodeGuruReviewerSLRDeletion",
            "Effect": "Allow",
            "Action": [
                "iam:DeleteServiceLinkedRole",
                "iam:GetServiceLinkedRoleDeletionStatus"
            ],
            "Resource": "arn:aws:iam::*:role/aws-service-role/codeguru-reviewer.amazonaws.com/AWSServiceRoleForAmazonCodeGuruReviewer"
        },
        {
            "Sid": "codecommitAccess",
            "Effect": "Allow",
            "Action": [
                "codecommit:ListRepositories"
            ],
            "Resource": "*"
        },
        {
            "Sid": "codecommitTagManagement",
            "Effect": "Allow",
            "Action": [
                "codecommit:TagResource",
                "codecommit:UntagResource"
            ],
            "Resource": "*",
            "Condition": {
                "ForAllValues:StringEquals": {
                    "aws:TagKeys": "codeguru-reviewer"
                }
            }
        },
        {
            "Sid": "CodeConnectTagManagement",
            "Effect": "Allow",
            "Action": [
                "codestar-connections:TagResource",
                "codestar-connections:UntagResource",
                "codestar-connections:ListTagsForResource"
            ],
            "Resource": "*",
            "Condition": {
                "ForAllValues:StringEquals": {
                    "aws:TagKeys": "codeguru-reviewer"
                }
            }
        },
        {
            "Sid": "CodeConnectManagedRules",
            "Effect": "Allow",
            "Action": [
                "codestar-connections:UseConnection",
                "codestar-connections:ListConnections",
                "codestar-connections:PassConnection"
            ],
            "Resource": "*",
            "Condition": {
                "ForAllValues:StringEquals": {
                    "codestar-connections:ProviderAction": [
                        "ListRepositories",
                        "ListOwners"
                    ]
                }
            }
        },
        {
            "Sid": "CloudWatchEventsManagedRules",
            "Effect": "Allow",
            "Action": [
                "events:PutRule",
                "events:PutTargets",
                "events:DeleteRule",
                "events:RemoveTargets"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "events:ManagedBy": "codeguru-reviewer.amazonaws.com"
                }
            }
        }
    ]
}
```

### AmazonCodeGuruReviewerReadOnlyAccess<a name="managed-read-only-access"></a>

`AmazonCodeGuruReviewerReadOnlyAccess` – Grants read\-only access to CodeGuru Reviewer and related resources in other AWS services\. Apply this policy to users who you want to grant the ability to view code reviews, but not to create or make any changes to them\. 

The `AmazonCodeGuruReviewerReadOnlyAccess` policy contains the following statement\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AmazonCodeGuruReviewerReadOnlyAccess",
            "Effect": "Allow",
            "Action": [
                "codeguru-reviewer:List*",
                "codeguru-reviewer:Describe*",
                "codeguru-reviewer:Get*"
            ],
            "Resource": "*"
        }
    ]
}
```

### AmazonCodeGuruReviewerServiceRolePolicy<a name="managed-policy-for-codecommit-and-codestar-connections"></a>

`AmazonCodeGuruReviewerServiceRolePolicy` – Grants permission to related resources in CodeCommit, AWS CodeStar connections, Amazon S3, and CloudWatch that are required to create repository associations\. 

For CodeCommit repository associations, the CodeCommit and CloudWatch permissions in this policy are required\. For associations with repositories that are managed by an AWS CodeStar connection, such as Bitbucket, the AWS CodeStar connections permissions are required\. For code reviews with security analysis, the Amazon S3 permissions are required\.

 When you create your first association with a CodeCommit, Amazon S3, or AWS CodeStar connections managed repository, CodeGuru Reviewer adds the `AmazonCodeGuruReviewerServiceRolePolicy` policy to your AWS account\. This policy grants CodeGuru Reviewer access to CodeCommit repositories, AWS CodeStar connections resources in your account that have a `aws:ResourceTag/codeguru-reviewer` tag\. It also grants access to Amazon S3 buckets that have a prefix that begins with `codeguru-reviewer-`\. When you associate a CodeCommit repository, CodeGuru Reviewer adds this tag to the repository\. When you associate an AWS CodeStar connections managed repository, CodeGuru Reviewer adds this tag to the AWS CodeStar connections resource, if it doesn't already exist\. 

The `AmazonCodeGuruReviewerServiceRolePolicy` policy contains the following statement\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AccessCodeGuruReviewerEnabledRepositories",
            "Effect": "Allow",
            "Action": [
                "codecommit:GetRepository",
                "codecommit:GetBranch",
                "codecommit:DescribePullRequestEvents",
                "codecommit:GetCommentsForPullRequest",
                "codecommit:GetDifferences",
                "codecommit:GetPullRequest",
                "codecommit:ListPullRequests",
                "codecommit:PostCommentForPullRequest",
                "codecommit:GitPull",
                "codecommit:UntagResource"
            ],
            "Resource": "*",
            "Condition": {
                "StringLike": {
                    "aws:ResourceTag/codeguru-reviewer": "enabled"
                }
            }
        },
        {
            "Sid": "AccessCodeGuruReviewerEnabledConnections",
            "Effect": "Allow",
            "Action": [
                "codestar-connections:UseConnection"
            ],
            "Resource": "*",
            "Condition": {
                "ForAllValues:StringEquals": {
                    "codestar-connections:ProviderAction": [
                        "ListBranches",
                        "GetBranch",
                        "ListRepositories",
                        "ListOwners",
                        "ListPullRequests",
                        "GetPullRequest",
                        "ListPullRequestComments",
                        "ListPullRequestCommits",
                        "ListCommitFiles",
                        "ListBranchCommits",
                        "CreatePullRequestDiffComment",
                        "GitPull"
                    ]
                },
                "Null": {
                    "aws:ResourceTag/codeguru-reviewer": "false"
                }
            }
        },
        {
            "Sid": "CloudWatchEventsResourceCleanup",
            "Effect": "Allow",
            "Action": [
                "events:DeleteRule",
                "events:RemoveTargets"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "events:ManagedBy": "codeguru-reviewer.amazonaws.com"
                }
            }
        },
        {
            "Sid": "AccessCodeGuruReviewerCreatedS3Bucket",
            "Effect": "Allow",
            "Action": [    
                "s3:GetObject",
                "s3:CreateBucket",
                "s3:ListBucket",
                "s3:PutBucketPolicy",
                "s3:PutLifecycleConfiguration"
            ],
            "Resource": [
                "arn:aws:s3:::codeguru-reviewer-*",
                "arn:aws:s3:::codeguru-reviewer-*/*"
            ]
        }
    ]
}
```

## CodeGuru Reviewer updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>



View details about updates to AWS managed policies for CodeGuru Reviewer since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the CodeGuru Reviewer [Amazon CodeGuru Reviewer user guide document history](doc-history.md)\.




| Change | Description | Date | 
| --- | --- | --- | 
|  [AmazonCodeGuruReviewerServiceRolePolicy](#managed-policy-for-codecommit-and-codestar-connections) – Update to an existing policy  |  CodeGuru Reviewer added new permissions to allow access to the `CreateBucket`, `ListBucket`, `PutBucketPolicy`, and `PutLifecycleConfiguration` actions on an Amazon S3 bucket resource\.  | April 28, 2021 | 
|  CodeGuru Reviewer started tracking changes  |  CodeGuru Reviewer started tracking changes for its AWS managed policies\.  | July 2, 2020 | 

## Customer managed policy examples<a name="security_iam_id-based-policy-examples"></a>

You can create your own custom IAM policies to allow permissions for CodeGuru Reviewer actions and resources\. You can attach these custom policies to the IAM users, roles, or groups that require those permissions\. You can also create your own custom IAM policies for integration between CodeGuru Reviewer and other AWS services\. 

 The following example IAM policies grant permissions for various CodeGuru Reviewer actions\. Use them to limit CodeGuru Reviewer access for your IAM users and roles\. These policies control the ability to perform actions with the CodeGuru Reviewer console, API, AWS SDKs, or the AWS CLI\. 

**Note**  
All examples use the US East \(Ohio\) Region \(us\-east\-2\) and contain fictitious account IDs\.

 **Examples**
+ [Example 1: Allow a user to see all recommendations created in an associated repository](#identity-based-policies-example-1)
+ [Example 2: Allow a user to view code reviews in an associated repository in a single Region](#identity-based-policies-example-2)
+ [Example 3: Allow a user to perform CodeGuru Reviewer operations in a single Region](#identity-based-policies-example-3)
+ [Example 4: Allow read\-only access to CodeGuru Reviewer operations for a user connecting from a specified IP address range ](#identity-based-policies-example-4)

### Example 1: Allow a user to see all recommendations created in an associated repository<a name="identity-based-policies-example-1"></a>

 The following example policy grants permissions for the AWS user with account ID `123456789012` to see a list of all recommendations in their AWS account and Region in the repository association with ID `association-uuid`\. 

```
{
   "Version": "2012-10-17",
   "Statement": [
      {
         "Effect": "Allow",
         "Action": [
            "codeguru-reviewer:ListRecommendations"
         ],
         "Resource": "arn:aws:codeguru-reviewer:us-east-2:123456789012:association:association-uuid"
      }
   ]
}
```

### Example 2: Allow a user to view code reviews in an associated repository in a single Region<a name="identity-based-policies-example-2"></a>

The following shows an example of a permissions policy that allows a user with account ID `123456789012` to get information about code reviews in Region `us-east-2` in an associated repository with ID `association-uuid`\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "codeguru-reviewer:DescribeCodeReview",
      "Resource": "arn:aws:codeguru-reviewer:us-east-2:123456789012:association:association-uuid"      
    }
  ]
}
```

### Example 3: Allow a user to perform CodeGuru Reviewer operations in a single Region<a name="identity-based-policies-example-3"></a>

The following permissions policy uses a wildcard character \(`"codeguru-reviewer:*"`\) to allow users to perform all CodeGuru Reviewer actions in the us\-east\-2 Region and not from other AWS Regions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
    {
            "Effect": "Allow",
            "Action": "codeguru-reviewer:*",
            "Resource": "arn:aws:codeguru-reviewer:us-east-2:123456789012:*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestedRegion": "us-east-2"
                }
            }
        }
    ]
}
```

### Example 4: Allow read\-only access to CodeGuru Reviewer operations for a user connecting from a specified IP address range<a name="identity-based-policies-example-4"></a>

You can create a policy that only allows users CodeGuru Reviewer read\-only access if their IP address is within a certain IP address range\. The following example grants read\-only CodeGuru Reviewer permissions to users whose IP addresses are within the specified IP address block of 203\.0\.113\.0/24\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
          "codeguru-reviewer:List*",
          "codeguru-reviewer:Describe*"
      ],
      "Resource": "*",
      "Condition": {
        "IpAddress": {
          "aws:SourceIp": "203.0.113.0/24"
        }
      }
    }
  ]
}
```