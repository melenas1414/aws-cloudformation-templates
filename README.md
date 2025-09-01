**CloudFormation Templates for AWS Services**
=============================================

This repository contains a collection of CloudFormation templates for deploying various services on Amazon Web Services (AWS).

**Available Templates**
-----------------------

> **🔒 Security Enhancement:** The "secure" templates include additional security features like AWS Origin Access Control (OAC), comprehensive error handling, and enhanced S3 privacy controls. Both versions are fully functional - choose based on your security requirements.

### 1. S3 Bucket with CloudFront (Secure)

* **Template:** `s3-cloudfront-secure.yaml`
* **Description:** Deploys a private S3 bucket with CloudFront distribution using Origin Access Control (OAC) for enhanced security.
* **Parameters:**
	+ `S3BucketName`: The name of the S3 bucket to create
	+ `ErrorPagePath`: Path to the error page for 4xx and 5xx errors (default: /index.html)
* **Resources:**
	+ Private S3 bucket with public access blocked
	+ CloudFront distribution with Origin Access Control
	+ Custom error page handling for all HTTP error codes
	+ S3 bucket policy allowing only CloudFront access

### 2. S3 Bucket with CloudFront and Route 53 (Secure)

* **Template:** `s3-cloudfront-route53-secure.yaml`
* **Description:** Deploys a private S3 bucket with CloudFront distribution and Route 53 DNS using Origin Access Control (OAC) for enhanced security.
* **Parameters:**
	+ `S3BucketName`: The name of the S3 bucket to create
	+ `HostedZoneName`: The name of the Route 53 hosted zone
	+ `HostedZoneId`: The ID of the Route 53 hosted zone
	+ `CertificateArn`: The ARN of the SSL certificate to use (must be in us-east-1)
	+ `SubdomainName`: The subdomain name for the CloudFront distribution
	+ `ErrorPagePath`: Path to the error page for 4xx and 5xx errors (default: /index.html)
* **Resources:**
	+ Private S3 bucket with public access blocked
	+ CloudFront distribution with Origin Access Control and custom domain
	+ Route 53 CNAME record for custom domain
	+ Custom error page handling for all HTTP error codes
	+ S3 bucket policy allowing only CloudFront access

### 3. S3 Bucket with CloudFront

* **Template:** `s3-cloudfront.yaml`
* **Description:** Deploys an S3 bucket with CloudFront distribution for static website hosting.
* **Parameters:**
	+ `S3BucketName`: The name of the S3 bucket to create
* **Resources:**
	+ S3 bucket with CloudFront distribution

### 4. S3 Bucket with CloudFront and Route 53

* **Template:** `s3-cloudfront-route53.yaml`
* **Description:** Deploys an S3 bucket with a CloudFront distribution and a Route 53 alias record.
* **Parameters:**
	+ `S3BucketName`: The name of the S3 bucket to create
	+ `HostedZoneName`: The name of the Route 53 hosted zone
	+ `HostedZoneId`: The ID of the Route 53 hosted zone
	+ `CertificateArn`: The ARN of the SSL certificate to use
	+ `SubdomainName`: The subdomain name for the CloudFront distribution
* **Resources:**
	+ S3 bucket with CloudFront distribution and Route 53 alias record

### 5. ECS with Autoscaling and ELB

* **Template:** `ecs-autoscaling-elb.yaml`
* **Description:** Deploys an ECS cluster with autoscaling and an Elastic Load Balancer (ELB).
* **Parameters:**
	+ `VpcId`: The ID of the VPC where the resources will be created
	+ `PrivateSubnet1` and `PrivateSubnet2`: The IDs of the private subnets where the resources will be created
	+ `PublicSubnet1` and `PublicSubnet2`: The IDs of the public subnets where the resources will be created
	+ `ECRRepositoryArn`: The ARN of the ECR repository containing the Docker image to deploy
	+ `ServiceName`: The name of the service to deploy
	+ `TaskName`: The name of the task to deploy
	+ `ClusterName`: The name of the ECS cluster to use for the service
	+ `PortMappings`: The port mappings for the container
	+ `ECSClusterId`: The ID of the ECS cluster
	+ `CertificateArn`: The ARN of the SSL certificate to use
	+ `LogsGroup`: The name of the CloudWatch Logs group to use for the container
	+ `CPU` and `Memory`: The CPU and memory settings for the task
* **Resources:**
	+ ECS cluster with autoscaling and ELB
	
**Adding New Templates**
----------------------

As new templates are added to this repository, their descriptions will be listed above. If you'd like to contribute a new template, please submit a pull request!

**Usage**
---------

1. Clone this repository to your local machine.
2. Choose the template you want to use and customize the parameters as needed.
3. Run the following command to deploy the template: `aws cloudformation deploy --template-file <template-name>.yaml --stack-name <stack-name> --capabilities CAPABILITY_IAM`
4. Wait for the stack to complete deployment.

**License**
---------

This repository is licensed under the GPL3 License. See `LICENSE` for details.