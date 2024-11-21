# Endpoint for Amazon S3
Amazon has introduced a new feature called VPC Endpoint for Amazon S3, which enhances the integration between Amazon Virtual Private Cloud (VPC) and Amazon Simple Storage Service (S3). This feature simplifies access to S3 resources from within a VPC, allowing for a more secure and efficient connection without the need for an Internet Gateway or NAT instances.
Key Points

1. VPC Overview: Amazon VPC allows users to create a logically isolated section of the AWS Cloud, providing complete control over the virtual network configuration, including security groups and access control lists (ACLs) to manage traffic.
2. Simplified Access: The introduction of VPC Endpoints enables EC2 instances located in private subnets to access S3 buckets and objects securely. This access is controlled by S3 bucket policies that specify which VPCs and VPC Endpoints can access the resources.
3. Configuration: Users can create and configure VPC Endpoints through various AWS interfaces, including the AWS Management Console, AWS CLI, and VPC API. The process involves selecting the desired VPC and customizing the access policy for the endpoint.
4. Access Control: By default, a VPC Endpoint can access any S3 bucket. However, users can restrict this access further by implementing specific access policies on both the VPC Endpoint and the S3 buckets using conditions like aws:SourceVpc and aws:SourceVpce.
5. Impact on Connections: When a VPC Endpoint is created, any open connections using an instance's public IP address in the affected subnets will be dropped. Nevertheless, existing S3 public endpoints and DNS names will continue to function normally.
6. Availability: The new VPC Endpoints for Amazon S3 are currently available in multiple regions, including US East (N. Virginia), US West (Oregon), Europe (Ireland), and Asia Pacific (Tokyo).

This feature aims to enhance security and efficiency for organizations utilizing AWS services by providing a direct, private connection to S3 without traversing public networks.

## Creating and Using VPC Endpoints
You can create and configure VPC Endpoints using the AWS Management Console, AWS Command Line Interface (AWS CLI), AWS Tools for Windows PowerShell, and the VPC API. Let’s create one using the console! Start by opening up the VPC Dashboard and selecting the desired region. Locate the Endpoints item in the navigation bar and click on it:

![alt text](https://media.amazonwebservices.com/blog/2015/vpc_endpoints_menu_1.png)

If you have already created some VPC Endpoints, they will appear in the list:

![alt text](https://media.amazonwebservices.com/blog/2015/vpc_endpoints_list_1.png)

Now click on Create Endpoint, choose the desired VPC, and customize the access policy (if you want):
![alt text](https://media.amazonwebservices.com/blog/2015/vpc_config_endpoint_5.png)
The access policy on the VPC Endpoint allows you disallow requests to untrusted S3 buckets (by default a VPC Endpoint can access any S3 bucket). You can also use access policies on your S3 buckets to control access from a specific VPC or VPC Endpoint. These access policies would use the new aws:SourceVpc and aws:SourceVpce conditions 
As you might be able to guess from the screen above, you will eventually be able to create VPC Endpoints for other AWS services!

Now choose the VPC subnets that will be allowed to access the endpoint:

![alt text](https://media.amazonwebservices.com/blog/2015/vpc_config_endpoint_routes_2.png)

open connections using an instance’s public IP address in the affected subnets will be dropped when you create the VPC Endpoint.

Once you create the VPC Endpoint, the S3 public endpoints and DNS names will continue to work as expected. The Endpoint simply changes the way in which the requests are routed from EC2 to S3.
