# Aws Getting Started

## Create VPC, Public Subnets and Private Subnets
#### VPC
1. Your VPCs -> Create VPC 
2. Create VPC
3. VPC Settings
```
Name tag: americano-vpc
IPv4 CIDR Block: 10.0.0.0/16
IPv6 CIDR block: No IPv6 CIDR block
Tenancy: Default
```

#### Public Subnets
Create 3 public subnets in 3 availability zones

1. Subnets -> Create subnet
2. Create subnet
3. VPC:
```
VPC ID: americano-vpc
```
4. Subnet settings:
```
Subnate name: americano-public-subnet-a
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2a
IPv4 CIDR block: 10.0.0.0/24
```
5. Press "Create subnet" button
6. Create another 2 subnets
7. Create subnet
8. VPC:
```
VPC ID: americano-vpc
```
9. Subnet settings:
```
Subnate name: americano-public-subnet-b
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2b
IPv4 CIDR block: 10.0.1.0/24
```
10. Press "Create subnet" button
11. Create subnet
12. VPC: 
```
VPC ID: americano-vpc
```
13. Subnet settings:
```
Subnate name: americano-public-subnet-c
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2c
IPv4 CIDR block: 10.0.1.0/24
```
14. Press "Create subnet" button

#### Private Subnets
Create 3 private subnets in 3 availability zones

1. Subnets -> Create subnet
2. Create subnet
3. VPC: 
```
VPC ID: americano-vpc
```
4. Subnet settings:
```
Subnate name: americano-private-subnet-a
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2a
IPv4 CIDR block: 10.0.100.0/24
```
5. Press "Create subnet" button
6. Subnets -> Create subnet
7. Create subnet
8. VPC: 
```
VPC ID: americano-vpc
```
9. Subnet settings:
```
Subnate name: americano-private-subnet-c
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2b
IPv4 CIDR block: 10.0.101.0/24
```
10. Press "Create subnet" button
11. Subnets -> Create subnet
12. Create subnet
13. VPC: 
```
VPC ID: americano-vpc
```
14. Subnet settings:
```
Subnate name: americano-private-subnet-c
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2c
IPv4 CIDR block: 10.0.102.0/24
```
15. Press "Create subnet" button

## Create Internet Gateways, Route Tables and NAT Gateways
#### Internet Gateways
Public subnet can communicate with internet and internet can access instances inside public subnet

1. Internet Gateways -> Create internet gateway
2. Create internet gateway
```
Internet gateway settings
Name tag:  americano-vpc-ig
```
3. Press "Create internet gateway" button
4. Attach to a VPC / Action -> Attach to VPC / Select ig-cafeamericano-vpc from the table, Click Action -> Attach to VPC
```
Attach to VPC (igw-<id>)
```
```
VPC
Available VPCs: americano-vpc
```
5. Press "Attach internet gateway" button

#### Route Tables
Create route table for internet gateway

1. Route Tables -> Create route table
2. Create route table
```
Name tag: americano-public-route
VPC: americano-vpc
```
3. Press "Create", then "Close" button
4. Select americano-public-route row from the list
5. Click Subnet Associations tab
6. Click "Edit subnet associations" button
7. Select all public subnets, i.e. americano-public-subnet-a, americano-public-subnet-b and americano-public-subnet-c
8. Then press "Save" button
9. Select Routes tab
10. Select "Edit routes" -> Add route
```
Destination: 0.0.0.0/0
Target: americano-vpc-ig
```
11. Press "Save routes" button
12. Then "Close" button

#### NAT Gateways
Private subnet can go through internet

1. NAT Gateways -> Create NAT gateway
2. Create NAT gateway
```
NAT gateway settings
Name: americano-nat-gateway
Subnet: americano-public-subnet-a (One of the public subnet)
Elastic IP allocation ID: Press Allocate Elastic IP button
```
3. Press Create NAT gateway button
4. Then go to Route Tables page
5. Route Tables -> Create route table
```
Create route table
Name tag: americano-nat-gateway-route
VPC: americano-vpc
```
6. Press "Create", then "Close" button
7. Select americano-nat-gateway-route row from the list
8. Click Subnet Associations tab
9. Click "Edit subnet associations" button
10. Select all private subnets, i.e. americano-private-subnet-a, americano-private-subnet-b and americano-private-subnet-c
11. Then press "Save" button
12. Select Routes tab
13. Select "Edit routes" -> Add route
```
Destination: 0.0.0.0/0
Target: americano-nat-gateway
```
14. Press "Save routes" button
15. Then "Close" button

## Create Security Groups
Create 3 security groups

1. Create security groups
2. Basic details
```
Security group name: americano-bastion-sg
Description: Bastion server security group
VPC: americano-vpc
```
3. Inbound rules
4. Press Add rule button
```
Type: SSH
IP: 0.0.0.0/0
```
5. Click "Create security group" button
6. Create security groups
7. Basic details
```
Security group name: americano-web-servers-sg
Description: Web servers security group
VPC: americano-vpc
```
8. Click "Create security group" button
9. Create security groups
10. Basic details
```
Security group name: americano-postgres-sg
Description: Postgres database security group
VPC: americano-vpc
```
11. Inbound rules
12. Press Add rule button
```
Type: PostgreSQL
Source: americano-bastion-security-group
```
13. Press Add rule button
```
Type: PostgreSQL
Source: americano-web-servers-security-group
```
14. Click "Create security group" button


## Configure RDS with Postgres
1. Sign in to the AWS Management Console.
2. Go to the Services dropdown menu at the top left corner
3. Choose RDS from the menu
4. Select Subnet Groups at the left menu
5. Select Create DB Subnet Group
```
Create DB Subnet Group:
Subnet group details:
Name: americano-private-subnets
Description: Americano private database subnet group
VPC: americano-vpc
Add subnets:
Availability Zones: ap-southeash-2a, ap-southeast-2b, ap-southeast-2c
Subnets: 10.0.100.0/24, 10.0.101.0/24, 10.0.102.0/24
```
6. Click Create button
7. Select Databases at the left menu
8. Select Create database button
9. Create database:
```
Choose a database creation method: Select Standard create

Engine options
Engine type: Select PostgreSQL
Version: Latest (PostgreSQL 12.4-R1)

Templates: Free tier

Settings:
DB instance identifier:
Credentials Settings:
Master username: postgres
Auto generate a password: Uncheck
Master password: password
Confirm password: password


DB instance size:
DB instance class:
Burstable classes (includes t classes)
db.t2.micro
Include previous generation classes: off

Storage: 
Storage type: General Purpose (SSD)
Allocated storage: 20
Storage autoscaling:
Enable storage autoscaling: Uncheck

Connectivity:
Virtual private cloud (VPC): americano-vpc
Subnet group: americano-private-subnets
Public access: No
VPC security group: Choose existing
Existing VPC security groups: americano-postgres-security-group
Availability Zone: No preference

Database authentication:
Database authentication options: Password authentication

Additional configuration:
Backup:
Enable automatic backups: Uncheck
Performacne Insights: 
Enable Performance Insights: Uncheck
```
10. Click Create database button

## Access RDS from 
**Todo**

## Create bastion server
**Todo**


AWS Beanstalk
------------

## Create dotnet MVC project
1. Create new directory to host project
```
PS>mkdir beanstalk-net
PS>cd beanstalk-net
```

##### dotnet cli to scaffold our new project. Create new dotnet core mvc project, scaffold
PS  C:\beanstalk-net>dotnet new mvc
PS  C:\beanstalk-net>dotnet build
PS  C:\beanstalk-net>dotnet run

open any browser window
go to link http://localhost:5000

Include EntityFramework package, postgresql and StackExchange.Redis

PS  C:\beanstalk-net>dotnet add package Microsoft.EntityFrameworkCore
PS  C:\beanstalk-net>dotnet add package Microsoft.EntityFrameworkCore.Design
PS  C:\beanstalk-net>dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
PS  C:\beanstalk-net>dotnet add package Npgsql

PS  C:\beanstalk-net>dotnet add package StackExchange.Redis - dotnet redis client.


rm -r -force .\site\
rm .\deploy-bundle.zip

dotnet publish -c Release -o site
zip file inside site
mv .\site\deploy-bundle.zip .





