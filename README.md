# Infrastructure as code using CloudFormation

Follow below steps in order to use the AWS CloudFormation to create an application stack

## CREATE CLOUDFORMATION STACK

```
aws cloudformation create-stack \
--stack-name applicationstack \
--parameters ParameterKey=AMIIDParameter,ParameterValue=ami-01669c557a23951ba \
ParameterKey=CodeDeployS3BucketName,ParameterValue=code-deploy.floyed-pinto.me \
ParameterKey=DomainName,ParameterValue=prod.floyed-pinto.me \
ParameterKey=VPCNameParameter,ParameterValue=VPC-01 \
ParameterKey=VPCCIDRParameter,ParameterValue=10.10.0.0/16 \
ParameterKey=RouteTableNameParameter,ParameterValue=VPC-01-RT \
ParameterKey=Subnet01CidrParameter,ParameterValue=10.10.1.0/24 \
ParameterKey=Subnet01NameParameter,ParameterValue=Subnet01 \
ParameterKey=Subnet02CidrParameter,ParameterValue=10.10.2.0/24 \
ParameterKey=Subnet02NameParameter,ParameterValue=Subnet02 \
ParameterKey=Subnet03CidrParameter,ParameterValue=10.10.3.0/24 \
ParameterKey=Subnet03NameParameter,ParameterValue=Subnet03 \
ParameterKey=InternetGatewayNameParameter,ParameterValue=VPC-01-IG \
  --region us-east-1 \
  --template-body file://scalable-application.json \
--capabilities CAPABILITY_NAMED_IAM

```

### Arguments passed in the above CLI command

| ParameterKey | ParameterValue |
| --- | --- |
|AMIIDParameter | The ID of the AMI to be used to run the EC2 instances |
|CodeDeployS3BucketName | The S3 bucket name which will store the webapp and lambda function code for deployment with CodeDeploy |
|DomainName | The domain name to configure in Route53 to redirect traffic to the Load balancer |
|VPCNameParameter | Name of the VPC |
|VPCCIDRParameter | The IPv4 CIDR block for the VPC | 
|RouteTableNameParameter | Name of the Route table |
|Subnet01CidrParameter | CIDR block for Subnet 1 |
|Subnet01NameParameter | Name for Subnet 1 |
|Subnet02CidrParameter | CIDR block for Subnet 2 |
|Subnet02NameParameter |  Name for Subnet 2 |
|Subnet03CidrParameter | CIDR block for Subnet 3 |
|Subnet03NameParameter | Name for Subnet 3 |
|InternetGatewayNameParameter | Name of the Internet Gateway |

## DELETE CLOUDFORMATION STACK

```
aws cloudformation delete-stack --stack-name applicationstack
```

## WAIT FOR CLOUDFORMATION STACK DELETION

```
aws cloudformation wait stack-delete-complete --stack-name applicationstack
```
