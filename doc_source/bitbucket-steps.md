# Connect to Bitbucket to associate a repository with CodeGuru Reviewer<a name="bitbucket-steps"></a>

You can connect to Bitbucket using an AWS CodeStar connection\. This enables you to associate repositories in a Bitbucket account with CodeGuru Reviewer to receive [recommendations](recommendations.md) for improvements in your Java code\.

## What are connections and app installations in CodeGuru Reviewer?<a name="about-connections"></a>

To access Bitbucket repositories and get recommendations from CodeGuru Reviewer, you need to set up connections and app installations through AWS CodeStar connections\. An *app installation* is a feature that allows AWS CodeStar connections to create connections to a single Bitbucket account\. A *connection* is a feature that uses an app installation through AWS CodeStar connections to connect a CodeGuru Reviewer account to a Bitbucket account\. 

If you're using a single Bitbucket account among multiple users in your organization, you can create multiple connections using the same app installation, and adjust permissions on the connections level\. 

To use a new Bitbucket account on your CodeGuru Reviewer account, you need to create a new connection\. When you create a new connection, if you need to, you can create a new app installation\.

## Create a new connection to Bitbucket<a name="create-new-bitbucket-connection"></a>

If you need to access Bitbucket repositories in a Bitbucket account that you have not connected with CodeGuru Reviewer before, you need to create a new connection\.

1. On the CodeGuru console **Associate repository** page, choose **Bitbucket** as the source provider\. Then choose **Create a Bitbucket connection**\.  
![\[Choose a source provider on the Associate repository page\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

   A window opens to confirm that you want to create a connection to Bitbucket\.

1. On the **Create a connection** page, provide a **Connection name**, and then choose **Connect to Bitbucket Cloud**\.   
![\[Provide a connection name\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

   A window opens for you to log in to Bitbucket\.

1. In the Bitbucket login window, enter your information to log in to Bitbucket\.  
![\[Log in to Bitbucket\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

   A window opens for authorization to grant access for AWS CodeStar connections to your Bitbucket account\.

1. On the **Confirm access to your account** page, choose **Grant access**\.   
![\[Grant access to Bitbucket for AWS CodeStar connections to create a connection\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

   A window opens with the Bitbucket connection settings\.

1. On the **Connect to Bitbucket Cloud** page, if you have an app installation set up, choose it from the **Bitbucket Cloud apps** list\. If you need to create a new app installation, choose **Install a new app**\.  
![\[Search the Bitbucket Cloud apps list or install a new app\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. If you are installing a new app, a window opens for Bitbucket authorization to grant access for AWS CodeStar connections\. On the **AWS CodeStar requests access** page, choose **Grant access** to allow AWS CodeStar connections to find the connection in Bitbucket Cloud\.  
![\[Grant access to AWS CodeStar connections to create a new app installation\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

1. When you have installed and chosen the app connection you want in the **Connect to Bitbucket Cloud** window, choose **Connect**\. 

After you create a connection to Bitbucket, return to the CodeGuru Reviewer console [**Associate repository** page](https://console.aws.amazon.com/codeguru/reviewer/#/configure), and then choose the connection name from the **Connect to Bitbucket \(with AWS CodeStar connections\)** list\. Then proceed to [Step 3: Finish associating a repository](step-one.md#finish-associating-repository)\. 