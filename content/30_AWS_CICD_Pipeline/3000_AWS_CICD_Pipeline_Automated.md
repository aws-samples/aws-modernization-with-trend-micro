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

Go to AWS Console and search for CloudFormation and after click in <b>Create Stack</b>

![create](/images/create_stack.png)

Save the CloudFormation template provided in the Git Repository before, or you can use the GIST link here to easily get the file: [GitHub Gist Link](https://gist.github.com/fernandostc/be67b1a0be68c4f53968e3e7ad82f84a)

After upload the CloudFormation template to AWS click in <b>Next</b>
![create1](/images/create_stack1.png)

Most of the parameters are pre-configured already, but you still need to define the <b>Stack name</b> and the <b>Cloud One - Conformity API Key</b>.

- <b>Stack name</b>: ModernizationWorkshop

- <b>Cloud One - Conformity API Key</b>: Check out <b>Lab 3</b> for an explanation on how to get the API Key in the Conformity console

After filling up the two fields missing information click <b>Next</b>
![create2](/images/create_stack2.png)

Click <b>Next</b> again
![create3](/images/create_stack3.png)

After, you will need to scroll down to acknowledge that AWS will be creating an AWS Identity and Access Management (IAM) resource for the roles and policies needed for the lab. Next, click on <b>Create stack</b>
![create4](/images/create_stack4.png)


After creating the stack, you will be able to play with the CloudFormation example in the CodeCommit repository.
![create5](/images/create_stack5.png)

Now, let’s see how the first IaC pipeline execution with the CloudFormation example that you will have in the CodeCommit:
![create6](/images/create_stack6.png)

The first release that automatically kicked-off failed. To see more details, click <b>Details</b> on the <b>Test stage</b>, then click <b>Link to Execution</b>.

![create7](/images/create_stack7.png)

![create8](/images/create_stack8.png)

You will see more information about the build stage of the template scanner. Now, you will need to click the <b>Build details</b> tab, scroll down to <b>Artifacts</b>, and click the <b>artifact link</b> that was uploaded to the Amazon Simple Storage Service (S3) bucket.

![create9](/images/create_stack9.png)

![create10](/images/create_stack10.png)

You can download the latest file to see the results by clicking <b>Actions</b> and then <b>Download</b>. You will need to unzip the file and you will see the following information as a JSON format:

{{% notice note %}}
<p style='text-align: left;'>
If the file downloaded doesn't have the zip extension, please add .zip to the file and unzip it.
</p>
{{% /notice %}}

        INFO: Obtaining required environment variables...
        INFO: All environment variables were received. The pipeline will fail if any "HIGH" level issues are found
        INFO: Offending entries:
        [
            {
                "attributes": {
                    "categories": [
                        "security"
                    ],
                    "cost": 0,
                    "descriptorType": "s3-bucket",
                    "ignored": false,
                    "last-updated-date": null,
                    "message": "Bucket S3Bucket doesn't have encryption enabled",
                    "not-scored": false,
                    "pretty-risk-level": "High",
                    "provider": "aws",
                    "region": "us-east-1",
                    "resource": "S3Bucket",
                    "risk-level": "HIGH",
                    "rule-title": "S3 Bucket Default Encryption",
                    "status": "FAILURE",
                    "tags": [
                        "Environment::ModernizationWorkshop"
                    ],
                    "waste": 0
                },
                "id": "ccc:AccountId:S3-021:S3:us-east-1:S3Bucket",
                "relationships": {
                    "account": {
                        "data": {
                            "id": "AccountId",
                            "type": "accounts"
                        }
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
                    "cost": 0,
                    "descriptorType": "s3-bucket",
                    "extradata": [],
                    "ignored": false,
                    "last-updated-date": null,
                    "message": "s3-bucket S3Bucket does not have S3 Block Public Access feature enabled.",
                    "not-scored": false,
                    "pretty-risk-level": "Very High",
                    "provider": "aws",
                    "region": "global",
                    "resource": "S3Bucket",
                    "risk-level": "VERY_HIGH",
                    "rule-title": "Enable S3 Block Public Access for S3 Buckets",
                    "status": "FAILURE",
                    "tags": [
                        "Environment::ModernizationWorkshop"
                    ],
                    "waste": 0
                },
                "id": "ccc:AccountId:S3-026:S3:global:S3Bucket",
                "relationships": {
                    "account": {
                        "data": {
                            "id": "AccountId",
                            "type": "accounts"
                        }
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
        CRITICAL: 2 offending entries found

You can see that you have <b>two misconfigurations</b> that are not meeting the minimum risk level that we defined as <b>HIGH</b> during the IaC pipeline creation. 
Keep in mind that you can change the risk level configuration anytime that you need. 

For this case, we are going to do the fix direct in the CodeCommit where our CloudFormation template is, but in real life, you will be able to share the details above with your cloud architect team and DevOps engineers to improve the CloudFormation before pushing it to the code repository.

Let's do the fixes in the CloudFormation then. :computer:
Search for <b>CodeCommit</b> and then click the <b>CloudFormationRepo</b> that was created by the CloudFormation template earlier.
Click on <b>cloudformation.yml</b> and then click <b>Edit</b> - you will see the following CloudFormation template for us to fix:


![create11](/images/create_stack11.png)

You will need to add the following line to fix the two <b>HIGH</b> issues found by the Conformity Template Scanner. Add the code below after line 29:

      BucketEncryption: 
        ServerSideEncryptionConfiguration: 
        - ServerSideEncryptionByDefault:
            SSEAlgorithm: AES256
      PublicAccessBlockConfiguration:
        BlockPublicAcls: true
        BlockPublicPolicy: true
        IgnorePublicAcls: true
        RestrictPublicBuckets: true

{{% notice warning %}}
<p style='text-align: left;'>
Recommendation: Change the Amazon S3 bucket name to a unique name — since it's a global resource, it cannot have a duplicated name.
</p>
{{% /notice %}}


{{% notice note %}}
<p style='text-align: left;'>
The Image ID used is from us-east-1 in AWS. If you are using a different region to deploy the CloudFormation template, please use the proper Image ID from the region that you are using.
</p>
{{% /notice %}}

After adding the lines above your CloudFormation template, it should look like this:

        Resources:
        Ec2Instance:
            Type: 'AWS::EC2::Instance'
            Properties:
            SecurityGroups: 
            - Ref: InstanceSecurityGroup
            ImageId: ami-0742b4e673072066f
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
            BucketName: test-modernizationworkshop
            BucketEncryption: 
                ServerSideEncryptionConfiguration: 
                - ServerSideEncryptionByDefault:
                    SSEAlgorithm: AES256
            PublicAccessBlockConfiguration:
                BlockPublicAcls: true
                BlockPublicPolicy: true
                IgnorePublicAcls: true
                RestrictPublicBuckets: true
            Tags:
                - 
                Key: "Environment"
                Value: "ModernizationWorkshop"


Now you will just need to add the information requested for the commit and click in <b>Commit Changes</b>, this way the pipeline will kick-off automatically because of the changes happening:


![create12](/images/create_stack12.png)

Go to <b>Pipelines</b> on the left under <b>CodePipeline</b> and select the <b>ModernizationWorkshop</b> pipeline to see the stages:

![create13](/images/create_stack13.png)

Now, you will see that the CloudFormation template passed in the Template Scanner analysis and it was able to be built in AWS :rocket: 
Congratulations, you have a simple, fully automated IaC with security scanning for your Cloud Formation templates before building the infrastructure.


![create14](/images/create_stack14.png)

---------------------


{{% notice note %}}
<p style='text-align: left;'>
The CloudFormation template will be creating a Amazon S3 bucket, a security group, and an Amazon Elastic Compute Cloud (EC2). You can go to the CloudFormation stack and delete the stack that we just created: <b>modernization-workshop-cft-example</b>
</p>
{{% /notice %}}


Now, you can skip to the <b>Lab 5. Integrating AWS with Cloud One - Conformity </b> :computer: :rocket:
