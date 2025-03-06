# CloudFormation AD Integration

This repository contains a CloudFormation template for integrating with Active Directory.

## Template Description

The `cloud_formation.template` file is a CloudFormation template that sets up a Windows web stack without an Elastic Load Balancer (ELB). The template includes parameters, mappings, conditions, and resources required to launch and configure the stack.

## Parameters

- **AdminListString**: Space-separated list of groups or users to add as local admins.
- **AppName**: Unique name of the application.
- **DomainJoinUsername**: Account with rights to join computers to the domain.
- **AppServerPort**: Port the application is listening on.
- **Creator**: Creator of the EC2 instance.
- **VpcId**: VPC ID to be launched in.
- **DomainJoinPassword**: Password for the account with rights to join computers to the domain.
- **APPSVCAccountUsername**: Account for the SVC account under which the app pool is running.
- **APPSVCAccountPassword**: Password for the SVC account under which the app pool is running.
- **Envname**: Environment name (dev, tst, prd).
- **KeyName**: Name of an existing EC2 KeyPair to enable SSH access to the web server.
- **BuildNumber**: Build number.
- **AZs**: Availability zones for the instances.
- **InstanceType**: EC2 instance type.
- **AmiId**: AMI ID for building the EC2 instance.

## Mappings

- **DNSServersByAZEnvname**: DNS servers by availability zone and environment name.
- **MapByEnvname**: Environment-specific configurations such as tags, security groups, and S3 buckets.
- **AppSubnetByAZEnvname**: Subnets by availability zone and environment name.
- **XAppSubnetByAZEnvname**: Additional subnets by availability zone and environment name.
- **AZnames**: Availability zone names and lists.

## Conditions

- **EncryptEbs**: Condition to determine if EBS volumes should be encrypted based on the environment name.

## Resources

- **ELBSecGroup**: Security group for the ELB.
- **ELB**: Elastic Load Balancer configuration.
- **AppInstanceCondition**: Wait condition for the application instance.
- **EC2LaunchConfiguration**: Launch configuration for the EC2 instances.
- **AppInstanceHandle**: Wait condition handle for the application instance.

## Usage

To use this template, create a new CloudFormation stack and upload the `cloud_formation.template` file. Provide the required parameters and launch the stack.

## License

This project is licensed under the MIT License.
