# Recommendations in Amazon CodeGuru Reviewer<a name="recommendations"></a>

Amazon CodeGuru Reviewer recommends various kinds of fixes in your Java and Python code\. These recommendations are based on common code scenarios and might not apply to all cases\. 

If you don't agree with a recommendation, you can [provide feedback](provide-feedback.md) in the CodeGuru Reviewer console or by commenting on the code in the pull requests\. Any positive or negative feedback can be used to help improve the performance of CodeGuru Reviewer so that recommendations get better over time\.

The following kinds of recommendations are provided\. 

**Topics**
+ [AWS best practices](#best-practices)
+ [Concurrency](#concurrency)
+ [Resource leak prevention](#resource-leak-prevention)
+ [Security analysis](#security-analysis)
+ [Sensitive information leak prevention](#info-leak-prevention)
+ [Common coding best practices](#common-bug-fixes)
+ [Refactoring](#refactoring)
+ [Input validation](#input-validation)
+ [Code maintainability detector](#code-quality)
+ [Third\-party recommendations](#third-party-recommendations)

## AWS best practices<a name="best-practices"></a>

AWS APIs contain a rich set of features to ensure performance and stability of software\. For example, usage patterns such as batching and waiters lead to enhanced performance and more efficient, maintainable code\. Use of pagination is often required to ensure correctness of code\. Developers might fail to use the right constructs when using AWS APIs, and this leads to problems in production\. AWS best practices provide recommendations on correct use of AWS APIs, which leads to availability and performance gains\. 

## Concurrency<a name="concurrency"></a>

CodeGuru Reviewer identifies problems with implementations of concurrency in multithreaded code\. Concurrency defects are often subtle and escape even expert programmers\. Incorrect implementations of concurrency can lead to incorrect code or performance issues\. CodeGuru Reviewer identifies atomicity violations that might result in correctness problems, and it identifies excessive synchronizations that might result in performance problems\.

## Resource leak prevention<a name="resource-leak-prevention"></a>

CodeGuru Reviewer looks for lines of code where resource leaks might be occurring\. Resource leaks can cause latency issues and outages\. CodeGuru Reviewer can point to code where this might be occurring and suggest handling the resources in a different way\.

## Security analysis<a name="security-analysis"></a>

 When you create a code review with security analysis, CodeGuru Reviewer performs a code review and also detects issues in your code that might compromise its security\. For each detected security issue, a recommendation is provided to help you improve your code security\. For more information, see [Create code reviews with GitHub Actions](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/working-with-cicd.html)\.

## Sensitive information leak prevention<a name="info-leak-prevention"></a>

Sensitive information in code should not be shared with unauthorized parties\. CodeGuru Reviewer looks for lines of code where sensitive information might be leaking, and suggests different ways to handle the data\.

## Common coding best practices<a name="common-bug-fixes"></a>

CodeGuru Reviewer checks parameters and looks for lines of code that could create bugs\. There are many common coding errors that cause bugs to happen, such as forgetting to check whether an object is null before setting it, reassigning a synchronized object, or forgetting to initialize a variable along an exception path\. CodeGuru Reviewer can point to the location of those errors and other sources of problems in code\.

## Refactoring<a name="refactoring"></a>

CodeGuru Reviewer looks for lines of code that appear to be duplicated or similar enough to be refactored\. Refactoring can help improve code maintainability\. 

## Input validation<a name="input-validation"></a>

It's important to detect unexpected input that arrives at a computation, and to apply appropriate validation before the computation starts\. Input validation is an important layer of defense against unintentional errors, such as client component changes, and malicious attacks, such as code injection or denial of service\. CodeGuru Reviewer looks for lines of code that process input data and suggests additional validation where it's needed\.

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

## Third\-party recommendations<a name="third-party-recommendations"></a>

 Amazon CodeGuru Reviewer code reviews incorporate analysis from third\-party providers\. If a third\-party tool finds an issue during a code review, then it adds recommendations to the recommendations created by CodeGuru Reviewer\. The following third\-party solutions are used during a code review\. 

Infer  
Infer is a third\-party tool that analyzes your Java code and detects potential bugs\. For more information about Infer, see its website at [Infer](https://fbinfer.com/)\. For the types of issues that Infer detects, see [List of all Infer issue types](https://fbinfer.com/docs/all-issue-types) on the Infer website\.

Bandit  
Bandit is a third\-party tool that finds security issues in Python code\. For more information about Bandit, see its website at [Bandit](https://bandit.readthedocs.io/en/latest/#)\. 