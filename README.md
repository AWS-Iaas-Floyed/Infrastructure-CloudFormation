# Infrastructure as code using CloudFormation

Follow below steps in order to use the AWS CloudFormation to create an application stack

## CREATE CLOUDFORMATION STACK

```
aws cloudformation create-stack \
--stack-name applicationstack1 \
--parameters ParameterKey=AMIIDParameter,ParameterValue=ami-01669c557a23951ba \
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
  --template-body file://application.json \
--capabilities CAPABILITY_NAMED_IAM

```

## DELETE CLOUDFORMATION STACK

```
aws cloudformation delete-stack --stack-name applicationstack1
```

## WAIT FOR CLOUDFORMATION STACK DELETION

```
aws cloudformation wait stack-delete-complete --stack-name applicationstack1
```
