# Troubleshooting<a name="troubleshooting"></a>

This section helps you troubleshoot common problems you might encounter when working with Amazon CodeGuru Reviewer\. 

**Topics**
+ [Where can I check the status of a repository association?](#troubleshooting-status-repo-assoc)
+ [Where can I check the status of a code review?](#troubleshooting-status-code-review)
+ [Where can I check the status of a third\-party source provider connection?](#troubleshooting-status-connection)
+ [My repository is in an associated state\. Why don't I see recommendations?](#troubleshooting-status-no-recos)
+ [Why did my association fail?](#troubleshooting-status-repo-assoc-failed)
+ [Why did my code review fail?](#troubleshooting-status-code-review-failed)
+ [What if I disagree with the recommendation?](#troubleshooting-status-reco-disagree)
+ [How do I suppress a recommendation?](#troubleshooting-status-reco-suppress)
+ [The repository status has been associating for more than 5 minutes\. What should I do?](#troubleshooting-long-associating-time)
+ [The code review status has been Pending for more than 15 minutes\. What should I do?](#troubleshooting-long-code-review-time)
+ [How do you access a repository if its owner is no longer available?](#troubleshooting-losing-repository-owner)
+ [Can I use the same AWS CodeStar connection to access repositories in two different accounts?](#troubleshooting-multiple-third-party-accounts)
+ [I'm trying to connect to my third\-party repositories\. What is the difference between an app installation and a connection? Which one can be used to adjust permissions?](#troubleshooting-connections-and-apps)
+ [How do I know if CodeGuru Reviewer used my aws\-codeguru\-reviewer\.yml file in a code review?](#troubleshooting-config-file-used)
+ [Why didn't my costs decrease when I used an aws\-codeguru\-reviewer\.yml file?](#troubleshooting-config-file-costs)

## Where can I check the status of a repository association?<a name="troubleshooting-status-repo-assoc"></a>

You can check the status of a repository in the CodeGuru console\. In the navigation pane, choose **Reviewer**, and then choose **Repositories**\. The **Repositories** page lists all of the associated repositories and their statuses\. 

You can also use the AWS CLI or the AWS SDK\. First call `ListRepositoryAssociations` to find the association ID, then call `DescribeAssociation`\. 

## Where can I check the status of a code review?<a name="troubleshooting-status-code-review"></a>

You can check the status of a code review in the CodeGuru console\. In the navigation pane, choose **Reviewer**, and then choose **Code reviews**\. The **Code reviews** page lists all of the recent code reviews and their statuses\. 

You can also use the AWS CLI or the AWS SDK\. If you have the code review Amazon Resource Name \(ARN\), you can call `DescribeCodeReview`\. Alternatively, you can call `ListCodeReviews` and filter using `ProviderType` and `RepositoryName`\. 

## Where can I check the status of a third\-party source provider connection?<a name="troubleshooting-status-connection"></a>

If you are using a source provider that uses AWS CodeStar connections, you can check the status of a connection using the AWS CLI or AWS SDK\. To do this, call `ListConnections` and filter by the type of source provider, such as `Bitbucket`\. 

If you can see your connection displayed there with a status of **Available**, you should be able to return to the CodeGuru console and find your connection\. Try refreshing the display in the console if you haven't already\. Your connection only displays on the CodeGuru console if it has a status of **Available**\. The console does not display connections with a status of **Pending** or **Error**\. 

## My repository is in an associated state\. Why don't I see recommendations?<a name="troubleshooting-status-no-recos"></a>

This could happen for the following reasons: 
+ CodeGuru Reviewer doesn't have any recommendations\.
+ There has not been a pull request or a full repository analysis request, so CodeGuru Reviewer has not had a chance to review\.
+ There was an issue running CodeGuru Reviewer on the source code\. You should [contact AWS Support](https://aws.amazon.com/premiumsupport/?nc2=h_ql_ce_spt)\.

## Why did my association fail?<a name="troubleshooting-status-repo-assoc-failed"></a>

An association usually fails because of missing permissions\. You can find more information about why the association failed from the status reason\.

You can check the status of a repository association in the CodeGuru console\. 

1. In the navigation pane, choose **Reviewer**, and then choose **Repositories** to navigate to the **Repositories** page\. This page lists all the associated repositories and their statuses\.

1. Select the association for which you want to see status details\.

1. From the **Action** list, choose **View repository details**\. A small window opens with information about the repository and the association status\.

You can also use the AWS CLI or the AWS SDK\. First, call `ListRepositoryAssociations` to find the association ID, then call `DescribeAssociation`\. 

When you have fixed the problem, retry associating the repository\. 

## Why did my code review fail?<a name="troubleshooting-status-code-review-failed"></a>

To check the failure status reason of the code review, call the `DescribeCodeReview` API using the AWS CLI or the AWS SDK\. You can also find more information about why the code review failed from the status reason on the console\. To view details about a code review status on the console, navigate to the **Code reviews** page and choose the name of the code review that failed\. 

Code reviews usually fail for the following reasons: 
+ Source code access permissions are revoked, and CodeGuru Reviewer was not able to clone the source code to review\. In CodeCommit, this usually happens when the customer removes the `codeguru-reviewer–enabled` repository tag from the repository\. The easiest way to fix this is to disassociate the repository and then associate the repository again\.
+ The pull request being reviewed has been closed, or the branch being reviewed has been deleted, and CodeGuru Reviewer was not able to clone the source code to review before that occurred\. Wait for CodeGuru Reviewer to finish reviewing your code before deleting the source branch or closing the pull request\.

## What if I disagree with the recommendation?<a name="troubleshooting-status-reco-disagree"></a>

Recommendations depend on context and a variety of other factors\. It's possible that some recommendations are not useful\. In these cases, reply to the recommendation in the source provider or the CodeGuru Reviewer console to leave feedback on the recommendation\. 

In CodeCommit, a thumbs\-up or thumbs\-down icon is provided next to the comments that you can use to respond to comments made by CodeGuru Reviewer\. In other repository source providers, you can reply to a comment made by CodeGuru Reviewer, and include a thumbs\-up or thumbs\-down emoji in your comment to indicate whether it was helpful\. You can also go to the **Code reviews** page on the CodeGuru Reviewer console and select the name of a code review to view details and recommendations from that code review\. There are thumbs\-up and thumbs\-down icons there under each recommendation that you can choose to indicate whether the recommendation was helpful\.

## How do I suppress a recommendation?<a name="troubleshooting-status-reco-suppress"></a>

You cannot suppress *individual *recommendations, but you can suppress recommendations from CodeGuru Reviewer for specific files or directories in your repository\. To do so, add the files or directories to an `aws-codeguru-reviewer.yml` file\. For more information, see [Suppress recommendations](recommendation-suppression.md)\.

## The repository status has been associating for more than 5 minutes\. What should I do?<a name="troubleshooting-long-associating-time"></a>

If you have refreshed the page and the status has not changed after five minutes, it's possible that there is a problem with the repository source provider\. To check the status of the repository, on the **Repositories** page, choose **Action**, then **View repository details**\. 

## The code review status has been Pending for more than 15 minutes\. What should I do?<a name="troubleshooting-long-code-review-time"></a>

If you have refreshed the page and the status has not changed after 15 minutes, it's possible that there is a problem with the repository association or an internal failure\. To check the status reason of the code review, call the `DescribeCodeReview` API using the AWS CLI or the AWS SDK\. You can also find more information about why the code review failed from the status reason on the console\. To view details about a code review status on the console, navigate to the **Code reviews** page and choose the name of the code review that failed\.

## How do you access a repository if its owner is no longer available?<a name="troubleshooting-losing-repository-owner"></a>

If the owner of a repository is no longer able to maintain it, you should make another person an administrator\. The new administrator should then disassociate the repository and reassociate it\. Having a group or email list with administrator privileges helps avoid this problem\.

## Can I use the same AWS CodeStar connection to access repositories in two different accounts?<a name="troubleshooting-multiple-third-party-accounts"></a>

Each connection is associated with one third\-party repository source provider account\. To access repositories in multiple accounts, create separate connections and switch between the accounts to access corresponding repositories\. You can create separate connections for the different accounts from the **Associate repository** page in the console\.

## I'm trying to connect to my third\-party repositories\. What is the difference between an app installation and a connection? Which one can be used to adjust permissions?<a name="troubleshooting-connections-and-apps"></a>

An *app installation* is a feature that allows AWS CodeStar connections to create connections to a single repository source provider account\. A *connection* is a feature that uses an app installation through AWS CodeStar connections to connect a CodeGuru Reviewer account to a repository source provider account\. Multiple connections can be used for the same app installation if different users need to have different levels of permissions\. 

## How do I know if CodeGuru Reviewer used my aws\-codeguru\-reviewer\.yml file in a code review?<a name="troubleshooting-config-file-used"></a>

CodeGuru Reviewer recognizes the presence of a valid and correctly named `aws-codeguru-reviewer.yml` file in your repository when it creates a full repository analysis code review or an incremental code review\. 

**To confirm that CodeGuru Reviewer used your `aws-codeguru-reviewer.yml` file in a code review**

1. In the CodeGuru Reviewer console, choose **Code reviews**\. This page lists all code reviews performed\.

1. Choose a code review in the list\.
   + If CodeGuru Reviewer used your file in the code review, then **Success** appears under **Analysis configuration file**\.  
![\[The Details section of a code review. Success appears under Analysis configuration file.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-config-file-success.png)
   + If CodeGuru Reviewer found errors in your file, then **Error** appears under **Analysis configuration file** and a message indicating the errors appears at the top of the page\. 

     Also, **Failed** appears under **Status**, indicating that CodeGuru Reviewer did not perform a code review\.

     Fix your `aws-codeguru-reviewer.yml` file based on the error messages and then initiate a new full repository analysis\. For more information, see [Error handling for the aws\-codeguru\-reviewer\.yml file](recommendation-suppression.md#error-handling-yml)\. ****  
![\[The Details section of a code review. List of errors in your YAML file appears in top banner.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-config-file-error.png)
   + If CodeGuru Reviewer did not recognize your file name or find the file at the root directory of your repository, then **No file detected** appears under **Analysis configuration file**\. Your file must be named `aws-codeguru-reviewer.yml` and must exist in the root directory of your repository\. Otherwise CodeGuru Reviewer cannot recognize that the file exists, use it in code reviews, or return error messages about problems with the file\.

     Confirm the name and location of your file, make any needed changes, and then initiate a new code review\.  
![\[The Details section of a code review. No file detected appears under Analysis configuration file.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-no-file-detected.png)

For more information about using an `aws-codeguru-reviewer.yml` file, see [Suppress recommendations](recommendation-suppression.md)\.

## Why didn't my costs decrease when I used an aws\-codeguru\-reviewer\.yml file?<a name="troubleshooting-config-file-costs"></a>

Using an `aws-codeguru-reviewer.yml` file to suppress recommendations from CodeGuru Reviewer might decrease the amount of code that CodeGuru Reviewer analyzes and reduce your costs\. If your costs do not decrease as expected when using an `aws-codeguru-reviewer.yml` file, then check the following possible reasons\.
+ CodeGuru Reviewer didn't recognize your `aws-codeguru-reviewer.yml` and couldn't use it to suppress recommendations during a code review\. Confirm that you named your file correctly and used the correct extension\.
+ Your `aws-codeguru-reviewer.yml` file is not excluding as much content as you initially thought\. Check the files and directories listed under `excludeFiles:` in your `aws-codeguru-reviewer.yml` file\.
+ Your repository increased in size, which offset any reduction from the files and directories listed under `excludeFiles:` in your `aws-codeguru-reviewer.yml` file\.
+ For incremental code reviews, monthly charges are based on the *maximum* number of lines of code reviewed during the month\. For example, if your repository includes 150,000 lines of code and you initiate a full repository analysis code review, but later in the month, you add some files or directories to a `aws-codeguru-reviewer.yml` file in your repository and run a new code review of 50,000 lines of code, your monthly bill reflects the cost for reviewing the *larger* number: 150,000 lines of code\.

For more information about using an `aws-codeguru-reviewer.yml` file, see [Suppress recommendations](recommendation-suppression.md)\.