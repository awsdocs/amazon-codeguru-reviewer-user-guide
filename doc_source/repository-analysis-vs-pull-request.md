# About full repository analysis and incremental code reviews<a name="repository-analysis-vs-pull-request"></a>

There are two different kinds of code reviews that CodeGuru Reviewer can do to provide recommendations\.
+ *Incremental code reviews* are created automatically when you create a pull request from your repository context on an associated repository\. These code reviews scan the changed code in a pull request\.
+ *Full repository analysis code reviews* are done when you create a repository analysis code review in the CodeGuru Reviewer console\. These code reviews scan all the code in a specified branch\.

You can get recommendations in code reviews by using a full repository analysis or an incremental code review\. After you associate a repository, you can choose when to have an entire branch get a code review at any time by using a repository analysis\. Every pull request created on an associated repository also receives a code review\.


| Type of code review | Is the review automatic after I associate the repository? | Where can I see recommendations? | What code is reviewed? | 
| --- | --- | --- | --- | 
|  Full repository analysis  |  No\. You must request a repository analysis in the CodeGuru Reviewer console or by using the AWS CLI or AWS SDK\.  |  In the CodeGuru Reviewer console, or by using the AWS CLI or AWS SDK\.   |  All the code in the branch is reviewed\.  | 
|  Incremental code review  |  Yes\. After associating the repository, every time you do a pull request there is a code review\.  |  In the CodeGuru Reviewer console, in the AWS CLI or AWS SDK, or in pull request comments in the repository source provider\.  |  The code that is changed in the pull request is reviewed\.  | 