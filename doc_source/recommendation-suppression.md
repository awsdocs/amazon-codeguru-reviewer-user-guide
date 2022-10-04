# Suppress recommendations from Amazon CodeGuru Reviewer<a name="recommendation-suppression"></a>

Whether you initiate a full repository analysis code review or an incremental code review, you can suppress recommendations from CodeGuru Reviewer\. You do this by excluding files and directories in an `aws-codeguru-reviewer.yml` file\.

By excluding files or directories, your costs associated with CodeGuru Reviewer analyzing your repository might also decrease\. For more information, see [Cost impact of suppressing recommendations](#costs-control-code-analyzed)\.

The following examples describe scenarios in which you might want to use an `aws-codeguru-reviewer.yml` file to exclude files or directories\.
+ Your repository contains directories that should not be included in a code review, such as `test`, `generated`, or `module` directories\. 
+ Your repository is a large open\-source repository and you don't want files about a feature or product inside the repository to be analyzed\. 

**Topics**
+ [Structure of the aws\-codeguru\-reviewer\.yml file](#structure-configure-file)
+ [Steps to suppress recommendations](#steps-to-suppress-recommendations)
+ [Cost impact of suppressing recommendations](#costs-control-code-analyzed)
+ [Error handling for the aws\-codeguru\-reviewer\.yml file](#error-handling-yml)

## Structure of the aws\-codeguru\-reviewer\.yml file<a name="structure-configure-file"></a>

The following content lists the criteria that your `aws-codeguru-reviewer.yml` file must meet, includes sample code that you can use as a template to create your file, and illustrates with example code snippets how to exclude files and directories\.

**Note**  
Be sure to use relative paths for files and directories that you add to your `aws-codeguru-reviewer.yml` file\.

### Criteria for the aws\-codeguru\-reviewer\.yml file<a name="criteria-configure-file"></a>

In addition to being valid YAML and not containing syntax errors, your `aws-codeguru-reviewer.yml` file must meet the following criteria\. If your file does not, then CodeGuru Reviewer returns error messages and does not use your file in any analysis\. For more information, see [Error handling for the aws\-codeguru\-reviewer\.yml file](#error-handling-yml)\.
+ File name: `aws-codeguru-reviewer.yml`
**Important**  
You must name the file `aws-codeguru-reviewer` and use the extension `.yml`, not `.yaml`\. If you don't, then CodeGuru Reviewer cannot recognize your file, use it in analyses, or return error messages about your file\. 
+ Maximum file size: 100 KB
+ Maximum length of each glob expression: 100 characters
+ Maximum number of glob expressions: 100
+ Version number: 1\.0

For more information about glob expressions, see [glob \(programming\)](https://en.wikipedia.org/wiki/Glob_(programming)) in *Wikipedia*\.

### Sample aws\-codeguru\-reviewer\.yml file<a name="sample-configure-file"></a>

You can copy the following sample YAML file content to use as a template when creating your own `aws-codeguru-reviewer.yml` file\. You can also download this sample file from the CodeGuru Reviewer console or from the [sample application repository in GitHub](https://github.com/aws-samples/amazon-codeguru-reviewer-sample-app/blob/master/aws-codeguru-reviewer.yml)\.

Replace the items under `excludeFiles:` with your own files and directories\. For information about how to exclude files and directories, see [Example code for the aws\-codeguru\-reviewer\.yml file](#example-configure-file)\. 

**Note**  
Be sure to use relative paths for files and directories that you add to your `aws-codeguru-reviewer.yml` file\.

```
version: 1.0

# Sample YAML file
# This configuration file is an optional file for Amazon CodeGuru Reviewer.
# You must name your file aws-codeguru-reviewer.yml for CodeGuru Reviewer to recognize it.
# Add the file to the root directory of your repository.
# For more information, see the Amazon CodeGuru Reviewer User Guide:
# https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/welcome.html.

# Exclude files and directories
# Use glob pattern syntax to specify the files and directories that you want to exclude 
# from analysis under excludeFiles. For more information, see glob (programming): 
# https://en.wikipedia.org/wiki/Glob_(programming).
# The following example excludes from analysis all content in the some-package directory, all content 
# in the tst directory, and all JSON files in a sub-directory under a directory prefixed with some-.
# Replace with your own list of files and directories that you want CodeGuru Reviewer to exclude.
# We recommend that you use a schema validator to confirm that the YAML syntax is valid.

excludeFiles:
  - 'src/some-package/**' 
  - 'tst/**'
  - 'src/some-*/**/*.json'
```

### Example code for the aws\-codeguru\-reviewer\.yml file<a name="example-configure-file"></a>

In your `aws-codeguru-reviewer.yml` file, add files and directories to exclude under `excludeFiles:`\. Use glob pattern syntax\. For more information about glob expressions, see [glob \(programming\)](https://en.wikipedia.org/wiki/Glob_(programming)) in *Wikipedia*\.

**Example 1: Excluding a particular directory**

In the following example, CodeGuru Reviewer excludes from analysis anything in the `resources` directory\.

```
version: 1.0

excludeFiles: 
  - 'resources/*'
```

**Example 2: Excluding files under any directory with a particular name**

In the following example, CodeGuru Reviewer excludes from analysis all files under any directory named `configuration`\.

```
version: 1.0

excludeFiles: 
  - '**/configuration/*'
```

**Example 3: Excluding all Java files**

In the following example, CodeGuru Reviewer excludes from analysis any file with a `.java` extension\.

```
version: 1.0

excludeFiles: 
  - '**/*.java'
```

## Steps to suppress recommendations<a name="steps-to-suppress-recommendations"></a>

You can add an `aws-codeguru-reviewer.yml` file to a repository either *before* or *after* you associate a repository\. For more information about associating a repository, see [Working with repository associations ](working-with-repositories.md)\.

**To suppress recommendations**

1. Create an `aws-codeguru-reviewer.yml` file\. For more information, see [Structure of the aws\-codeguru\-reviewer\.yml file](#structure-configure-file)\.

1. Add the `aws-codeguru-reviewer.yml` file to the root directory of the repository that you want CodeGuru Reviewer to analyze\.

1. For new repositories, associate the repository\. After you associate the repository, CodeGuru Reviewer automatically initiates a full repository analysis code review\. For more information, see [Working with repository associations ](working-with-repositories.md)\.

1. For repositories that have already been associated, initiate either a full repository analysis code review or an incremental code review\. For more information, see [ Create code reviews](create-code-reviews.md)\.

1. To confirm that CodeGuru Reviewer used your file for the code review, check the CodeGuru Reviewer console\.

   1. Choose **Code reviews**\. This page lists all code reviews performed\.

   1. Choose the code review that CodeGuru Reviewer just performed\. 
      + If CodeGuru Reviewer used your file in the code review, then **Success** appears under **Analysis configuration file**\.  
![\[The Details section of a code review. Success appears under Analysis configuration file.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-config-file-success.png)
      + If CodeGuru Reviewer found errors in your file, then **Error** appears under **Analysis configuration file** and a message indicating the errors appears at the top of the page\. 

        Also, **Failed** appears under **Status**, indicating that CodeGuru Reviewer did not perform a code review\.

        Fix your `aws-codeguru-reviewer.yml` file based on the error messages and then initiate a new full repository analysis\. For more information, see [Error handling for the aws\-codeguru\-reviewer\.yml file](#error-handling-yml)\. ****  
![\[The Details section of a code review. List of errors in your YAML file appears in top banner.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-config-file-error.png)
      + If CodeGuru Reviewer did not recognize your file name or find the file at the root directory of your repository, then **No file detected** appears under **Analysis configuration file**\. Your file must be named `aws-codeguru-reviewer.yml` and must exist in the root directory of your repository\. Otherwise CodeGuru Reviewer cannot recognize that the file exists, use it in code reviews, or return error messages about problems with the file\.

        Confirm the name and location of your file, make any needed changes, and then initiate a new code review\.  
![\[The Details section of a code review. No file detected appears under Analysis configuration file.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-no-file-detected.png)

1. Check **Recommendations** to confirm that the recommendations match what you expect based on the settings in your `aws-codeguru-reviewer.yml` file\.

## Cost impact of suppressing recommendations<a name="costs-control-code-analyzed"></a>

You are only charged for the lines of code that CodeGuru Reviewer analyzes\. You are not charged for the lines of code in files or directories that you exclude in your `aws-codeguru-reviewer.yml` file\. For more information, see [Amazon CodeGuru pricing](http://aws.amazon.com/codeguru/pricing/)\.

If you receive an error message about the `aws-codeguru-reviewer.yml` file, CodeGuru Reviewer did not analyze your repository and you are not charged\. For more information about error messages, see [Error handling for the aws\-codeguru\-reviewer\.yml file](#error-handling-yml)\.

## Error handling for the aws\-codeguru\-reviewer\.yml file<a name="error-handling-yml"></a>

CodeGuru Reviewer does not validate your `aws-codeguru-reviewer.yml` file, but you could receive error messages under the following situations\. 
+ When you initiate a full repository analysis code review in the console, messages about any errors appear in the CodeGuru Reviewer console\.   
![\[The Details section of a code review. List of errors in your YAML file appears in top banner.\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/code-review-config-file-error.png)
+ When you submit a pull request for the analysis configuration file, messages about any errors appear as comments in the `aws-codeguru-reviewer.yml` file\. 
+ When you initiate an incremental code review, messages about any errors appear in comments on the changed lines of code in your pull request\. 

In these situations, CodeGuru Reviewer does not review any files or directories, and you are not charged for the attempted analysis\. 