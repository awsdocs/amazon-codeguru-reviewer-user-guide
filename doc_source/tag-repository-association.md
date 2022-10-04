# Tagging a repository association in Amazon CodeGuru Reviewer<a name="tag-repository-association"></a>

A *tag* is a custom attribute label that you or AWS assigns to an AWS resource\. Each AWS tag has two parts:
+ A tag *key* \(for example, `CostCenter`, `Environment`, `Project`, or `Secret`\)\. Tag keys are case sensitive\.
+ An optional field known as a tag *value* \(for example, `111122223333`, `Production`, or a team name\)\. Omitting the tag value is the same as using an empty string\. Like tag keys, tag values are case sensitive\.

Together these are known as *key*\-*value* pairs\. For limits on the number of tags you can have on an associated repository and restrictions on tag keys and values, see [Tags](quotas.md#limits-tags)\. 

Tags help you identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources from different services to indicate that the resources are related\. For example, you can assign the same tag to a CodeGuru Reviewer associated repository that you assign to an AWS CodeBuild build project\. For more information about using tags, see the [Tagging Best Practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\. 

In CodeGuru Reviewer, you can use the CodeGuru Reviewer console, the AWS CLI, CodeGuru Reviewer APIs, or AWS SDKs to add, manage, and remove tags for a repository association\. In addition to identifying, organizing, and tracking your repository association with tags, you can use tags in IAM policies to help control who can view and interact with your repository association\. 

A repository association has a parent\-child hierarchical relationship with code reviews because a repository association contains all the code reviews inside it\. Because of this, you can use tags on repository associations to control access to the code reviews in it\. For examples of tag\-based access policies, see [Using tags to control access to Amazon CodeGuru Reviewer associated repositories](auth-and-access-control-using-tags.md)\.

**Topics**
+ [Add a tag to a CodeGuru Reviewer associated repository](how-to-tag-associated-repositories-add.md)
+ [View tags for a CodeGuru Reviewer associated repository](how-to-tag-associated-repository-view.md)
+ [Add or update tags for a CodeGuru Reviewer associated repository](how-to-tag-associated-repository-update.md)
+ [Remove tags from a CodeGuru Reviewer associated repository](how-to-tag-associated-repository-remove.md)