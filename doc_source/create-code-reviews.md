# Create code reviews in Amazon CodeGuru Reviewer<a name="create-code-reviews"></a>

Amazon CodeGuru Reviewer uses code reviews to provide [different kinds of recommendations](recommendations.md) to help improve your code\. These recommendations are focused on best practices and resolving potential defects in code that are difficult for developers to find\. After a code review is successfully completed on a full repository analysis or incremental code review, you can view recommendations\. You can then choose whether to incorporate the recommendations, and you can provide feedback about whether the recommendations were helpful\.

If you want to suppress recommendations, you can add files and directories to an `aws-codeguru-reviewer.yml` file for CodeGuru Reviewer to exclude from analysis\. You can create this analysis configuration file and add it to the root directory of your repository at any time\. CodeGuru Reviewer uses the file for both incremental code reviews and full repository analysis code reviews, or returns errors indicating problems with the file\. For more information, see [Suppress recommendations](recommendation-suppression.md)\.

**Note**  
We recommend that you use both CodeGuru Reviewer and traditional peer review processes during the code review stage\. Using a combination of code review processes helps to identify more issues before they reach production\.

There are three different kinds of code reviews that CodeGuru Reviewer can do to provide recommendations\.
+  *Incremental code reviews* are created automatically when you create a pull request from your repository context on an associated repository\. These code reviews scan the changed code in a pull request\.
+ *Full repository analysis code reviews* scan all the code in a specified branch in the CodeGuru Reviewer console\.
+ *Full repository analysis code reviews for CI/CD workflows* scan all the source code in your CI/CD workflow\. For more information, see [Create code reviews with GitHub Actions](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/working-with-cicd.html)\.

For more information on the difference between incremental code reviews and full repository analysis code reviews, see [About full repository analysis and incremental code reviews](repository-analysis-vs-pull-request.md)\.

**Topics**
+ [Get recommendations using full repository analysis](#get-repository-scan)
+ [Get recommendations using incremental code reviews](#get-pull-request-scan)
+ [Get recommendations using GitHub Actions](#working-with-github-actions)

## Get recommendations using full repository analysis<a name="get-repository-scan"></a>

To get recommendations on all the code in a branch, associate the repository with CodeGuru Reviewer\. CodeGuru Reviewer automatically initiates a full repository analysis\. Later, to initiate a full repository analysis on\-demand, follow these steps:

1. Navigate to the **Code reviews** pane in the console\.

1. On the **Full repository analysis** tab, choose **Create full repository analysis**\.  
![\[The Code reviews section showing the Create full repository analysis button on the Full repository analysis tab.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-reviews-create-full-repo-analysis.png)

   A window opens for you to specify the location of the source code you wish to scan\.

1. On the **Create full repository analysis** page, choose the associated repository from the list, then choose the branch you want reviewed\.

1. \(Optional\) If you want to, you can provide a name for your code review\. If you don't, CodeGuru Reviewer provides a name for you that you can modify\.

1. \(Optional\) If you want to suppress recommendations, create an `aws-codeguru-reviewer.yml` file and add it to the root directory of your repository\. You can download a sample file to use as a template from the **Analysis configuration file** section\. For more information, see [Suppress recommendations](recommendation-suppression.md)\.

1. When you have specified the branch you want reviewed, choose **Create full repository analysis**\.   
![\[The Create full repository analysis section with source code settings and sample YAML file information.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/create-full-repo-analysis.png)

To view the recommendations, navigate to the **Code reviews** page in the console and choose the name of the code review to view the detailed code review page\. If you do not see the code review right away, try refreshing the page\. For more information, see [View code review details](view-code-review-details.md)\.

 If a repository contains Java and Python files, then CodeGuru Reviewer generates recommendations for the language for which there are more files\. For example, if there are five Java files and ten Python files in an associated repository, then CodeGuru Reviewer generates recommendations for the Python code and does not generate recommendations for the Java code\. If the number of Java and Python files is the same, then only Java recommendations are generated\. 

## Get recommendations using incremental code reviews<a name="get-pull-request-scan"></a>

To get recommendations from CodeGuru Reviewer for code changes in an associated repository, referred to as an incremental code review, use the repository source provider to submit a pull request\. CodeGuru Reviewer then provides recommendations to improve your code as comments on the pull request in the source provider\. 

You can also view the recommendations in the CodeGuru Reviewer console\. 

1. Navigate to the **Code reviews** pane in the console\. 

1. On the **Incremental code reviews** tab, choose the name of the code review\. 

   CodeGuru Reviewer then displays the detailed code review page that contains the list of recommendations\.

## Get recommendations using GitHub Actions<a name="working-with-github-actions"></a>

This sections shows you how to create recommendations using GitHub Actions and disassociate a workflow, and also provides examples to get your started\. 

**Topics**
+ [Create code reviews with GitHub Actions](#create-recommendations-with-github-actions)
+ [Disassociate your CI/CD workflow](#disassociate-your-workflow)
+ [GitHub Actions code review examples](#codeguru-reviewer-on-github-hosted-runner-example)

### Create code reviews with GitHub Actions<a name="create-recommendations-with-github-actions"></a>

This section shows you how to create code reviews and get recommendations using GitHub Actions\.

**To start recommendations using GitHub Actions**

1. Create an Amazon S3 bucket with the prefix **codeguru\-reviewer\-\*** to upload your code and artifacts\. For information on creating a new Amazon S3 bucket, see [Creating a bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html)\.

1. Sign into your GitHub account to complete the CI/CD integration process\. Your repository must be public or private if it's part of a GitHub organization in order for GitHub actions to work\.

1. In order to run the CodeGuru Reviewer Action, you need to provide AWS credentials\. We recommend using [aws\-actions/configure\-aws\-credentials](https://github.com/aws-actions/configure-aws-credentials) to configure your credentials for a job\. For self\-hosted runners, the `configure-aws-credentials` action assumes the runner’s IAM credentials or role to the CodeGuru Reviewer Action\. Docker must be installed for self\-hosted runners\. For information on installing Docker, see [Get started with Docker](https://docs.docker.com/get-started/)\.

   For GitHub hosted runners, you can configure the credentials in GitHub Secrets\. 

   The IAM user or IAM role should have the `AmazonCodeGuruReviewerFullAccess` policy enabled and Amazon S3 Permissions `(s3:PutObject, s3:ListBucket, s3:GetObject)`\. For more details on AWS credentials, see [Configuration and credential file settings](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)\. 

1. Add the CodeGuru Reviewer Action\. The following code snippet provides an example showing how you can enable your workflow, as supported by CodeGuru Reviewer\.

   ```
   - name: Amazon CodeGuru Reviewer Scanner
         if: ${{ always() }}
         uses: aws-actions/codeguru-reviewer@v1.1
         with:
           build_path: target # build artifact(s) directory. This is only required for Java repositories
           s3_bucket: codeguru-reviewermyactions-bucket  # S3 Bucket with "codeguru-reviewer-*" prefix
   ```

   The following is a list of parameters\.    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/create-code-reviews.html)

1. Run your workflow in GitHub to start the code analysis\. When the build is complete, review your recommendations in the GitHub **Security** tab\.

### Disassociate your CI/CD workflow<a name="disassociate-your-workflow"></a>

If your CI workflow association fails, you can disassociate your repository by choosing **Disassociate repository**\. If you want to associate your CI workflow later, you can associate your repository again by following set up steps\.

If you want to stop CodeGuru Reviewer recommendations for your CI workflow, remove the `codeguru` action script from your repository’s YML file\. Then, choose **Disassociate repository** to remove the repository association\. On your next job run, CodeGuru Reviewer associates the repository again unless you remove the `codeguru` action script from the YML file\.

### GitHub Actions code review examples<a name="codeguru-reviewer-on-github-hosted-runner-example"></a>

Run CodeGuru Reviewer Action on a GitHub hosted runner\.

```
steps:
    - name: Checkout repository
      uses: actions/checkout@v2
      with:
        fetch-depth: 0   # Required
   
    - name: Configure AWS Credentials
      uses: aws-actions/configure-aws-credentials@v1
      if: ${{ always() }} # This ensures that your workflow runs successfully
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-west-2

    - name: Amazon CodeGuru Reviewer Scanner
      uses: aws-actions/codeguru-reviewer@v1.1
      if: ${{ always() }} 
      with:
        build_path: target # build artifact(s) directory
        s3_bucket: codeguru-reviewer-my-bucket  # S3 Bucket with "codeguru-reviewer-*" prefix
    
    - name: Upload review result
      if: ${{ github.event_name != 'push' }}
      uses: github/codeql-action/upload-sarif@v1
      with:
        sarif_file: codeguru-results.sarif.json
```

Run a CodeGuru Reviewer Action on a self\-hosted runner\.

```
steps:
    - name: Checkout repository
      uses: actions/checkout@v2
      with:
        fetch-depth: 0

    - name: Configure AWS Credentials
      if: ${{ always() }} #  This ensures that your workflow runs successfully
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-region: us-west-2
        role-to-assume: my-github-actions-role

    # Refer to Step 2 for more details
    - name: Amazon CodeGuru Reviewer
      uses: aws-actions/codeguru-reviewer@v1.1
      if: ${{ always() }}
      with:          
        build_path: target # build artifact(s) directory
        s3_bucket: codeguru-reviewermy-bucket

    - name: Upload review result
      if: ${{ github.event_name != 'push' }}
      uses: github/codeql-action/upload-sarif@v1
      with:
        sarif_file: codeguru-results.sarif.json
```