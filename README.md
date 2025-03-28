# CloudFormation Template for Multi-AZ VPC with ECS Fargate and Blue/Green Deployment

This CloudFormation template sets up a multi-AZ VPC with private and public subnets, an Internet Gateway, a NAT Gateway, and an ECS Fargate deployment with Blue/Green deployment.

## Overview

This template creates the following resources:

* A VPC with two public and two private subnets
* An Internet Gateway and a NAT Gateway
* An ECS cluster with a Fargate task definition
* A Blue/Green deployment with CodeDeploy
* A PostgreSQL database with SSM parameter store for credentials
* CloudWatch logs for ECS tasks
* S3 bucket for storing application data

## Parameters

The template takes the following parameters:

* `AppName`: The name of the application
* `VPCCidrBlock`: The CIDR block for the VPC
* `PublicSubnet1CIDR` and `PublicSubnet2CIDR`: The CIDR blocks for the public subnets
* `PrivateSubnet1CIDR` and `PrivateSubnet2CIDR`: The CIDR blocks for the private subnets
* `AvailabilityZone1` and `AvailabilityZone2`: The availability zones for the subnets
* `DatabaseName`: The name of the PostgreSQL database
* `DatabaseUser`: The username for the PostgreSQL database
* `DatabasePassword`: The password for the PostgreSQL database
* `ECSTaskCPU` and `ECSTaskMemory`: The CPU and memory settings for the ECS task definition
* `ECSServiceDesiredCount`: The desired number of tasks in the ECS service
* `S3BucketNameSuffix`: The suffix for the S3 bucket name

## Outputs

The template outputs the following values:

* `VPCID`: The ID of the VPC
* `PublicSubnet1ID` and `PublicSubnet2ID`: The IDs of the public subnets
* `PrivateSubnet1ID` and `PrivateSubnet2ID`: The IDs of the private subnets
* `LoadBalancerDNSName`: The DNS name of the Application Load Balancer
* `ProdTargetGroupArn` and `TestTargetGroupArn`: The ARNs of the production and test target groups
* `DatabaseEndpoint`: The endpoint of the PostgreSQL database
* `DatabasePort`: The port of the PostgreSQL database
* `ECSClusterName`: The name of the ECS cluster

## Usage

To use this template, create a new CloudFormation stack and upload the template file. Fill in the required parameters and click "Create stack". The template will create all the necessary resources and configure the Blue/Green deployment.

Note: This template assumes that you have the necessary permissions to create the required resources. Make sure to review the template and understand what resources will be created before deploying it to your AWS account.