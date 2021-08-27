---
title: "Finding and Remediating Misconfigurations"
chapter: false
weight: 80
pre: "<b>7. </b>"
---

### Use cases of possible cloud misconfiguration and how to fix it

We have prepared a CloudFormation template with some common use cases of misconfiguration for main AWS services that we see in many customers. This way you will be able to run the template in your own AWS account for some practice, or you could deploy the template in an AWS account provided for a lab purpose at a Security Immersion Day event. Here are some the use cases that we created for you:

1.  <b>Amazon S3 Bucket</b>
    - Amazon S3 Bucket Publix Access Via Policy
    - Amazon S3 Server Side Encryption

2.  <b>AWS Identity and Access Management (IAM)</b>
    - Overly Permissive IAM Role

3.  <b>Amazon Simple Queue Service (SQS) and Amazon Simple Notification Service (SNS)</b>
    - Unencrypted SQS queue
    - SNS Topics Disable

:warning: **For the these labs above you will need to deploy this CloudFormation stack, below:**

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=AWS-Modernization-Workshop-labs&templateURL=https://trend-aws-security-immersion-day.s3.amazonaws.com/template.json)

or 

You can get the CloudFormation Template for the labs using this [Link](https://trend-aws-security-immersion-day.s3.amazonaws.com/template.json)

---

#### Populating the AWS account with misconfigurations for the labs

- Back in your AWS account, go to the [AWS Cloud Formation console](https://console.aws.amazon.com/cloudformation/)

- Select <b>Create stack</b> and then <b>With new resources</b> from the drop-down menu
![Populating_AWS](/images/populating.png)

- Use the following CloudFormation template link to create the stack in the AWS account: https://trend-aws-security-immersion-day.s3.amazonaws.com/template.json

- Paste the link into <b>Amazon S3 URL</b> field and click <b>Next</b>:
![Populating_AWS_2](/images/populating2.png)

- Set up the name of the CloudFormation stack as <b>AWS-Modernization-Workshop-labs</b>
![Populating_AWS_3](/images/populating3_new.png)

- Click <b>Next</b>
![Populating_AWS_4](/images/populating4.png)

- Scroll down, check the box to acknowledge and then click <b>Create stack</b>
![Populating_AWS_5](/images/populating5.png)

- After a couple of minutes, the stack will be completed, and you will be able to start the labs
![Populating_AWS_6](/images/populating6_new.png)

{{% notice note %}}
<p style='text-align: left;'>
Because we are not using the Realtime monitoring in Cloud One - Conformity in this lab will be important to manually force a Conformity check scan to recognize all the new resource created from the CloudFormation template. If not it will take a couple of minutes to run the hourly Conformity check.  
</p>
{{% /notice %}}

- Log in  Cloud One account, select Conformity, select your AWS account on the left side, and then click on Run Conformity Bot. It will force a full Conformity check in your AWS account. 

![la2_s3](/images/run_scan.png)

----------------------------------------------------------------------------------------------------------------------

#### Extra Lab - Scanning CloudFormation Template with some misconfigurations

-  <b>Scanning IaC CloudFormation template and fixing it</b>
    - Enable Amazon S3 Block Public Access for Amazon S3 buckets
    - Amazon S3 Bucket Default Encryption
    - Amazon S3 Bucket Logging Enabled
    - VPC Flow Logs Enabled

:warning: For the template scanner you will need to download this CloudFormation template to use in your IDE for the exercise ->  <b>[LINK](https://trend-aws-security-immersion-day.s3.amazonaws.com/lab5.template.yaml) </b>

:warning: <b>This is a great challenge for you to learn more about how to see misconfigurations in the early stage of the IaC pipeline with our IDE Security Plugin.</b>

---

Let's start remediating the misconfiguration issues in the AWS Account. :laptop: