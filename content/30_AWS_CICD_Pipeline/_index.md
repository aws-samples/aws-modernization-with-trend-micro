---
title: "IaC Pipeline with Security"
chapter: false
weight: 50
pre: "<b>4. </b>"
---

### Create a CI/CD pipeline using AWS tools and integrate the Cloud One - Conformity Template Scanner into it

In the first stage, we showed how you could scan CloudFormation templates before committing a new version of the template to the code repository. Unfortunately, the developers or DevOps engineer can forget to do it and commit the CloudFormation Templates that has some issues. Now, we will be able to create a security gate to help you prevent new resources being used that do not follow best practices recommended by your organization.

This will help you to monitor and audit any new change in real-time before you deploy it in the AWS environment. 🤯

In this chapter, we will show how to use Template Scanner in the CI/CD pipeline with AWS CodeCommit, AWS CodeBuild, and AWS CodePipeline. Let’s do it 💻

Here is a little recap about the architecture that we are going to create:
![Diagram](/images/IaC_diagram.png)

----------------------------------------------------------------------------------------------------------------------

#### IaC - Pipeline with Security Creation

For this exercise we have a CloudFormation template to build for you to use:

- <b>Automated Creation</b>
    - Just go to <b>4.1 Automated Process to create the IaC pipeline with security </b> to start the automated process.