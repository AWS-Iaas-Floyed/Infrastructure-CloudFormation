# Infrastructure as code using CloudFormation

Follow below steps in order to use the AWS CloudFormation

## CREATE CLOUDFORMATION STACK

```
aws cloudformation create-stack \
  --stack-name csye6225demo \
  --parameters ParameterKey=InstanceTypeParameter,ParameterValue=t2.micro \
  --template-body file://networking.json
```

## DELETE CLOUDFORMATION STACK

```
aws cloudformation delete-stack --stack-name csye6225demo
```

## WAIT FOR CLOUDFORMATION STACK DELETION

```
aws cloudformation wait stack-delete-complete --stack-name csye6225demo
```
