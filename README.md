# Honeypot Project

## Objective

The goal of this project is to demonstrate how a honeypot functions and its purpose. Honeypots work by simulating a vulnerable system, which then can lure attackers away from critical resources while providing valuable information about their tactics, techniques, and procedures(TTPs). By observing attackers in a controlled environment, you can better understand what they might be up to in your network.

For this project, I will be configuring **T-Pot** The All-In-One Multi Honeypot Platform which includes many different honeypots and numerous visualization options using the Elastic Stack, animated live attack maps, and lots of security tools like Kibana, CyberChef, and Spiderfoot




### Skills Learned



### Tools Used
- Amazon Web Services
- Virtual Box
- Ubuntu 24
- T-Pot - All-In-One Multi Honeypot Platform
- 

### Prerequisites

-There are two Prerequisites for this lab. The first prereq is that you need some sort of SSH client, in my case I will be using Ubuntu 24 to connect to the AWS Honeypot instance

-The second prerequisite is that you need to have an AWS account, the reason for that is we are going to be utilizing hardware that AWS hosts. This lab is **NOT** free and does cost some money.

### Steps

Instance configuration

1. Navigate to EC2 and click launch instance on your AWS account

   - I chose Debian 11 AMI
   - t2.xlarge
   - Create a new custom key pair
   - 128GB of storage as recommended by T-Pot
   - Allow SSH from your IP address, we will set up other rules when T-Pot installation is complete
   - Launch Instance
   - When your instance is fully operational, look in the top right corner and hit connect
     
![TPOTTTT](https://github.com/user-attachments/assets/23b903ca-7cd5-47f8-bf5c-e2f83010fbf0)



2. Connect to the AWS instance Via SSH

   - To be able to connect to my AWS instance I will be using a virtual machine running Ubuntu 24
   - I will download my SSH key file (yourkey.pem) to my SSH client(Ubuntu)
   - Set permission for the file as: `chmod 400 yourkey.pem`
   - SSH to AWS instance with: `ssh -i "yourkey.pem" ubuntu@<your-ec2-Public-DNS>`
     
     
     ![TPOT](https://github.com/user-attachments/assets/903fcd58-1d94-4ba8-9e8f-34cd8c9c3040)

3. Once connected to AWS instance I will run these commands to Install T-Pot:
  
   - Clone the T-Pot Repository   
   ```
   git clone https://github.com/telekom-security/tpotce
   ```
   - Navigate to the T-Pot Folder:   
   ```  
   cd price
   ```   
   - Run the Installer, make sure to run the installer script as a non-root user:    
   ```
   ./install.sh --type=user
   ```   
  - During the installation, it will ask you to
     choose your T-Pot type:
   ```  
 (H)ive   - T-Pot Standard / HIVE installation.
            Includes also everything you need for a distributed setup with sensors.
 (S)ensor - T-Pot Sensor installation.
            Optimized for a distributed installation, without WebUI, Elasticsearch and Kibana.
 (M)obile - T-Pot Mobile installation.
            Includes everything to run T-Pot Mobile (available separately).
 Install Type? (h/s/m) h
  ```

- I will hit h for T-Pot Standard
- Next, you will be asked for a web username and password
  
4. Now I will go back to my EC2 instance and traverse to Security Groups where we will click on edit inbound rules and create these three rules:

   - Custom TCP   64295   My IP     SSH for Admin
   - Custom TCP   64297   My IP     SSH Web Admin
   - Custom TCP  1-64000  Anywhere   Open to all
   
![TPOT 3](https://github.com/user-attachments/assets/d5683186-170f-43c0-a0d8-db4845c2b562)

5. Now that the inbound rules are set I can head back to my SSH client and SSH back to my EC2 instance

   I have to modify the SSH command to contain the port number
   - `ssh -i "yourkey.pem" ubuntu@<your-ec2-instance-Public-DNS> -p 64295`

6. Now that the rules seem to be working lets try and access the web portal by heading to a web browser and type in:

   - `https://yourpublicip:64297`
   - Type in the username and password you created when installing T-Pot
   ### Here is what the dashboard looks like:  

   ![TPOT 4](https://github.com/user-attachments/assets/e44ec602-7cfd-4595-8b1b-68a64bb1e531)

   I am going to head to Kibana and look at all of the active attacks

### The Honeypot has only had 10 minutes to ingest attacks and information and already has numerous attacks against it

7. This is Kibana and you can see how powerful these dashboards can be as they show multiple valuable information data streams in one centralized place. Just in this one dashboard, we get access to an attack map, bar graph, pie charts, and a heatmap

![TPOT6](https://github.com/user-attachments/assets/e434e7d0-90d2-4403-8c89-8e3079f05f39)

8. This is the attack map for this Honeypot, as you can see there is quite a lot of activity for only being up for such a short amount of time, and attacks ranging from all around the world
   
![TPOT5](https://github.com/user-attachments/assets/e3d8f950-6c78-4c9e-b9e5-f274214942bf)

