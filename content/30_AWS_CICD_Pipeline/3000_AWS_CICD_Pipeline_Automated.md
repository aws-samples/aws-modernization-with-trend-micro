---
title: "Automated Process to create IaC pipeline with Security"
chapter: false
weight: 51
pre: "<b>4.1 </b>"
---

### Using the CloudFormation Template to build the IaC pipeline in you AWS account

Here is the link to the GitHub Repository with the CloudFormation template to build the IaC architecture into your AWS account -> [GitHub Repository](https://github.com/fernandostc/AWS_IaC_pipeline_with_Security)


![Automated](/images/aws_cicd_pipeline.png)

Let's build the CloudFormation template:

#### Create Stack

**1.** Click on the button below to deploy the stack in AWS CloudFormation

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ModernizationWorkshop&templateURL=https://aws-and-trendmicro-modernization-workshop.s3.amazonaws.com/cloudformation_automated_iac.yml)

{{% notice note %}}
<p style='text-align: left;'>
Make sure you are using the <b>us-east-1</b> in AWS. If you are using a different region to deploy the CloudFormation template, please use the proper Image ID from the region that you are using.
This CloudFormation template has some dependencies with us-east-1. 
</p>
{{% /notice %}}

If you want to check the CloudFormation Template content click on the link here to easily see the file on GitHub GIST: [GitHub Gist Link](https://gist.github.com/fernandostc/be67b1a0be68c4f53968e3e7ad82f84a)

---

**2.** On this page click on the **Next** button 
![create1](/images/create_stack1.PNG)

---

**3.** Most of the parameters are pre-configured already, but you still need to define the <b>Stack name</b> and the <b>Cloud One - Conformity API Key</b>.

- <b>Stack name</b>: <code>ModernizationWorkshop</code>

- <b>Cloud One - API Key</b>: Check out [Creating API Key](/20_ide_plugin.html#enabling-the-api-token-to-scan-aws-cloudformation-templates-on-the-ide) for an explanation on how to get the API Key in the Cloud One Console through User Management. 

After filling up the two fields missing information click <b>Next</b>
![create2](/images/create_stack2.png)

---

**4.** Click <b>Next</b> again
![create3](/images/create_stack3.png)

---

**5.** After, you will need to scroll down to acknowledge that AWS will be creating an AWS Identity and Access Management (IAM) resource for the roles and policies needed for the lab. Next, click on <b>Create stack</b>
![create4](/images/create_stack4.png)

---

**6.** After creating the stack, you will be able to play with the CloudFormation example in the CodeCommit repository.
![create5](/images/create_stack5.png)

---

**7.** Now, let’s see how the first IaC pipeline execution goes with the CloudFormation example that you will have in the CodeCommit. 

- Search for <b>CodePipeline</b> on AWS console
- Click on the icon, and you will see a pipeline failed like the image below. 
- Then click on the Pipeline Name 

![create6](/images/create_stack_add_detail.png)

![create6](/images/create_stack6.png)

---

**8.** The first release that automatically kicked-off failed. To see more details, click <b>Details</b> on the <b>Test stage</b>, then click <b>Link to Execution</b>.

![create7](/images/create_stack7.png)

![create8](/images/create_stack8.png)

---

**9.** Conformity has generated findings as an artifiact for the failed build, you will see more information about the build stage of the template scanner following the steps below: 

- Click the <b>Build details</b> tab, scroll down to <b>Artifacts</b>
- After click the <b>artifact link</b> that was uploaded to the Amazon Simple Storage Service (S3) bucket.

![create9](/images/create_stack9.png)

![create10](/images/create_stack10.png)

---

**10.** You can download the latest file to see the results by <b>selecting the artifact</b> and click in the button <b>Download</b>. You will need to unzip the file and you will see the following information as a JSON format:

{{% notice note %}}
<p style='text-align: left;'>
If the file downloaded doesn't have the zip extension, please add .zip to the file and unzip it.
</p>
{{% /notice %}}

![create10](/images/create_stack_add_detail_2.png)

```
INFO: Obtaining required environment variables...
INFO: All environment variables were received. The pipeline will fail if any "HIGH" level issues are found
INFO: Offending entries:
[
    {
        "attributes": {
            "categories": [
                "security"
            ],
            "compliances": [
                "GDPR",
                "AWAF",
                "NIST4",
                "NIST5",
                "NIST-CSF",
                "ISO27001",
                "HIPAA",
                "HITRUST",
                "PCI",
                "APRA",
                "FEDRAMP",
                "MAS",
                "CSA"
            ],
            "cost": 0,
            "descriptorType": "s3-bucket",
            "ignored": false,
            "last-updated-date": null,
            "logicalResourceId": "S3Bucket",
            "message": "Bucket S3Bucket does not enforce Server-Side Encryption",
            "not-scored": false,
            "pretty-risk-level": "High",
            "provider": "aws",
            "region": "us-east-1",
            "resolution-page-url": "https://www.cloudconformity.com/knowledge-base/aws/S3/server-side-encryption.html",
            "resource": "S3Bucket",
            "risk-level": "HIGH",
            "rule-title": "Server Side Encryption",
            "status": "FAILURE",
            "tags": [
                "Environment::ModernizationWorkshop"
            ],
            "waste": 0
        },
        "id": "ccc:OrganisationId:S3-016:S3:us-east-1:S3Bucket",
        "relationships": {
            "account": {
                "data": null
            },
            "rule": {
                "data": {
                    "id": "S3-016",
                    "type": "rules"
                }
            }
        },
        "type": "checks"
    },
    {
        "attributes": {
            "categories": [
                "security"
            ],
            "compliances": [
                "GDPR",
                "AWAF",
                "NIST4",
                "NIST5",
                "NIST-CSF",
                "ISO27001",
                "HIPAA",
                "HITRUST",
                "ASAE-3150",
                "PCI",
                "APRA",
                "FEDRAMP",
                "MAS",
                "CSA"
            ],
            "cost": 0,
            "descriptorType": "s3-bucket",
            "ignored": false,
            "last-updated-date": null,
            "logicalResourceId": "S3Bucket",
            "message": "Bucket S3Bucket doesn't have encryption enabled",
            "not-scored": false,
            "pretty-risk-level": "High",
            "provider": "aws",
            "region": "us-east-1",
            "resolution-page-url": "https://www.cloudconformity.com/knowledge-base/aws/S3/bucket-default-encryption.html",
            "resource": "S3Bucket",
            "risk-level": "HIGH",
            "rule-title": "S3 Bucket Default Encryption",
            "status": "FAILURE",
            "tags": [
                "Environment::ModernizationWorkshop"
            ],
            "waste": 0
        },
        "id": "ccc:OrganisationId:S3-021:S3:us-east-1:S3Bucket",
        "relationships": {
            "account": {
                "data": null
            },
            "rule": {
                "data": {
                    "id": "S3-021",
                    "type": "rules"
                }
            }
        },
        "type": "checks"
    },
    {
        "attributes": {
            "categories": [
                "security"
            ],
            "compliances": [],
            "cost": 0,
            "descriptorType": "s3-bucket",
            "extradata": [
                {
                    "label": "LocationConstraint",
                    "name": "LocationConstraint",
                    "type": "META",
                    "value": "us-east-1"
                }
            ],
            "ignored": false,
            "last-updated-date": null,
            "logicalResourceId": "S3Bucket",
            "message": "s3-bucket S3Bucket does not have S3 Block Public Access feature enabled.",
            "not-scored": false,
            "pretty-risk-level": "Very High",
            "provider": "aws",
            "region": "global",
            "resolution-page-url": "https://www.cloudconformity.com/knowledge-base/aws/S3/bucket-public-access-block.html",
            "resource": "S3Bucket",
            "risk-level": "VERY_HIGH",
            "rule-title": "Enable S3 Block Public Access for S3 Buckets",
            "status": "FAILURE",
            "tags": [
                "Environment::ModernizationWorkshop"
            ],
            "waste": 0
        },
        "id": "ccc:OrganisationId:S3-026:S3:global:S3Bucket",
        "relationships": {
            "account": {
                "data": null
            },
            "rule": {
                "data": {
                    "id": "S3-026",
                    "type": "rules"
                }
            }
        },
        "type": "checks"
    }
]
CRITICAL: 3 offending entries found
```


---

**11.** You can see that you have <b>three misconfigurations</b> that are not meeting the minimum risk level that we defined as <b>HIGH</b> during the IaC pipeline creation. 
Keep in mind that you can change the risk level configuration anytime that you need. 

For this case, we are going to do the fix direct in the CodeCommit where our CloudFormation template is, but in real life, you will be able to share the details above with your cloud architect team and DevOps engineers to improve the CloudFormation before pushing it to the code repository.

Let's do the fixes in the CloudFormation then. :computer:
Search for <b>CodeCommit</b> and then click the <b>CloudFormationRepo</b> that was created by the CloudFormation template earlier.
Click on <b>cloudformation.yml</b> and then click <b>Edit</b> - you will see the following CloudFormation template for us to fix:

![create11](/images/create_stack11_updated.PNG)

---

**12.** You will need to update the current CloudFormation template that you have with the new one that we updated below. This new CloudFormation has the goal to fix the two <b>HIGH</b> issues found by the Conformity Template Scanner.


{{% notice note %}}
<p style='text-align: left;'>
The Image ID used is from us-east-1 in AWS. If you are using a different region to deploy the CloudFormation template, please use the proper Image ID from the region that you are using.
</p>
{{% /notice %}}

---

**13.** Copy and paste this new CloudFormation template in your environment:

```
Resources:
  Ec2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      InstanceType: t3.micro
      SecurityGroups:
      - Ref: InstanceSecurityGroup
      ImageId: resolve:ssm:/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2
      Tags:
        - 
          Key: "Environment"
          Value: "ModernizationWorkshop"
  InstanceSecurityGroup:
    Type: 'AWS::EC2::SecurityGroup'
    Properties:
      GroupDescription: Enable SSH access via port 22 test 
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
      Tags:
       - 
          Key: "Environment"
          Value: "ModernizationWorkshop"
  S3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      PublicAccessBlockConfiguration:
        BlockPublicAcls: true
        BlockPublicPolicy: true
        IgnorePublicAcls: true
        RestrictPublicBuckets: true
      BucketEncryption: 
        ServerSideEncryptionConfiguration: 
        - ServerSideEncryptionByDefault:
            SSEAlgorithm: AES256
      Tags:
        - 
          Key: "Environment"
          Value: "ModernizationWorkshop"
```

{{% notice note %}}
<p style='text-align: left;'>
In the new CFT we added two configurations to fix the issue "BucketEncryption" and "PublicAccessBlockConfiguration".
</p>
{{% /notice %}}


---

**14.** Now you will just need to add the information requested for the commit and click in <b>Commit Changes</b>, this way the pipeline will kick-off automatically because of the changes happening:


![create12](/images/create_stack12.PNG)

---

**15.** Go to <b>Pipelines</b> on the left under <b>CodePipeline</b> and select the <b>ModernizationWorkshop</b> pipeline to see the stages:

![create13](/images/create_stack13.png)

---

**16.** Now, you will see that the CloudFormation template passed in the Template Scanner analysis and it was able to be built in AWS :rocket: 
Congratulations, you have a simple, fully automated IaC with security scanning for your Cloud Formation templates before building the infrastructure.


![create14](/images/create_stack14.png)

---------------------


{{% notice note %}}
<p style='text-align: left;'>
The CloudFormation template will be creating a Amazon S3 bucket, a security group, and an Amazon Elastic Compute Cloud (EC2). You can go to the CloudFormation stack and delete the stack that we just created: <b>modernization-workshop-cft-example</b>
</p>
{{% /notice %}}

![create14](/images/create_stack_add_detail_3.PNG)

{{% notice warning %}}
<p style='text-align: left;'>
If you are using your own account, remember to delete the CloudFormation created with the name <b>modernization-workshop-cft-example</b> for you don't spend unnecessary money.
</p>
{{% /notice %}}


Now, you can skip to the <b>Lab 5. Integrating AWS with Cloud One - Conformity </b> :computer: :rocket:
