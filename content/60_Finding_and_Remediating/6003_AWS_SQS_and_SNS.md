---
title: "AWS SQS and SNS - lab"
chapter: false
weight: 83
pre: "<b>7.3 </b>"
---

### Scenario

In this scenario, we have a use case where a customer accidentally created a SNS topic and SQS queue without encryption. Our goal here is to detect and remediate the SNS topic and SQS queue.

Here is a valuable use case from AWS about why encrypting SQS and SNS is important: [Link to AWS Blog](https://aws.amazon.com/blogs/compute/encrypting-messages-published-to-amazon-sns-with-aws-kms/)

![scenario2](/images/scenario3.png)

#### 1. Log in to Trend Micro - Cloud One,  choose Conformity, select the account on your left that you have integrated for this workshop, and then click in Browse All Checks

![la2_s3](/images/lab_s3_1.png)

#### 2. Click Filter checks to open the filter options to enable  an easy way to investigate some checks for Amazon SQS and SNS

![la2_s3](/images/lab_s3_2.png)

#### 3. Define the Filter check

Here are the configurations that you should apply:

- On <b>Resource Types</b>: search for <b>SQS Queue</b> and press <b>Enter</b>
- On <b>Resource Types</b>: search for <b>SNS Topic</b> and press <b>Enter</b>
- On <b>Search Tags</b>: add <b>Lab::4</b> and press <b>Enter</b>
- On <b>Status</b>: uncheck <b>Success</b>

After you complete configurations, click <b>Filter Check</b> again

![la3_iam](/images/lab_sqs_3.png)


#### 4. How to look for the specific Conformity check to properly perform remediation

Locate the Conformity checks that pertains to the misconfigurations of this scenario ([SNS Topic Encrypted](https://www.cloudconformity.com/knowledge-base/aws/SNS/server-side-encryption.html#102741628407) and [Queue Server Side Encryption](https://www.cloudconformity.com/knowledge-base/aws/SQS/server-side-encryption.html#102741628407)). Next to each, select <b>Resolve</b>, which will populate the step-by-step instructions for remediating these misconfiguration.  

Clicking the <b>(+)</b> icon on the left side of the Conformity checks allows you to see more details about the discovered misconfiguration. It will also provide the direct link to the resource to help you to review and fix it.

![la2_s3](/images/lab_sqs_4.png)

#### 5. Remediation 

Clicking <b>Resolve</b> button will bring you to the Knowledge Base where you will find step-by-step instructions on how to remediate the misconfiguration found by Conformity.

- SNS Topic Encrypted - [Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/SNS/server-side-encryption.html#102741628407)
- Queue Server Side Encryption - [Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/SQS/server-side-encryption.html#102741628407)

![la2_s3](/images/lab_sqs_6.png)

#### 6. Review the remediation  

After completing the remediation for those two use cases, you can return to the Conformity click <b>Run Conformity Bot</b> to start a new process.

The default Conformity process for monitoring is hourly checks performed by the Conformity bot. You can also manually run the checks or enable the real-time monitoring feature.  

After couple minutes the Conformity Bot check will finish and you can check if the previous configurations will now appear as <b>Succeeded</b> instead of <b>Failed</b>.

![la2_s3](/images/lab_s3_7.png)
