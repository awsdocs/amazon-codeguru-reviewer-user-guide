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

## CodeGuru Reviewer quotas for creating, deploying, and managing an API<a name="codeguru-reviewer-control-service-limits-table"></a>

The following fixed quotas apply to creating, deploying, and managing an API in CodeGuru Reviewer, using the AWS CLI, the API Gateway console, or the API Gateway REST API and its SDKs\. These quotas can't be increased\.

The default quota for all except three CodeGuru Reviewer APIs is 1 request per second per account\. None of these quotas can be increased\. For a list of all CodeGuru Reviewer APIs, see [ Amazon CodeGuru Reviewer Actions](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_Operations.html)\.

The three APIs with different default quotas are in the following table\.


| Action | Default quota | Can be increased | 
| --- | --- | --- | 
| [AssociateRepository](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_AssociateRepository.html) | 1 request every 2 seconds per account | No | 
| [CreateCodeReview](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_CreateCodeReview.html) | 1 request every 2 seconds per account | No | 
| [PutRecommendationFeedback](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/API_PutRecommendationFeedback.html) | 2 request per second per account | No | 