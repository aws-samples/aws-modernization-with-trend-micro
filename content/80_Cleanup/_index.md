---
title: "Cleanup"
chapter: false
weight: 95
pre: "<b>9. </b>"
---

### Current Stacks created in your AWS Account 

You should have all these 4 CloudFormation stacks based in the labs, now we will need to delete them:
![Cleanup](/images/cleanup.png) 

---

### CI/CD Pipeline - CloudFormation

Based in the <b>Lab 4 IaC Pipeline with Security</b> you should have two CloudFormation stacks from this lab:

1º called - <b>ModernizationWorkshop</b> or any other name that you added during the CloudFormation stack creation
2º called - <b>modernization-workshop-cft-example</b>

You will need to delete the <b>modernization-workshop-cft-example</b> stack first. After it will be completed delete the <b>ModernizationWorkshop</b> stack.

![Cleanup1](/images/cleanup1.png) 

You could go to CloudFormation console and delete those stacks through the console or using the AWS cli.

----

### Cloud One - Conformity - CloudFormation

Based in the <b>Lab 5 Integrating AWS with Conformity</b> you should have a CloudFormation stack called <b>CloudConformity</b>

You could go to CloudFormation console and delete those stacks through the console or using the AWS cli.

{{% notice note %}}
<p style='text-align: left;'>
If you keep this CloudFormation stack integrated with your account it will keep the integration with Cloud One - Conformity for you to check additional details about your environment and for you to generated additional compliance reports. The Conformity bots will be running every hour by default.
</p>
{{% /notice %}}

----

### Exercise labs - CloudFormation

Based in the <b>Lab 7 Finding and Remediating Misconfigurations</b> you should have a CloudFormation stack called <b>AWS-Modernization-Workshop-labs</b>

You could go to CloudFormation console and delete those stacks through the console or using the AWS cli.

------

Now that you deleted all the CloudFormation stacks from the labs you can test the others Cloud One sercurity services. 

---

### Unsubscribe Cloud One subscription in your AWS Account

**1.** Go to AWS account and search for AWS Marketplace Subscription.
![Cleanup](/images/unsubscribe1.png)


**2.** Find the Trend Micro Cloud One subscription and click on Manage.
![Cleanup](/images/unsubscribe2.png)


**3.** Then click Action, Cancel subscription
![Cleanup](/images/unsubscribe3.png)


**4.** You will need to check the box and click on "Yes, cancel subscription"
![Cleanup](/images/unsubscribe4.png)

**5.** You will see a confirmation message like this one, below:
![Cleanup](/images/unsubscribe5.png)

**You will see the update in the Cloud One console in around 1 to 2 hours.**