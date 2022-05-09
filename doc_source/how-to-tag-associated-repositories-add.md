# Add a tag to a CodeGuru Reviewer associated repository<a name="how-to-tag-associated-repositories-add"></a>

Adding tags to an associated repository can help you identify and organize your AWS resources and manage access to them\. First, you add one or more tags \(key\-value pairs\) to an associated repository\. Keep in mind that there are limits on the number of tags you can have on an associated repository\. There are restrictions on the characters you can use in the key and value fields\. For more information, see [Tags](quotas.md#limits-tags)\. After you have tags, you can create IAM policies to manage access to the associated repository based on these tags\. You can use the CodeGuru Reviewer console, AWS CLI, or SDK to add tags to an associated repository\. 

**Important**  
Adding tags to an associated repository can impact access to that associated repository\. Before you add a tag to an associated repository, make sure to review any IAM policies that might use tags to control access to resources such as associated repositories\. For examples of tag\-based access policies, see [Using tags to control access to Amazon CodeGuru Reviewer associated repositories](auth-and-access-control-using-tags.md)\.

**Topics**
+ [Add a tag to a CodeGuru Reviewer associated repository \(console\)](how-to-tag-associated-repository-add-console.md)
+ [Add a tag to a CodeGuru Reviewer associated repository \(AWS CLI\)](how-to-tag-associated-repository-add-cli.md)