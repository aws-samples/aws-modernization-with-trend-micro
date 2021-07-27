---
title: "IDE Security Plugin"
chapter: false
weight: 40
pre: "<b>3. </b>"
---

### Install the Security plugin in the IDE 

First you will need to install the VSCode IDE in your machine to install the Cloud Conformity Security Plugin as you can see here: [Link](https://marketplace.visualstudio.com/items?itemName=raphaelbottino.cc-template-scanner)

- Click on **Install** after opening the link from Cloud Conformity Plugin provide above and it will automatically download the plugin for the Visual Studio Code in your machine that you have installed in the Prequisites session:

![IDE1](/images/IDE1.png)


### Enabling the API Token to scan AWS CloudFormation Templates on the IDE

Second you will need to create one account in Conformity using this link here [Create Account](https://cloudone.trendmicro.com/SignUp.screen#), login into your account, and generate an API Token.

Log in to Trend Micro <b>Cloud One Platform</b>:

1. Click in <b>Conformity</b> service
2. Click the <b>Username</b> on the top right
3. Then click in <b>User Settings</b>
4. Click <b>API Keys</b> on the left
5. Finally click in <b>New API Key</b> to create one to be used in the VSCode plugin.

Remember to copy the key and save it safely. You won't be able to get it again.

![API](/images/API.png)

#### Copy the API Key and go back to VSCode IDE 💻

1. Click on the <b>Extensions</b> icon (left side) and click in <b>Extension Settings</b> ⚙️ for the Cloud Conformity Template Scanner entry.
2. Select edit in <b>settings.json</b> on the <b>Cc: ApiKey</b> section.
3. Input the <b>API Key</b> you generated on the previous step and save.

![API2](/images/API2.png)

Now you will be able to scan the CloudFormation templates based on hundreds of checks that help you comply with the AWS Well-Architected Framework among others standards and frameworks to ensure you are building superior cloud infrastructure.
Here is one example of a <b>bad</b> CloudFormation template <b>NOT</b> following the engineering best practices for you to test:

{{% notice note %}}
<p style='text-align: left;'>
Copy the CloudFormation template example below and save the file with the YAML format (.yml).
If you do not save the file, the template scanner will fail.
</p>
{{% /notice %}}


```
#This is an CloudFormation template example NOT following the AWS Well-Architected Framework  

Resources:
  Ec2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      SecurityGroups:
        - !Ref InstanceSecurityGroup
      KeyName: ec2-keypair
      ImageId: ami-0ff8a91507f77f867
      Tags:
        - 
          Key: "Environment"
          Value: "TM_Lab"
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
          Value: "TM_Lab"
  S3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: test-tm-lab-s3-bucket
      Tags:
        - 
          Key: "Environment"
          Value: "TM_Lab"
```

To test the extension, open the CloudFormation template above with the VSCode IDE and open the Command Pallet with:

    - MAC OS: ⇧ + ⌘ + P
    - Windows/Linux: Ctrl+Shift+P

Search for <b>Cloud One Conformity: Scan the Current Open Template</b> and hit **enter** to start automatically scanning your CloudFormation template:

![IDE3](/images/IDE3.png)

**The result will appear in a second tab called Scan Result like the image below.**

You can also check out the Conformity [Knowledge Base](https://www.cloudconformity.com/knowledge-base/aws/), which can help you better understand more about any best practice check violations and how to remediate and fix them in your CloudFormation template or in production environments:

![IDE4](/images/IDE4.png)

Awesome the first stage for an IaC Security automation is done. 😃🤖💻
------