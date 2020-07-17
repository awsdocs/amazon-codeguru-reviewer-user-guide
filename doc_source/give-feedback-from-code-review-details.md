# View recommendations and provide feedback<a name="give-feedback-from-code-review-details"></a>

After you access the detailed code review page by choosing the name of the code review from the **Code reviews** page, you can view the recommendations from the code review directly in the console\. 

You can also leave feedback on the recommendations by choosing the thumbs\-up or thumbs\-down icon\. Providing feedback can improve the quality of recommendations CodeGuru Reviewer provides for your code, making CodeGuru Reviewer increasingly effective in later analyses\.

![\[The Code review details window in the CodeGuru Reviewer console\]](http://docs.aws.amazon.com/codeguru/latest/reviewer-ug/)

You can also use the AWS CLI or the AWS SDK to provide feedback on recommendations\. If you have the code review ARN, you can call `ListRecommendations`\. This returns the list of all recommendations for a completed code review\. You can then use `PutRecommendationFeedback` to store reactions and send feedback as UTF\-8 text code for emojis\. 

To view the feedback that you have submitted, call `DescribeRecommendationFeedback` using the `RecommendationId`\. To view feedback from all users, call `ListRecommendationFeedback` by using a filter on `RecommendationIds` and `UserIds`\. For more information, see the [Amazon CodeGuru Reviewer API Reference](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/Welcome.html)\.

Your feedback is used to improve CodeGuru Reviewer through model\-tuning efforts that will help make CodeGuru Reviewer recommendations more useful to you and others\.