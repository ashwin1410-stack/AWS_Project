# Launching EC2 Instance(Linux), Connecting via SSH, and Installing Apache HTTP Server

## Introduction:-
This document will guide you through the process of launching an Amazon EC2 instance running Linux, connecting to it via SSH, and installing Apache HTTP Server (httpd) to host a website.



### Prerequisites:-
- An AWS account with appropriate permissions to create EC2 instances.
- Basic knowledge of the AWS Management Console.
- Basic knowledge of using SSH.
## Step 1: Launching an EC2 Instance:-
1. **Sign in to the AWS Management Console**: Go to AWS Console and sign in with your credentials.
2. **Navigate to EC2 Dashboard**: From the services menu, select EC2, or you can search for EC2 in the services search bar.
3. **Launch Instance**:
    - Click on the "Launch Instance" button.
    - Choose an Amazon Machine Image (AMI) with a Linux distribution of your choice Amazon Linux 2.
    - Select an instance type based on your requirements t2.micro.
    - Configure instance details, including network settings, storage, tags, and security groups.
    - Create a new security group allowing inbound traffic on port 22 (SSH) and port 80 (HTTP) from your IP address or any other relevant source.
    - Review and launch the instance.
4. **Create a new key pair or use existing one**:
    - If you are creating a new key pair, download the private key "Linux.pem" file. Ensure to keep it secure as it's required for SSH access.
5. **Launch Instance**:
    - Once everything is configured, click on the "Launch" button to launch the instance.
6. **Wait for Instance to Start**:
    - It might take a few minutes for the instance to initialize.
## Step 2: Connecting to the Instance via SSH:-
1. **Locate Your Instance**:
    - Once the instance state is "running" in the EC2 dashboard, note down its public IP address or public DNS.
2. **Open Terminal (or Command Prompt for Windows)**:
    - Change directory to where your private key "Linux.pem" file is located.
3. **Set Permissions for the Private Key**:
    - Run chmod 700 "Linux.pem"  to set proper permissions for the private key file.
4. **SSH into the Instance**:
    - Use the following command to connect to the instance:
```
ssh -i "Linux.pem" ec2-user@3.110.219.165
```
**You are now connected to your EC2 instance via SSH**.

## Step 3: Installing Apache HTTP Server (httpd):-
**Update Package Repository**:

- Run the following command to update the package repository:
```
sudo yum update -y
```
**Install Apache HTTP Server**:

- Run the following command to install Apache HTTP Server:
```
sudo yum install httpd -y
```
**Start Apache Service**:

- After installation, start the Apache service by running:
```
start systemctl start httpd
```
**Enable Apache Service to Start on Boot**:

- Enable Apache service to start automatically on system boot with:
```
sudo systemctl enable httpd
```
## Step 4: Testing Apache Installation:-
**Verify Apache Status**:

- Check if Apache HTTP Server is running:
```
sudo systemctl status httpd
```
![Screenshot 2024-03-23 212007.png](https://eraser.imgix.net/workspaces/VD88RMtz6aOYgc8J5F4H/wDvujyqwbvYnfYNLiDs25jwkruJ3/mglIntWiJv3p_sfmHrMyy.png?ixlib=js-3.7.0 "Screenshot 2024-03-23 212007.png")

**Access Apache Default Page**:

- Open a web browser and navigate to your instance's public IP address or DNS.
- You should see the Apache default page, confirming that Apache is installed and running correctly.
## Conclusion
Congratulations! You have successfully launched an EC2 instance(Linux), connected to it via SSH, and installed Apache HTTP Server. You can now host your website or web application on this EC2 instance. Make sure to configure your security groups and server settings according to your requirements for production use.

