# S3_CDK
Create an S3 Bucket using CDK with AWS CodeWhisperer.

## Pre-requisites and Setting Up
Make the directory in your github repository and navigate to it.

```bash
mkdir hello-cdk
cd hello-cdk
```

Make sure you have the AWS CDK installed. If not, you can install it using the following command:
```bash
python -m pip install aws-cdk-lib
```

Then, you're going to need to download node.js and npm. You can do this by going to the following link and downloading the latest version of node.js and npm:
[https://nodejs.org/en](https://nodejs.org/en). Here, you can download the version that is used the most by users. 
Follow all the installation instructions and then check if the installation was successful by running the following commands: 
```bash
node -version
npm -version
```
Then, you're going to need to install the AWS CDK Toolkit. You can do this by running the following command:
```bash
sudo npm install -g aws-cdk
```
To ensure that the installation was successful, run the following command:
```bash
cdk --version
```
Next, we initialize the CDK project by running the following command:
```bash
cdk init app --language python
```

Then you need to create a virtual environment by running the following command:
```bash
source .venv/bin/activate
```
And then install all the dependencies required for the project by running the following command:
```bash
python -m pip install -r requirements.txt
```

## Setting up your IAM User:
You need to create an IAM user with the following permissions:
- AmazonS3FullAccess
- AWSAmazonElasticContainerRegistryPublicFullAccess	
- AWSCloudFormationFullAccess	
- AWSSystemsManagerForSAPFullAccess	
- IAMFullAccess	
- IAMUserChangePassword
Furthermore to ensure that the user has the necessary permissions, you need to attach the following policies to the user using the 'Create inline policy' option after creating the user and adding this to the JSON file:
```json

{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "VisualEditor0",
			"Effect": "Allow",
			"Action": [
				"s3:ListAccessPointsForObjectLambda",
				"s3:GetAccessPoint",
				"s3:PutStorageLensConfiguration",
				"iam:CreateRole",
				"iam:AttachRolePolicy",
				"iam:PutRolePolicy",
				"cloudformation:CreateChangeSet",
				"s3:ListStorageLensGroups",
				"ssm:GetParameter",
				"ecr:DeleteRepository",
				"iam:PassRole",
				"ssm:DeleteParameter",
				"iam:DetachRolePolicy",
				"cloudformation:DescribeStackEvents",
				"iam:DeleteRolePolicy",
				"s3:ListAccessGrantsInstances",
				"ecr:DescribeRepositories",
				"cloudformation:DescribeChangeSet",
				"cloudformation:ExecuteChangeSet",
				"iam:GetRole",
				"ecr:PutLifecyclePolicy",
				"s3:PutAccountPublicAccessBlock",
				"s3:ListAccessPoints",
				"ecr:CreateRepository",
				"s3:ListJobs",
				"s3:CreateStorageLensGroup",
				"iam:DeleteRole",
				"ssm:GetParameters",
				"s3:ListMultiRegionAccessPoints",
				"cloudformation:DescribeStacks",
				"ssm:PutParameter",
				"s3:ListStorageLensConfigurations",
				"s3:GetAccountPublicAccessBlock",
				"s3:ListAllMyBuckets",
				"cloudformation:GetTemplate",
				"cloudformation:DeleteStack",
				"ecr:SetRepositoryPolicy",
				"s3:PutAccessPointPublicAccessBlock",
				"s3:CreateJob"
			],
			"Resource": "*"
		},
		{
			"Sid": "VisualEditor1",
			"Effect": "Allow",
			"Action": [
				"s3:PutEncryptionConfiguration",
				"s3:PutBucketPublicAccessBlock",
				"s3:*",
				"s3:PutBucketPolicy",
				"s3:CreateBucket",
				"s3:DeleteBucketPolicy",
				"s3:DeleteBucket",
				"s3:PutBucketVersioning"
			],
			"Resource": "arn:aws:s3:::*"
		}
	]
}   
```


## Synthesizing and Deploying your CDK Stack
First, you need to synthesize the CDK app to make sure that there are no errors in the code. Synthesizing the CDK app will generate a CloudFormation template that represents the resources that will be created when the CDK app is deployed.
To synthesize the CDK app, run the following command:
```bash
cdk synth
```

Then, you are ready to deploy your app. To deploy the CDK stack, run the following command:
```bash
cdk bootstrap
```
This command will create a CloudFormation stack that contains the resources required to deploy the CDK app. Is successful, it will display the following message:
<img width="1200" alt="image" src="https://github.com/AaryaDesai1/S3_CDK/assets/143753050/6e235613-38ba-4463-b6d2-1280da5c9e04">

Once the stack is created, you can deploy the CDK app by running the following command:
```bash
cdk deploy
```
When you successfully deploy the CDK app, you will see the following message:
<img width="913" alt="image" src="https://github.com/AaryaDesai1/S3_CDK/assets/143753050/6758c31f-1269-4ffb-a452-ae5e5a317ecc">

## Making sure the S3 Bucket is created
To check if the S3 bucket is created, go to the AWS Management Console and navigate to the S3 service. You should see the S3 bucket that was created by the CDK app.
It should look like this:
<img width="1346" alt="image" src="https://github.com/AaryaDesai1/S3_CDK/assets/143753050/43f2ee94-eab9-4e54-85b6-29cef8588fc6">