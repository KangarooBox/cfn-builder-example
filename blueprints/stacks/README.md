# CloudFormation Stacks

This directory contains the blueprints for your CFN stacks.  Each file can generate 1 or more CFN
stacks (one per region).


## Example Stack

This stack creates an IAM Role with S3 ReadOnly access and an EC2 Security Group that allows SSH access (port 22) from anywhere on the Internet.

```
{
	"ProjectName" : "MyStack",
	"Owner"				: "My Name",
	"Template"		: "common/base-all.hbs",
	"Region"			: "us-east-1",

	"IAMRoles": [
		{	"Name": "MyRole",
			"ManagedPolicyArns": ["arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess"]
		}
	],

	"EC2SecurityGroups": [
		{	"Name": "MyGroup",
			"SecurityGroupIngress": [
				{	"IpProtocol": "tcp", "FromPort": 22, "ToPort": 22, "CidrIp": "0.0.0.0/0" }
			],
			"SecurityGroupEgress": [
				{ "IpProtocol": "tcp", "CidrIp": "0.0.0.0/0" }
			]
		}
	]
}
```