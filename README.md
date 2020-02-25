# Infrastructure as code using CloudFormation

Follow below steps in order to use the AWS CloudFormation

## CREATE CLOUDFORMATION STACK

```
aws cloudformation create-stack \
  --stack-name demostack25 \
  --parameters ParameterKey=VPCNameParameter,ParameterValue=VPC-01 \
  --parameters ParameterKey=VPCCIDRParameter,ParameterValue=10.10.0.0/16 \
  --parameters ParameterKey=RouteTableNameParameter,ParameterValue=VPC-01-RT \
  --parameters ParameterKey=Subnet01CidrParameter,ParameterValue=10.10.1.0/24 \
  --parameters ParameterKey=Subnet01NameParameter,ParameterValue=Subnet01 \
  --parameters ParameterKey=Subnet02CidrParameter,ParameterValue=10.10.2.0/24 \
  --parameters ParameterKey=Subnet02NameParameter,ParameterValue=Subnet02 \
  --parameters ParameterKey=Subnet03CidrParameter,ParameterValue=10.10.3.0/24 \
  --parameters ParameterKey=Subnet03NameParameter,ParameterValue=Subnet03 \
  --parameters ParameterKey=InternetGatewayNameParameter,ParameterValue=VPC-01-IG \
  --region us-east-1 \
  --template-body file://network1.json

```

## DELETE CLOUDFORMATION STACK

```
aws cloudformation delete-stack --stack-name demostack25
```

## WAIT FOR CLOUDFORMATION STACK DELETION

```
aws cloudformation wait stack-delete-complete --stack-name demostack25
```
