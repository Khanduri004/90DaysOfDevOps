#  AWS EC2 and Security Groups

EC2 stands for Elastic Compute Cloud. 
EC2 is an on-demand computing service on the AWS cloud platform. Under computing, it includes all the services a computing device
can offer to you along with the flexibility of a virtual environment.

Amazon EC2 is a short form of Elastic Compute Cloud (ECC) it is a cloud computing service offered by the Cloud Service Provider AWS. 
You can deploy your applications in EC2 servers without worrying about the underlying infrastructure. 
You configure the EC2-Instance in a very secure manner by using the VPC, Subnets, and Security groups.

**Create EC2 Instance in AWS (Amazon)**
The following are the steps for creating an EC2 instance in AWS (Amazon):

**1)** Open your browser and navigate to the AWS Management Console. 

**2)** First, log into your AWS account and click on “services” present on the left of the AWS management console, 
i.e. the primary screen. From the drop-down menu of options, tap on “EC2”. To create an AWS free tier account refer to 

**3)** Click "Launch Instance" 
Choose Amazon Machine Image (AMI) (e.g., Ubuntu, Amazon Linux). Select the required operating 
system from the available. There are different types of OS available select the OS as per your requirement.

**4)** Choose an Instance Type 
AWS Free Tier includes t2.micro, which is eligible for 750 hours/month for the first 12 months.
Select t2.micro (1 vCPU, 1 GB RAM).
Click Next: Configure Instance Details.

**5)** Configure Instance Details 
Add VPC, Subnet, IAM Role if required.

**6)** Add Storage 
Define volume size and type. 
The default storage size for Amazon Linux 2 is typically 8 GB of General Purpose SSD (gp2), which is within the Free Tier limits.
You can leave the default storage as is.

**7)** Add Tags (Optional) 
Tags are optional and used for organizing and identifying your instances. You can skip this step or create tags if needed.
For example, you can add a Name tag with value like My-First-EC2-Instance.

**8)** Configure Security Group 
A Security Group acts as a virtual firewall to control traffic to your instance.
Select Create a new security group.
Add Inbound Rules: For web access, add a rule for SSH (for Linux instances):
Type: SSH
Protocol: TCP
Port Range: 22
Source: Anywhere (0.0.0.0/0) (if you want to allow SSH from any IP) or My IP (to restrict to your current IP).
You can also add HTTP (port 80) or HTTPS (port 443) rules if you plan to use this instance as a web server.
Click Review and Launch. 

**9)** Review and Launch
Review all the details you’ve selected:
Instance Type: t2.micro (Free Tier eligible)
AMI: Amazon Linux 2
Security Group: SSH access enabled
Storage: 8 GB SSD 

**10)** Select a Key Pair
In this step, you'll create or choose an existing Key Pair, which will be used to securely connect to your EC2 instance via SSH.
If you don’t have a key pair:

                            Select Create a new key pair.
                            Give the key pair a name (e.g., MyKeyPair).
                            Click Download Key Pair. 
                            
This will download a .pem file to your system. Store this file securely — you'll need it to connect to your instance.

**11)** Access Your EC2 Instance
After launching, go to the EC2 Dashboard and click on Instances in the left sidebar.

**12)** Connect to Your EC2 Instance (via SSH) 
        Open a terminal (Linux/macOS) or an SSH client (Windows).
        Navigate to the directory where you downloaded the .pem key pair file.
        Run the following SSH command to connect to your instance (replace ec2-user and <your-public-ip> with your actual 
        instance username and IP address):
        
        ssh -i MyKeyPair.pem ec2-user@<your-public-ip>

**Note** : If you are on Windows and using PuTTY, convert the .pem file to .ppk using PuTTYgen, and then connect via PuTTY.

Once logged in, you should have full access to your EC2 instance. You can now start configuring your instance, installing software, 
and setting up your environment as needed.

**13)** Terminate Your Instance (When Done) 
To avoid unexpected charges, remember to terminate your EC2 instance after you're done with it.
        In the EC2 Dashboard, go to Instances.
        Select your running instance.
        Click on the Actions button, choose Instance State, and then Terminate.
        Confirm the termination when prompted.


**Inbound Rules** (Incoming Traffic)
Protocol	Port	Source	Purpose
SSH	22	My IP	Secure remote access
HTTP	80	0.0.0.0/0	Web server access
HTTPS	443	0.0.0.0/0	Secure web access
MySQL	3306	Custom IP	Database connection (Limit to backend only)
RDP	3389	Custom IP	Remote Desktop for Windows instances
PostgreSQL	5432	Custom IP	Database access

 **Outbound Rules** (Outgoing Traffic)
By default, all outbound traffic is allowed.

**Best Practices for Security Groups** :

Follow Least Privilege Principle – Open only necessary ports.

Restrict SSH (Port 22) Access – Allow only your IP instead of 0.0.0.0/0.

Use IAM Roles for Permissions – Instead of allowing public access.

Monitor Traffic – Enable AWS CloudTrail & VPC Flow Logs.

Regularly Audit Security Groups – Remove unused rules.

Use Network ACLs – For an additional layer of security.

💪 Task Completed! 🚀

📌 GitHub Repository: 90 Days of DevOps - Network

https://github.com/Khanduri004/90DaysOfDevOps/new/Personal-Notes/2025/networking/Week%201%20Challenge%20

🚀 Happy Cloud Learning! 🎉

        
