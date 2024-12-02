# AWS Scalable Web Application Architecture

## Description
This architecture is a hands-on walk through of a three-tier web architecture in AWS. We will be manually creating the necessary network, security, app, and database components and configurations in order to run this architecture in an available and scalable manner.

## Architecture Design
![alt text](image.png)

## Procedure Explanation of Scalable Web Application
### Step1
### 1. Create a VPC
   a. In the AWS Management Console, in the search bar, type vpc and select vpc which is highlighted.
![alt text](vpc.png)

   b. In the VPC dashboard, In the left navigation, in th Virtual Private Cloud Section, Select Your VPCs
![alt text](vpcdashboard.png)

   c. Click "Create VPC" on the top right of VPC console.
![alt text](<vpc create.png>)

   d. In the Create VPC Section, Select "VPC and more" option. Name the VPC. Set the IPv4 CIDR block to   10.0.0.0/16.Choose "No IPv6 CIDR block" option. Leave the tenancy to default. Choose the Number of Availability Zones "2", Choose Number of public subnets "2" , Choose Number of private subnets "4".
   Choose NAT Gateway "In 1 AZ". Choose VPC Endpoints "None". Leave the DNS options as default.
   Choose "Create VPC"
![alt text](<create vpc section.png>)

![alt text](<create vpc1.png>)

![alt text](<create vpc2.png>)

   e. VPC is Succesfully created
![alt text](vpcfinal.png)

### 2. Go To "Subnets" tab under "Your VPCs"

![alt text](subnets.png)

a. Select a public subnet and Click on Actions dropdown and Click "Edit Subnet Settings" and 
Check the "Enable auto-assign public IPv4 address" option in the "Auto-assign IP settings" section, Scroll down and Click Save.
b. Make Sure this Step 1.2a should be for every public subnet.

![alt text](publicsubnetselect1.png)

![alt text](<edit subnet.png>)

![alt text](<public subnet save.png>)

### 3. Go to "Route tables" tab
a. Select 3tierwebapp public route table in Route table console
![alt text](3tierprt.png)

b. go to "Routes" tab and click "Edit Routes"
![alt text](3tierroutesedit.png)

c. Click "Add route" option. Select Destination "0.0.0.0/0" and Target "Internet Gateway" and Save changes.
![alt text](3tieraddroute.png)

![alt text](3tierrouteadded.png)

e. Move to "Subnet associations" tab and click "Edit subnet associations"
![alt text](3tiersubnetassociates.png)

f. Select public subnets in both availability zones and click Save associations
![alt text](3tieraddsubnetassociates.png)


### 4. Go to "Internet gateways" tab
a. Click on "Create internet gateway" option
![alt text](3tierigw.png)

b. type the name and click "Create internet gateway"
![alt text](igwcreate.png)

c. Select the internet gateway and click on Actions dropdown, click "Attach to VPC" and check vpc is
attached
![alt text](igwvpc.png)

![alt text](igwcheck.png)


### 5. Go to "NAT gateways" tab
Check the NAT gateway is created

![alt text](natgw.png)

### 6. Go to "Security Groups" tab in Security Section in Left Navigation of VPC console
a. Create "Security Group"
![alt text](sgconsole.png)

b. type the name and description and select the created vpc
![alt text](securitygroup.png)

c. Add "Inbound rules"
   a. type : SSH, source: Anywhere-IPv4
   b. type : HTTP, source: Anywhere-IPv4
   c. type : HTTPS, source: Anywhere-IPv4
![alt text](sginbound.png)

d. Scroll down and Click "Create security group"
![alt text](clicksg.png)

e. See the selected security group
![alt text](sgsconsole.png)


## Step 2

1. Type in the search bar "EC2", Select EC2 service, EC2 dashboard will be shown

![alt text](ec2search.png)

![alt text](ec2dashboard.png)

2. Select the "Instances(running)" option in Resources tab, ec2 console will be shown
![alt text](ec2console.png)

3. Move to "Launch Templates" tab under "Instance Type", Launch Templates console will be shown

![alt text](launchtemplate.png)

4. type the name and description, Check the "Provide guidance to help me set up a template that I can use with EC2 Auto Scaling" in Auto Scaling section. Choose "Quick Start" tab in "Application and OS Images (Amazon Machine Image)" section. Choose "Amazon Linux" AMI. Choose "t3.micro" instance type which is free tier eligible. Choose "Don't include in launch template" in Key Pair section.

![alt text](launchtemplatecreate.png)

![alt text](launchtemplateAMI.png)

![alt text](launchtemplateinstancetype.png)

5. 
