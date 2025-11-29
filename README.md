# VPCWebServer
Making a Virtual Private Cloud so you can launch an EC2 instance to place inside of the VPC, highlighting the architecture of the AWS Cloud

## Project Overview
- Creating a virtual private cloud (VPC)
- Creating subnets
- Configuring security groups
- Launch an Amazon Elastic Compute Cloud (EC2) into a VPC

## VPC Architecture
<img width="1114" height="511" alt="image" src="https://github.com/user-attachments/assets/171ca351-5d45-496b-800e-adced7d5d699" />

## 🛠 Steps Performed
### 1️⃣ Create the VPC
1. On the AWS Management Console, VPC services page, click "Create VPC"
- **Resources to create**: VPC and more
- **Name tag auto-generation**: Uncheck the box
- **IPv4 CIDR**: Enter 10.0.0.0/16
- **IPv6 CIDR block**: Choose No IPv6 CIDR block
- **Tenancy**: Choose Default
- **Number of Availability Zones (AZs**): 1
- **Number of public subnets**: 1
- **Number of private subnets**: 1
- Expand **Customize subnets CIDR blocks**
  - **Public subnet CIDR block**: 10.0.0.0/24
  - **Private subnet CIDR block**: 10.0.1.0/24
- **VPC endpoints**: Choose none
### 2️⃣ Creating additional subnets
1. Choose Subnets in the left navigation pane on the VPC page.
2. To configure the second public subnet, choose create subnet and configure it
  - **VPC ID**: Choose the VPC name that you created in Step 1.
  - **Subnet name**: Public Subnet 2
  - **Availability Zone**: No preference
  - **IPv4 CIDR block**: Enter 10.0.2.0/24
3. Create Subnet
4. Create subnet for the second private subnet
  - **VPC ID**: Choose the VPC name that you created in Step 1
  - **Subnet name**: Private subnet 2
  - **Availability Zone**: No preference
  - **IPv4 CIDR block**: Enter 10.0.3.0/24
5. Create subnet
### 3️⃣ Adding routes
1. In the left navigation pane, choose **Route Tables**
2. Choose **Public Route Table**
3. In the lower pane, choose the Subnet associations tab
4. Under **Subnets without explicit associations**, choose **Edit subnet associations**
5. Select the check boxes for **Public Subnet 2**
6. Choose **Save associations**
7. Choose **Private Route Table**
8. In the lower pane, choose the **Subnet associations tab**
9. Under **Subnets without explicit associations**, choose **Edit subnet associations**
10. Select the check boxes for **Private Subnet 2**
11. Choose **Save associations**
### 4️⃣ Create a VPC security group
1. In the left navigation pane, choose **Security Groups**
2. Choose **Create security group**
3. Configure the security group
  - **Security group name**: Enter ```Web Security Group```
  - Description: Enter ```Enable HTTP access```
  - VPC: Choose your created VPC
4. Under **Inbound rules**, choose **Add rule**
5. Configure the following options
  - **Type**: Choose HTTP
  - **Source**: Choose Anywhere IPv4
  - **Description**: ```Permit web requests```
6. Create security group
### 5️⃣ Launch a web server instance
1. Go to EC2 on the AWS Management Console
2. In the left navigation pane, choose Instances
3. Choose Launch instances a
