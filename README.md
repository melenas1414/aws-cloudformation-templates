**CloudFormation Templates for AWS Services**
=============================================

This repository contains a collection of CloudFormation templates for deploying various services on Amazon Web Services (AWS).

**Available Templates**
-----------------------

### 1. S3 Bucket with CloudFront and Route 53

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

### 2. ECS with Autoscaling and ELB

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