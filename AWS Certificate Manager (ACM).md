# AWS Certificate Manager (ACM) 
Is a service designed to simplify the management of SSL/TLS certificates. It enables users to provision, manage, and deploy both public and private certificates for use with AWS services as well as internal resources. This service is crucial for securing network communications and establishing the identity of websites and applications.
## How AWS Certificate Manager Works
ACM automates many of the complex processes associated with SSL/TLS certificate management. Users can request certificates directly from ACM, which handles the issuance and renewal processes. The key functionalities include:

*  Certificate Issuance: Users can request Amazon-issued public certificates or import third-party certificates. ACM supports various types of certificates, including wildcard certificates that can secure multiple subdomains.
*  Automated Renewals: ACM automatically renews certificates before they expire, reducing the risk of downtime due to expired certificates.
*  Integration with AWS Services: ACM is integrated with several AWS services, such as **Elastic Load Balancing, Amazon CloudFront**, and **Amazon API Gateway**, allowing for seamless deployment of certificates on these platforms.

Main Features of AWS Certificate Manager

1. Public and Private Certificates: ACM allows the management of both public and private SSL/TLS certificates. Public certificates are issued by Amazon, while private certificates can be created using AWS Private CA.
2. Centralized Management: Users can manage all their SSL/TLS certificates through the AWS Management Console, AWS CLI, or ACM APIs. This centralized approach simplifies certificate lifecycle management.
3. Security and Compliance: Certificates managed by ACM are stored securely using strong encryption practices. This ensures that private keys are protected, meeting compliance requirements for data encryption in transit.
4. No Additional Costs: There are no extra charges for managing SSL/TLS certificates through ACM when used with integrated AWS services. Users only pay for the AWS resources they create.
5. Domain Validation Options: To issue a certificate, ACM requires domain validation, which can be done via DNS or email methods. This ensures that the requester has control over the domain names specified.
6. Regional Resource Management: Certificates in ACM are regional resources; therefore, users must request or import a certificate for each AWS region where it will be used.
7. Export Capabilities: While ACM manages public certificates primarily within AWS services, users can export private certificates for use outside of AWS environments.
8. Support for Wildcard Certificates: Wildcard certificates can secure multiple subdomains under a single domain name, providing flexibility in managing domain security.

- https://aws.amazon.com/certificate-manager/faqs/?loc=5&nc=sn
- https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html
- https://aws.amazon.com/certificate-manager/?nc1=h_ls
- https://docs.aws.amazon.com/acm/latest/userguide/gs.html
- https://k21academy.com/amazon-web-services/aws-certificate-manager-acm/
- https://tutorialsdojo.com/aws-certificate-manager/
- https://aws.amazon.com/es/blogs/security/how-to-monitor-expirations-of-imported-certificates-in-aws-certificate-manager-acm/
