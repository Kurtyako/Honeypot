# Honeypot Project

## Objective


-T-Pot - The All In One Multi Honeypot Platform



### Skills Learned



### Tools Used

###Prerequisites

-There are two Prerequisites for this lab. The first prereq is that you need some sort of SSH client, in my case I will be using Ubuntu 24 to connect to the AWS Honeypot instance

-The second prerequisite is that you need to have an AWS account, the reason for that is we are going to be utilizing hardware that AWS hosts. This lab is **NOT** free and does cost some money.

### Steps

Instance configuration

1. Navigate to EC2 and Click launch instance on AWS

   - I chose Debian 11 AMI
   - t2.xlarge
   - Create new custom keypair
   - 128GB of storage as recommended by T-Pot
   - Allow SSH from your IP address, we will set up other rules when T-Pot installation is complete
   - Launch Instance
   - When your instance is fully operational, look in the top right corner hit connect
     
![TPOTTTT](https://github.com/user-attachments/assets/f690fa13-bd9d-490d-a3be-c020a5cc07d3)


2. Connect to the AWS instance Via SSH

   - To be able to connect to my AWS instance I will be using a virtual machine running Ubuntu 24
   - Download SSH key file (yourkey.pem) to your SSH client
   - set permission the file as: `chmod 400 yourkey.pem`
   - SSH to AWS instance with: `ssh -i "Examplekey.pem" ubuntu@<your-ec2-instance-ip>`
     
7. Install Honeypot(T-Pot) on AWS instance by running these commands

  - Clone the T-Pot Repository:
   git clone https://github.com/telekom-security/tpotce

   - Navigate to the T-Pot Folder:
   cd price
   
   - Run the Installer: Execute the installer script as a non-root user:
   ./install.sh
   

9. Fourth

10. Fifth

11. Sixth

