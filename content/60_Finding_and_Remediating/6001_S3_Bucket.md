---
title: "Amazon S3 - lab"
chapter: false
weight: 81
pre: "<b>7.1 </b>"
---

### Scenario

In this scenario we have a use case where a customer accidentally created a bucket and made it public without encryption. Our goal here is to detect the bucket and fix its two main configuration security issues.

![scenario1](/images/scenario1.png)

### Automatically Finding the Misconfiguration

{{% notice warning %}}
<p style='text-align: left;'><b>
It's very important you completed chapter 5 of the workshop before starting this one, because you will need a Trend Micro Cloud One account that is integrated with your AWS account.
</b></p>
{{% /notice %}}

We will use the Confomirty dashboard to search for the misconfigurations.

#### 1. Log in to Trend Micro - Cloud One, select Conformity, select the account on your left that you have integrated for this workshop, and then click on "Browser All Checks"

![la2_s3](/images/lab_s3_1.png)

#### 2. Click Filter checks to open the filter options so we can enable an easy way to investigate some checks for Amazon S3 buckets.

![la2_s3](/images/lab_s3_2.png)

#### 3. Define the Filter check

Here are the configurations that you should apply:

- On <b>Resource Types</b>, search for S3 Bucket and press <b>Enter</b>
- On <b>Search Tags</b>, add <b>Lab::2</b> and press <b>Enter</b>
- On <b>Status</b>, uncheck <b>Success</b>

After you complete the configurations, click <b>Filter Check</b> again

![la2_s3](/images/lab_s3_3.png)

#### 4. How to look for the specific Conformity check to properly perform remediation

Locate the two Conformity checks that pertain to the misconfigurations of this scenario ([S3 Bucket Public Access Via Policy](https://www.cloudconformity.com/knowledge-base/aws/S3/s3-bucket-public-access-via-policy.html#102741628407) and [Server Side Encryption](https://www.cloudconformity.com/knowledge-base/aws/S3/server-side-encryption.html#102741628407)). Next to each, select <b>Resolve</b>, which will populate the step-by-step instructions for remediating these misconfigurations.  

![la2_s3](/images/lab_s3_4.png)

#### 5. View more details about the the Conformity checks

Selecting the Conformity checks will allow you to see more details about the misconfiguration that was found. You will also have the direct link to the resource to help you to review and fix the misconfigurations that have been found.

![la2_s3](/images/lab_s3_5.png)

#### 6. Remediation 

Click Resolve to bring you to the Knowledge Base, here you will find the step-by-step on how to remediate the misconfiguration found by Conformity.

- [S3 Bucket Public Access Via Policy - Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/S3/s3-bucket-public-access-via-policy.html#102741628407)
- [Server Side Encryption - Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/S3/server-side-encryption.html#102741628407)

![la2_s3](/images/lab_s3_6.png)

#### 7. Review the remediation  

After completing the remediation for these two use cases, you can return to the Conformity dashboard and click <b>Run Conformity Bot</b> to start a new process. 

The default Conformity process for monitoring is hourly checks performed by the Conformity bot. You can also manually run the checks, or enable the real-time monitoring feature.  

After couple minutes the Conformity Bot check will finish and you can check if the previous configurations will now appear as <b>Succeeded</b> instead of <b>Failed</b>.

![la2_s3](/images/lab_s3_7.png)
