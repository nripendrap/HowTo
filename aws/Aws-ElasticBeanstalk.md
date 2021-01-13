# Aws Getting Started

## Create VPC, Public Subnets and Private Subnets
*VPC*

Your VPCs -> Create VPC 

Create VPC

VPC Settings
Name tag: americano-vpc
IPv4 CIDR Block: 10.0.0.0/16
IPv6 CIDR block: No IPv6 CIDR block
Tenancy: Default



02. Subnet

Subnets -> Create subnet

Create subnet

VPC 
VPC ID: americano-vpc

Subnet settings
Subnate name: americano-public-subnet-a
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2a
IPv4 CIDR block: 10.0.0.0/24

Press "Create subnet" button

Create another 2 subnets

Create subnet

VPC: 
VPC ID: americano-vpc

Subnet settings:
Subnate name: americano-public-subnet-b
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2b
IPv4 CIDR block: 10.0.1.0/24

Press "Create subnet" button

Create subnet

VPC: 
VPC ID: americano-vpc

Subnet settings:
Subnate name: americano-public-subnet-c
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2c
IPv4 CIDR block: 10.0.1.0/24

Press "Create subnet" button

Create 3 private subnets in 3 availability zone

VPC: 
VPC ID: americano-vpc

Subnet settings:
Subnate name: americano-private-subnet-a
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2a
IPv4 CIDR block: 10.0.100.0/24

Press "Create subnet" button

VPC: 
VPC ID: americano-vpc

Subnet settings:
Subnate name: americano-private-subnet-c
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2b
IPv4 CIDR block: 10.0.101.0/24

Press "Create subnet" button

VPC: 
VPC ID: americano-vpc

Subnet settings:
Subnate name: americano-private-subnet-c
Availability Zone: Asia Pacific (Sydney) / ap-southeast-2c
IPv4 CIDR block: 10.0.102.0/24

Press "Create subnet" button

03. Internet Gateways

so public subnet can communicate with internet and internet can access instances inside public subnet

Internet Gateways -> Create internet gateway

Create internet gateway

Internet gateway settings
Name tag:  americano-vpc-ig

Press "Create internet gateway" button

Attach to a VPC / Action -> Attach to VPC / Select ig-cafeamericano-vpc from the table, Click Action -> Attach to VPC

Attach to VPC (igw-<id>)

VPC
Available VPCs: americano-vpc

Press "Attach internet gateway" button


04. Route Tables

Create route table for internet gateway

Route Tables -> Create route table

Create route table
Name tag: americano-public-route
VPC: americano-vpc

Press "Create", then "Close" button

Select americano-public-route row from the list
Click Subnet Associations tab
Click "Edit subnet associations" button
Select all public subnets, i.e. americano-public-subnet-a, americano-public-subnet-b and americano-public-subnet-c
Then press "Save" button

Select Routes tab
Select "Edit routes" -> Add route
Destination: 0.0.0.0/0
Target: americano-vpc-ig

Press "Save routes" button
Then "Close" button



05. NAT Gateways
So private subsets can go through internet

NAT Gateways -> Create NAT gateway

Create NAT gateway

NAT gateway settings
Name: americano-nat-gateway
Subnet: americano-public-subnet-a (One of the public subnet)
Elastic IP allocation ID: Press Allocate Elastic IP button

Press Create NAT gateway button

Then go to Route Tables page
Route Tables -> Create route table

Create route table
Name tag: americano-nat-gateway-route
VPC: americano-vpc

Press "Create", then "Close" button

Select americano-nat-gateway-route row from the list
Click Subnet Associations tab
Click "Edit subnet associations" button
Select all private subnets, i.e. americano-private-subnet-a, americano-private-subnet-b and americano-private-subnet-c
Then press "Save" button

Select Routes tab
Select "Edit routes" -> Add route
Destination: 0.0.0.0/0
Target: americano-nat-gateway

Press "Save routes" button
Then "Close" button

06. Security Group

    Create security groups

    06.01
        Basic details
        Security group name: americano-bastion-sg
        Description: Bastion server security group
        VPC: americano-vpc

        Inbound rules
        Press Add rule button
        Type: SSH
        IP: 0.0.0.0/0

        Click "Create security group" button

    06.02
        Basic details
        Security group name: americano-web-servers-sg
        Description: Web servers security group
        VPC: americano-vpc

        Click "Create security group" button

    06.03
        Basic details
        Security group name: americano-postgres-sg
        Description: Postgres database security group
        VPC: americano-vpc

        Inbound rules
        Press Add rule button
        Type: PostgreSQL
        Source: americano-bastion-security-group

        Press Add rule button
        Type: PostgreSQL
        Source: americano-web-servers-security-group

        Click "Create security group" button




Configure RDS with Postgres
-----------------------

Sign in to the AWS Management Console.
Go to the Services dropdown menu at the top left corner
Choose RDS from the menu



Select Subnet Groups at the left menu
Select Create DB Subnet Group

Create DB Subnet Group:
    Subnet group details:
        Name: americano-private-subnets
        Description: Americano private database subnet group
        VPC: americano-vpc
    Add subnets:
        Availability Zones: ap-southeash-2a, ap-southeast-2b, ap-southeast-2c
        Subnets: 10.0.100.0/24, 10.0.101.0/24, 10.0.102.0/24

Click Create button


Select Databases at the left menu
Select Create database button

Create database:
    
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
    
    Click Create database button


Access RDS from 

Create bastion server:


AWS Beanstalk
------------

Create dotnet MVC project
---------------------



PS  C:\>mkdir beanstalk-net
PS  C:\>cd beanstalk-net

##dotnet cli to scaffold our new project. Create new dotnet core mvc project, scaffold
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





