# Secure-EC2-Web-Application-PoC


images/ec2-web-output.png

Objective
•	Deploy a web application on EC2
•	Use AWS networking & security correctly
•	Enable monitoring and storage
•	Stay completely inside Free Tier

🌍 AWS Region
•	Asia Pacific (Mumbai)

Step 1: IAM Setup
•	Create IAM user
•	Attach AdministratorAccess
•	Enable MFA


 Step 2: Launch EC2 (Free Tier)
•	Instance type: t2.micro
•	AMI: Amazon Linux 2
•	Network: Default VPC
•	Public IP: Enabled
•	Storage: 30 GB gp2


Step 3: Security Group
Allow only required ports:
Port	Source
22 (SSH)	Your IP only
80 (HTTP)	Anywhere


Step 4: Install Web Server

SSH into EC2 and run:
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
Create a test page:
echo "EC2 Free Tier PoC Running Successfully" | sudo tee /var/www/html/index.html
	
Step 5: Access Website
•	Copy Public IPv4 address
•	Open in browser:
http://<EC2-PUBLIC-IP>
✅ Website loads


Step 6: EBS Validation (Storage PoC)
•	Stop EC2
•	Modify volume size (example: 20 → 30 GB)
•	Start EC2
✔ Shows scalable storage

Step 7: CloudWatch Monitoring
•	EC2 → Monitoring tab
•	Observe:
o	CPU Utilization
o	Network In / Out
o	Disk activity
