# Recommendation types in CodeGuru Reviewer<a name="recommendations"></a>

Amazon CodeGuru Reviewer recommends various kinds of fixes in your Java and Python code\. These recommendations are based on common code scenarios and might not apply to all cases\. 

If you don't agree with a recommendation, you can [provide feedback](provide-feedback.md) in the CodeGuru Reviewer console or by commenting on the code in the pull requests\. Any positive or negative feedback can be used to help improve the performance of CodeGuru Reviewer so that recommendations get better over time\.

The following kinds of recommendations are provided\.

**Topics**
+ [AWS best practices](#best-practices)
+ [Code maintainability detector](#code-quality)
+ [Common coding best practices](#common-bug-fixes)
+ [Concurrency](#concurrency)
+ [Input validation](#input-validation)
+ [Refactoring](#refactoring)
+ [Resource leak prevention](#resource-leak-prevention)
+ [Secrets detection](#secrets-detection)
+ [Security analysis](#security-analysis)
+ [Sensitive information leak prevention](#info-leak-prevention)

## AWS best practices<a name="best-practices"></a>

AWS APIs contain a rich set of features to ensure performance and stability of software\. For example, usage patterns such as batching and waiters lead to enhanced performance and more efficient, maintainable code\. Use of pagination is often required to ensure correctness of code\. Developers might fail to use the right constructs when using AWS APIs, and this leads to problems in production\. AWS best practices provide recommendations on correct use of AWS APIs, which leads to availability and performance gains\. 

## Code maintainability detector<a name="code-quality"></a>

 CodeGuru Reviewer code analysis suggests how you can improve the quality of your code\. The following are some of the code quality issues that it finds and about which it informs you\. 

Method source lines of code \(Source LOC\)  
CodeGuru Reviewer detects the number of lines of source code \(*Source LOC*\) in a method\. Large methods with a high number of lines can be difficult to read and have logic that is hard to understand and test\.

Method cyclomatic complexity  
*Cyclomatic complexity* indicates the number of decisions that are made in a method\. A method with high cyclomatic complexity can make its logic difficult to understand and test\.

Method fan out  
*Method fan out* indicates how many methods are called by a given method\. Methods with high fan out are highly coupled with other methods\. This can make them difficult to understand and vulnerable to unexpected behavior changes when one of their referenced methods is updated\.

Class fan out  
*Class fan out* indicates how many other classes are referenced by a given class\. The higher the number of classes that are referenced, the more it is coupled with other classes and the higher the fan out\. Classes with high fan out can be complex, difficult to understand, and might change unexpectedly when a referenced classes is updated\.

Class cohesion  
 CodeGuru Reviewer notices if a class contains clusters of instance methods that do not have any accessed class members in common\. For example, a cluster of two methods might access only the class fields `x` and `y`, and another cluster of methods in the same class might access only the class fields `a` and `b`\. A high number of these clusters indicates low *class cohesion*\. Classes with low cohesion contain unrelated operations, can be difficult to understand, and are often less likely to be used\.

## Common coding best practices<a name="common-bug-fixes"></a>

CodeGuru Reviewer checks parameters and looks for lines of code that could create bugs\. There are many common coding errors that cause bugs to happen, such as forgetting to check whether an object is null before setting it, reassigning a synchronized object, or forgetting to initialize a variable along an exception path\. CodeGuru Reviewer can point to the location of those errors and other sources of problems in code\.

## Concurrency<a name="concurrency"></a>

CodeGuru Reviewer identifies problems with implementations of concurrency in multithreaded code\. Concurrency defects are often subtle and escape even expert programmers\. Incorrect implementations of concurrency can lead to incorrect code or performance issues\. CodeGuru Reviewer identifies atomicity violations that might result in correctness problems, and it identifies excessive synchronizations that might result in performance problems\.

## Input validation<a name="input-validation"></a>

It's important to detect unexpected input that arrives at a computation, and to apply appropriate validation before the computation starts\. Input validation is an important layer of defense against unintentional errors, such as client component changes, and malicious attacks, such as code injection or denial of service\. CodeGuru Reviewer looks for lines of code that process input data and suggests additional validation where it's needed\.

## Refactoring<a name="refactoring"></a>

CodeGuru Reviewer looks for lines of code that appear to be duplicated or similar enough to be refactored\. Refactoring can help improve code maintainability\. 

## Resource leak prevention<a name="resource-leak-prevention"></a>

CodeGuru Reviewer looks for lines of code where resource leaks might be occurring\. Resource leaks can cause latency issues and outages\. CodeGuru Reviewer can point to code where this might be occurring and suggest handling the resources in a different way\.

## Secrets detection<a name="secrets-detection"></a>

CodeGuru Reviewer integrates with AWS Secrets Manager to use a secrets detector that finds unprotected secrets in your code\. Secrets detection is automatic, so you don't need to turn it on\. 

The secrets detector searches for hardcoded passwords, database connection strings, user names, and more\. When an unprotected secret is found during a code review, CodeGuru Reviewer generates a recommendation and displays it with your code reviews\. The recommendation tells you about the unprotected secret\. To immediately protect that secret, choose **Protect your credential** in the code review\. This opens the Secrets Manager console to protect and manage the secret\. For more information, see [Create a secret](https://docs.aws.amazon.com/secretsmanager/latest/userguide/manage_create-basic-secret.html) in the *AWS Secrets Manager User Guide* and [View recommendations and provide feedback](give-feedback-from-code-review-details.md)\.

**Topics**
+ [Secrets detection supported file types](#secrets-file-extension-support)
+ [Types of secrets detected by CodeGuru Reviewer](#secrets-found-types)

### Secrets detection supported file types<a name="secrets-file-extension-support"></a>

The secrets detector finds unprotected secrets the following file types with a maximum file size of 100kb\.
+ Config files \(\*\.config, \*\.cfg, \*\.conf, \*\.cnf, \*\.cf\)
+ Environment files \(\*\.env\)
+ Initialization files \(\*\.ini\)
+ Java files \(\*\.java\)
+ JSON files \(\*\.json\)
+ Jupyter Notebook files \(\*\.ipynb\)
+ Key files \(\*\.key\)
+ Markdown files \(\*\.md\)
+ Privacy Enhanced Mail files \(\*\.pem\)
+ Property List files \(\*\.plist\)
+ Python files \(\*\.py\)
+ reStructuredText files \(\*\.rst\)
+ Text files \(\*\.txt, \*\.text\)
+ TOML files \(\*\.toml\)
+ XML files \(\*\.xml\)
+ YAML files \(\*\.yml, \*\.yaml\)

### Types of secrets detected by CodeGuru Reviewer<a name="secrets-found-types"></a>

Amazon CodeGuru Reviewer detects unprotected usernames, passwords, RSA keys, and the following secrets\.


**Secrets detected by CodeGuru Reviewer**  

| Provider | Secrets detected | 
| --- | --- | 
| Amazon Web Services \(AWS\) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Atlassian |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Databricks |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Datadog |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| GitHub |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Hubspot |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Intercom |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Mailchimp |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Mailgun |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Salesforce |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| SendGrid |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Shopify |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Slack |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Stripe |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Tableau |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Telegram |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 
| Twilio |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/recommendations.html)  | 

## Security analysis<a name="security-analysis"></a>

 When you create a code review with security analysis, CodeGuru Reviewer performs a code review and also detects issues in your code that might compromise its security\. For each detected security issue, a recommendation is provided to help you improve your code security\. For more information, see [Create code reviews with GitHub Actions](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/working-with-cicd.html)\.

## Sensitive information leak prevention<a name="info-leak-prevention"></a>

Sensitive information in code should not be shared with unauthorized parties\. CodeGuru Reviewer looks for lines of code where sensitive information might be leaking, and suggests different ways to handle the data\.