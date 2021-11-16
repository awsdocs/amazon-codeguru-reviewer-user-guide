# Encrypting a repository association in Amazon CodeGuru Reviewer<a name="encrypt-repository-association"></a>

All associated repositories in Amazon CodeGuru Reviewer are encrypted by default using a key that AWS owns and manages for you\. You can encrypt an associated repository using an AWS Key Management Service key, known as a *KMS key*, that you manage\. If you want to use a KMS key, then you must create one in advance using AWS KMS, or create one when you create your associated repository\. For more information, see [Creating keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.

You can encrypt an associated repository with a KMS key only when you create it\. If you want to update how an existing repository is encrypted, you must disassociate it and then recreate it with the encryption you want\. For more information, see [Disassociate a repository in CodeGuru Reviewer](disassociate-repository-association.md)\. 

The encryption key \(either an AWS owned and managed key, or a KMS key you create\) encrypts the associated repository and all of its code reviews\. Each code review is a child of the associated repository that contains the reviewed code\.

If you encrypt an associated repository with a KMS key, then revoke access to that key by disabling it or removing CodeGuru Reviewer's grant to AWS KMS using the AWS Identity and Access Management AWS CLI or SDK, the following occurs:
+ Recommendations related to the associated repository become unavailable\.
+ You cannot successfully review code in the associated repository\. You can schedule a code review, but the code review fails\.

To restore access to an associated repository that is encrypted with a disabled key, you can re\-enable it\. For more information, see [Enabling and disabling keys](https://docs.aws.amazon.com/kms/latest/developerguide/enabling-keys.html) in the *AWS Key Management Service Developer Guide*\.

**Note**  
Creation of an AWS KMS key results in charges to your AWS account\. For more information, see [AWS Key Management Service pricing](http://aws.amazon.com/kms/pricing)\.

**Topics**
+ [Encrypt an associated repository using an AWS KMS key](#encrypt-repository-association-how-to-use-cmk)
+ [Update how a repository association is encrypted](#encrypt-repository-association-how-to-change-cmk)

## Encrypt an associated repository using an AWS KMS key<a name="encrypt-repository-association-how-to-use-cmk"></a>

You can use the Amazon CodeGuru Reviewer console to specify an AWS Key Management Service key \(KMS key\) to encrypt your associated repository\. If you do not do this, your associated repository is encrypted by default using a key that is owned and managed by AWS\.

**Encrypt an associated repository using a KMS key**

1. Follow the steps in one of the following topics to create an association with your repository type: 
   +  [Create an AWS CodeCommit repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-codecommit-association.html#create-codecommit-association-console) 
   +  [Create a Bitbucket repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-bitbucket-association.html#create-bitbucket-association-console) 
   +  [Create a GitHub or GitHub Enterprise Cloud repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-github-association.html) 
   +  [Create a GitHub Enterprise Server repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-github-enterprise-association.html#create-github-enterprise-association-console) 

1. Expand **Additional configuration**\.

1. Select **Customize encryption settings \(advanced\)**\.

1. Do one of the following: 
   + If you already have a KMS key that you manage, enter its Amazon Resource Name \(ARN\)\. For information about finding the ARN of your key using the console, see [Finding the key ID and ARN](https://docs.aws.amazon.com/kms/latest/developerguide/find-cmk-id-arn.html) in the *AWS Key Management Service Developer Guide*\.
   + If you want to create a KMS key, choose **Create an AWS KMS key** and follow the steps in the AWS KMS console\. For more information, see [Creating keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.

1. Complete the rest of the steps to create your repository association\.

## Update how a repository association is encrypted<a name="encrypt-repository-association-how-to-change-cmk"></a>

If you want to update how your associated repository is encrypted, you must disassociate it, then recreate it\. When you recreate the associated repository, specify the AWS Key Management Service key \(KMS key\) you want to use\. If you do not specify a KMS key, then your data is encrypted by a key that is managed by AWS\.

**Change how an associated repository is encrypted**

1. Disassociate your associated repository by following the steps in [Disassociate a repository in CodeGuru Reviewer \(console\) ](disassociate-repository-association.md#disassociate-repository-association-console)\.

1. Follow the steps in one of the following topics to create an association with your repository type\. Specify the KMS key you want to use or don't specify any KMS key if you want to encrypt your data using an AWS owned and managed key\. 
   +  [Create an AWS CodeCommit repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-codecommit-association.html#create-codecommit-association-console) 
   +  [Create a Bitbucket repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-bitbucket-association.html#create-bitbucket-association-console) 
   +  [Create a GitHub or GitHub Enterprise Cloud repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-github-association.html) 
   +  [Create a GitHub Enterprise Server repository association \(console\)](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-github-enterprise-association.html#create-github-enterprise-association-console) 