# AWS Certificate Manager (ACM) 
Is a service designed to simplify the management of SSL/TLS certificates. It enables users to provision, manage, and deploy both public and private certificates for use with AWS services as well as internal resources. This service is crucial for securing network communications and establishing the identity of websites and applications.
## How AWS Certificate Manager Works
ACM automates many of the complex processes associated with SSL/TLS certificate management. Users can request certificates directly from ACM, which handles the issuance and renewal processes. The key functionalities include:
*  Certificate Issuance: Users can request Amazon-issued public certificates or import third-party certificates. ACM supports various types of certificates, including wildcard certificates that can secure multiple subdomains.
*  Automated Renewals: ACM automatically renews certificates before they expire, reducing the risk of downtime due to expired certificates.
*  Integration with AWS Services: ACM is integrated with several AWS services, such as **Elastic Load Balancing, Amazon CloudFront**, and **Amazon API Gateway**, allowing for seamless deployment of certificates on these platforms.
## Main Features of AWS Certificate Manager
1. Public and Private Certificates: ACM allows the management of both public and private SSL/TLS certificates. Public certificates are issued by Amazon, while private certificates can be created using AWS Private CA.
2. Centralized Management: Users can manage all their SSL/TLS certificates through the AWS Management Console, AWS CLI, or ACM APIs. This centralized approach simplifies certificate lifecycle management.
3. Security and Compliance: Certificates managed by ACM are stored securely using strong encryption practices. This ensures that private keys are protected, meeting compliance requirements for data encryption in transit.
4. No Additional Costs: There are no extra charges for managing SSL/TLS certificates through ACM when used with integrated AWS services. Users only pay for the AWS resources they create.
5. Domain Validation Options: To issue a certificate, ACM requires domain validation, which can be done via DNS or email methods. This ensures that the requester has control over the domain names specified.
6. Regional Resource Management: Certificates in ACM are regional resources; therefore, users must request or import a certificate for each AWS region where it will be used.
7. Export Capabilities: While ACM manages public certificates primarily within AWS services, users can export private certificates for use outside of AWS environments.
8. Support for Wildcard Certificates: Wildcard certificates can secure multiple subdomains under a single domain name, providing flexibility in managing domain security.
## Certificate services and monitoring
AWS Certificate Manager (ACM) plays a crucial role in maintaining trust and providing encryption for both internal and external infrastructure and applications. Here are the key points regarding its certificate services and monitoring.
###Key Points

- Certificate Importance: Certificates are essential for ensuring trust and encryption in applications and infrastructure.
- Managed Renewals: ACM offers managed renewals that typically automate the renewal of certificates. However, this does not apply to imported certificates, which cannot be automatically renewed.
- Monitoring Expirations: To monitor certificate expirations, ACM publishes events and metrics to Amazon CloudWatch. This data can trigger notifications via Amazon Simple Notification Service (SNS) and can be logged in AWS Security Hub.
- Consequences of Expiration: An expired certificate can lead to website or application unavailability, resulting in operational and business disruptions.
- Notification Challenges: Organizations using third-party certificates may face challenges receiving notifications about expirations, especially if those certificates are outside of the AWS account where notifications are configured.
- Regional Monitoring: Security Hub can monitor certificate expirations, but it operates at a regional level, making it cumbersome to track across multiple regions. The solution discussed consolidates notifications into a single region's findings.
### Monitoring Options
- - ACM Certificate Expiration Event:
    - Utilizes Amazon EventBridge to trigger a Lambda function when a certificate is nearing expiration.
    - The Lambda function publishes findings to Security Hub and sends notifications via SNS for email alerts or IT service management (ITSM) systems.
- - DaysToExpiry Metric:
    - A newly launched metric that allows scheduling batch searches for expiring certificates.
    - It logs all findings and sends a consolidated SNS notification for all expiring certificates.
These monitoring solutions enhance the ability to manage certificate expirations effectively, ensuring continuous security for applications and infrastructure.
## Monitoring with Lambda function and CloudWatch rules
The solution involves a Lambda function that utilizes CloudWatch rules to monitor and report on certificates nearing expiration. This function operates in two primary modes based on the type of event it receives.
### Monitoring Options
1. Time-Based Events: The Lambda function checks for all certificates with a DaysToExpiry metric when a time-based event is triggered.
2. Specific Certificate Events: When an event related to a specific certificate occurs, the function focuses on that single certificate.
In both scenarios, the findings are logged to Security Hub, and notifications are sent out via SNS (Simple Notification Service). While notifications can be sent as basic emails, integrating them into ticketing or alerting systems is recommended for better incident management.
### Option 1: CloudWatch Event for Single Certificate
A CloudWatch event from ACM signals that a certificate is approaching expiration.
The workflow is as follows:
![alt text](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2021/05/02/Monitor-expirations-ACM-1.png)
1. CloudWatch receives the event and invokes the Lambda function.
2. The function examines the specified certificate.
3. Findings are logged in Security Hub.
4. A notification with expiration details is published to an SNS topic.
5. SNS then notifies subscribers (commonly via email).
### Option 2: Scheduled CloudWatch Rule for All Certificates
This option allows for a scheduled review of all expiring certificates in ACM. The workflow includes:
![alt text](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2021/05/02/Monitor-expirations-ACM-2.png)
1. CloudWatch runs the rule on a timer and invokes the Lambda function.
2. The function identifies all certificates with a DaysToExpiry metric.
3. All expiring certificates are logged as findings in Security Hub.
4. A notification detailing all expirations is published to an SNS topic.
5. SNS sends out notifications to subscribers.
This structured approach ensures timely alerts and facilitates effective management of SSL certificate renewals.

[ACM](https://aws.amazon.com/certificate-manager/faqs/?loc=5&nc=sn)
[ACM Overview](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html)
[ACM](https://aws.amazon.com/certificate-manager/?nc1=h_ls)
[ACM User guide](https://docs.aws.amazon.com/acm/latest/userguide/gs.html)
[title](https://k21academy.com/amazon-web-services/aws-certificate-manager-acm/)
[title](https://tutorialsdojo.com/aws-certificate-manager/)
[title](https://aws.amazon.com/es/blogs/security/how-to-monitor-expirations-of-imported-certificates-in-aws-certificate-manager-acm/)
