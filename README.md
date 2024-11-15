# Honeypot Project

## Objective

T-Pot - The All In One Multi Honeypot Platform


### Skills Learned



### Tools Used

### Steps

Instance configuration

1. Navigate to EC2 and Click launch instance on AWS

   - I chose Debian 11 AMI
   - t2.xlarge
   - Create new custom keypair
   - 128GB of storage as recommended by T-Pot
   - Allow SSH from your IP address, we will set up other rules when T-Pot installation is complete
   - Launch Instance

5. Access your new instance using SSh
   - Click on your instance and in the top right corner hit connect
![TPOTTTT](https://github.com/user-attachments/assets/f690fa13-bd9d-490d-a3be-c020a5cc07d3)
   - Download SSH key file (yourkey.pem)
   - set permission the file as: `chmod 400 yourkey.pem`
   - SSH to instance with: `ssh -i "Examplekey.pem" ubuntu@<your-ec2-instance-ip>`
     
7. Third

8. Fourth

9. Fifth

10. Sixth

