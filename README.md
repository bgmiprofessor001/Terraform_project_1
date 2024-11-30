Terraform Project: AWS VPC with Application Load Balancer and EC2 Instances

This Terraform configuration deploys a highly available web application infrastructure on AWS. It creates a Virtual Private Cloud (VPC) with subnets, security groups, EC2 instances, and an Application Load Balancer (ALB). Additionally, it provisions an S3 bucket and outputs the ALB DNS name for easy access.

Architecture Overview
The setup includes:

A VPC with two public subnets in different availability zones.
An Internet Gateway for public internet access.
An ALB to distribute traffic across two EC2 instances.
Security groups to allow HTTP and SSH traffic.
An S3 bucket for storing artifacts or logs.


Resources Created
Networking
VPC
CIDR Block: var.cidr


Subnets
sub1: 10.0.0.0/24, AZ: us-east-1a
sub2: 10.0.1.0/24, AZ: us-east-1b

Internet Gateway
Attached to the VPC

Route Table
Routes all internet-bound traffic to the IGW

Security
Security Group (webSg)
Allows inbound HTTP (port 80) and SSH (port 22) traffic from anywhere
Allows all outbound traffic
EC2 Instances

Web Server 1
AMI: ami-005fc0f236362e99f
Instance Type: t2.micro
User Data Script: userdata.sh

Web Server 2
AMI: ami-005fc0f236362e99f
Instance Type: t2.micro
User Data Script: userdata1.sh

Application Load Balancer
ALB (myalb)
Public-facing
Spanning both subnets
Target Group (myTG)
Health Check: path = "/"

Storage
S3 Bucket
Name: adityaterraform2024project
