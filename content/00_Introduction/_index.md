---
title: "Introduction"
chapter: false
weight: 20
pre: "<b>1. </b>"
---

## Putting Security into The IaC Pipeline
Infrastructure-as-Code or IaC is the new normal for creating and building any new cloud environment through machine-readable files or code templates. It is important, however, to consider security in regard to the infrastructure that you may be creating to ensure it is following the best practices and compliance from your organization.

### Why IaC is the New Normal?
Physical hardware can require you to add in the rack and make the proper configuration before starting to use it, which sometimes could take weeks or months to be able to create a new server. Now with IaC, you can create a complete infrastructure for your application in the cloud in less than an hour.

Before IaC, IT teams would have to add the server into the data center manually, install operating systems (OS), and make the proper configurations before they could use it. In some cases, they would use some automated scripts to help with some tasks, but it would not make it fully automated.

With IaC, your Infrastructure takes the form of code templates. Since the code is a text file, it is easy for you to edit, copy, and share it with your team. It is recommended that you put it under source control as we do for any source code file using code repositories like GitHub, GitLab, Bitbucket, or AWS CodeCommit. Here are the three main benefits of using IaC:


![Benefits](/images/benefits.png)

- <b>Speed</b>: Enables you to quickly set up a new infrastructure by just using code or scripts.

- <b>Control</b>: Since you can view IaC template files like any other source code file, you have full traceability through code repository of the changes that each template has suffered.

- <b>Consistency</b>: Any human is susceptible to making mistakes. IaC prevents mistakes by using config files, having a single source of truth, and ensuring the same configurations for the hole environment.

Check out this informative animation video explaining IaC more in depth:

{{< youtube id="z90UOAhyHeg" title="Infrastructure as Code Explained" >}}


### Three Ways to Add Security into Your IaC Pipeline

Now that we have more information on implementing security into the CI/CD pipeline, let’s continue by discussing how to add security checks for misconfigurations in your IaC.

<i>According to Gartner, “Through 2023, at least 99% of cloud security failures will be the customer’s fault.”1 Gartner also states, “Through 2024, organizations implementing a CSPM offering and extending this into development will reduce cloud-related security incidents due to misconfiguration by 80%.” 1</i>

These statistics are mainly associated with misconfigurations in the cloud infrastructure. It is so important to have visibility and a process for real-time feedback, as it gives developers more information about the IaC before they build. Without the proper information, a developer could unknowingly start to build in a new cloud environment with security flaws that could generate a lot of headaches for your company.

![Diagram](/images/IaC_diagram.png)

Here are some tools that we will be implementing via Trend Micro Cloud One™ to help protect against misconfigurations:

1. <b>Integrated Development Environment(IDE) Security Plugin</b>
This type of plugin is designed to give real-time feedback to developers on the IaC and application development. Developers can scan and fix issues in the development environment workspace without any additional security tools to detect issues—shifting security left as far as possible.

2. <b>Template Scanner</b>
This scanner uses APIs directly within the security platform to integrate with custom tools or specific use cases in CI/CD pipelines. The scans provide real-time checks every time you push new code. The results can be shared with developers and cloud architects, providing them with the information they need to monitor any issues before going to production.

3. <b>Cloud Security Posture Management (CSPM)</b>
A security tool to detect misconfigurations in multiple cloud service providers. This technology aligns with the DevSecOps approach by integrating to help with auto-remediation capabilities in your cloud infrastructure. It can also help organizations gain a coherent picture of security and compliance risks across multi-cloud environments.

Using the above mentioned tools is important to ensure that you are creating new infrastructure in Amazon Web Services (AWS) that is following the best practices architectures based on the <b>AWS Well-Architect Framework</b>.

Now let's start implementing the first tool mentioned in the architecture above.  :man_technologist: :woman_technologist: :laptop: :cloud:


1 Gartner, Inc.; Innovation Insight for Cloud Security Posture Management; 25 January 2019 | G00377795

{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various Trend Micro - Cloud One and AWS services can be architected to build a solution while demonstrating best practices along the way.
</p>
{{% /notice %}}