# Connect to GitHub Enterprise Server to associate a repository with CodeGuru Reviewer<a name="github-enterprise-steps"></a>

You can connect to GitHub Enterprise Server using an AWS CodeStar connection\. This enables you to associate repositories in a GitHub Enterprise Server account with CodeGuru Reviewer to receive [recommendations](recommendations.md) for improvements in your Java code\.

**Note**  
GitHub Enterprise Server repositories are associated using this procedure, but GitHub Enterprise Cloud repositories and other GitHub repositories have a [different procedure](github-steps.md)\.

To connect to GitHub Enterprise Server, you create a connection and a host through AWS CodeStar connections to allow CodeGuru Reviewer to access your repositories to provide recommendations\. For more information about connections and hosts, see [Working with connections](https://docs.aws.amazon.com/dtconsole/latest/userguide/connections.html) and [Working with hosts](https://docs.aws.amazon.com/dtconsole/latest/userguide/connections-hosts.html)\.

## Prerequisites for Connecting to GitHub Enterprise Server<a name="ghe-connection-prereqs"></a>

 Before you connect to GitHub Enterprise Server, complete the following requirements: 
+ You must have a GitHub Enterprise Server account with at least one repository\.
+ You must have network or virtual private cloud \(VPC\) that you have already configured\.
+ You must have already created your instance and, if you plan to connect with your VPC, launched your instance into your VPC\.

## Connect to GitHub Enterprise Server using the CodeGuru Reviewer console<a name="create-new-ghe-connection"></a>

If you need to access a GitHub Enterprise Server repository in an account that you have not connected with CodeGuru Reviewer before, create a new connection to associate the repository\.

1. On the CodeGuru console **Associate repository** page, choose **GitHub Enterprise Server** as the source provider\. Then choose **Create a GitHub Enterprise Server Connection**\.  
![\[Choose a source provider on the Associate repository page\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. On the **Create a connection** page, if you have not created a host, choose **Create host** and follow the steps at [Create a host](https://docs.aws.amazon.com/dtconsole/latest/userguide/connections-host-create.html) to set up a host for your connection\. As part of this process, you log in to your GitHub Enterprise Server account, connect to the endpoint where your provider is installed, and choose to use a public network or an Amazon VPC configuration\.  
![\[Create a host from the Create a connection page\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. On the **Create a connection** page, provide a **Connection name**, choose a host, and then choose **Connect to GitHub Enterprise Server**\.

1. Proceed to Step 3: Connect to GitHub Enterprise Server of [Create a connection](https://docs.aws.amazon.com/dtconsole/latest/userguide/connections-create.html) and follow the steps there to complete the procedure\.

After you connect to GitHub Enterprise Server, proceed to [Step 3: Finish associating a repository](step-one.md#finish-associating-repository)\. 