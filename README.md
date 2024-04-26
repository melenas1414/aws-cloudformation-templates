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