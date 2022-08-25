# View all code reviews<a name="view-all-code-reviews"></a>

You can view all code reviews from the past 90 days and their statuses on the **Code reviews** page in the Amazon CodeGuru Reviewer console\. There is an **incremental code review** tab to view code reviews done on incremental code reviews and a **Full repository analysis** tab to view code reviews requested for full repository analyses\.

To learn about the types of recommendations, see [Amazon CodeGuru Reviewer Detector Library](https://docs.aws.amazon.com/codeguru/detector-library/index.html)\.

## Code reviews page<a name="about-viewing-code-reviews"></a>

To view this page, in the navigation pane, choose **Reviewer**, **Code reviews**\.

![\[The Code review page in the CodeGuru Reviewer console\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/images/codereview_repo_analysis.png)

**Note**  
After 90 days have passed since a code review was done, you can't view that code review in the Amazon CodeGuru Reviewer console\. But you might be able to view the recommendations from incremental code reviews in the repository source provider\.

To view code reviews with the AWS CLI or the AWS SDK, call `ListCodeReviews`\. You can filter using `ProviderType`, `RepositoryName`, or `State`\. For more information, see the [Amazon CodeGuru Reviewer API Reference](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/Welcome.html)\.

## Navigate to repositories and pull requests<a name="go-to-repository-and-request"></a>

From the **Code reviews** page, you can navigate to the repository or the pull request that CodeGuru Reviewer scanned\. On either the **Incremental code review** or **Full repository analysis** tab, choose a name under the **Repository** column\. 