---
title: "AWS IAM - lab"
chapter: false
weight: 82
pre: "<b>7.2 </b>"
---

### Scenario

In this scenario, we have a use case where a customer accidentally created an IAM role policy that is overly permissive. Our goal here is to detect the IAM role and fix it so it only grants access to those who absolutely need it. 

![scenario2](/images/scenario2.png)


#### 1. Log in to Trend Micro Cloud One, choose Conformity, select the account on your left that you have integrated for this workshop, and then click Browser All Checks

![la2_s3](/images/lab_s3_1.png)

#### 2. Click Filter checks to open the filter options so we can enable an easy way to investigate some checks for AWS IAM

![la2_s3](/images/lab_s3_2.png)

#### 3. Define the Filter check

Here are the configurations that you should apply

- On <b>Services</b>, search for <b>IAM</b> and press <b>Enter</b>
- On <b>Search Tags</b>, add <b>Lab::3</b> and press <b>Enter</b>
- On <b>Status</b>, uncheck <b>Success</b>

After you complete configurations, click Filter Check again.

![la3_iam](/images/lab_iam_3.png)


#### 4. How to look for the specific Conformity check to properly perform remediation

Locate the Conformity check that pertains to the misconfiguration of this scenario ([IAM Role Policy Too Permissive](https://www.cloudconformity.com/knowledge-base/aws/IAM/iam-role-policy-too-permissive.html)). Next to it, select <b>Resolve</b>, which will populate the step-by-step instructions for remediating this misconfiguration.  

Clicking the (+) icon on the left side of the Conformity checks will allow you to see more details about the discovered misconfiguration. It also provides direct link to the resource to help you to review and fix it.

![la2_s3](/images/lab_iam_4.png)

#### 5. Remediation 

Clicking <b>Resolve</b> will bring you to the Knowledge Base where you will find step-by-step instructions on how to remediate the misconfiguration found by Conformity. In this case, you will find multiple use cases for remediation so you can choose the best approach based on your least privilege access strategy for giving users permission to resources in the cloud.

- IAM Role Policy Too Permissive - [Knowledge Base Link](https://www.cloudconformity.com/knowledge-base/aws/IAM/iam-role-policy-too-permissive.html)

For this lab you can apply Case C in the Knowledge Base:

![la2_s3](/images/lab_iam_6.png)

#### 6. Review the remediation guide

After completing the remediation for those two use cases, you can return to the Conformity dashboard and click <b>Run Conformity Bot</b> to run a new process.

The default Conformity process for monitoring is hourly checks performed by the Conformity bot. You can also manually run the checks or enable the real-time monitoring feature.  

After couple minutes the Conformity Bot check will finish and you can check if the previous configuration will now appear as <b>Succeeded</b> instead of <b>Failed</b>. 

![la2_s3](/images/lab_s3_7.png)
