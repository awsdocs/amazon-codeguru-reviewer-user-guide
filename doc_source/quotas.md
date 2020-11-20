# Quotas for CodeGuru Reviewer<a name="quotas"></a>

The following table lists the current quota in Amazon CodeGuru Reviewer\. This quota is for each supported AWS Region for each AWS account\. 

## CodeCommit repositories<a name="limits-reviewer"></a>


****  

| Resource | Default | 
| --- | --- | 
| Maximum number of analyzed pull requests per month | 5,000 | 

## Tags<a name="limits-tags"></a>

 Tag limits apply to tags on CodeGuru Reviewer associated repository resources\. 


****  

| Resource | Default | 
| --- | --- | 
| Maximum number of tags you can associate with a resource | 50 \(tags are case sensitive\)\. | 
| Resource tag key names |  Any combination of Unicode letters, numbers, spaces, and allowed characters in UTF\-8 between 1 and 127 characters in length\. Allowed characters are `+ - = . _ : / @`\. Tag key names must be unique, and each key can only have one value\. A tag key name cannot: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/quotas.html)  | 
| Resource tag values |  Any combination of Unicode letters, numbers, spaces, and allowed characters in UTF\-8 between 0 and 255 characters in length\. Allowed characters are `+ - = . _ : / @`\. A key can only have one value, but many keys can have the same value\. A tag key value cannot contain emojis or any of the following characters:` ? ^ * [ \ ~ ! # $ % & * ( ) > < \| " ' ` [ ] { } ;`\.  | 