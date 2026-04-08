# 🌍 Cross-Region Backup Strategy using AWS

## 📌 Project Overview
This project demonstrates how to implement a **cross-region backup and disaster recovery strategy** using AWS services.

The goal is to ensure that application data is safely backed up in another region and can be restored quickly in case of failure.

---

## 🎯 Objective
- Launch an EC2 instance in one region
- Create a backup using EBS snapshot
- Copy the snapshot to another region
- Restore the application in the second region
- Validate application availability

---

## 🛠️ Technologies & Services Used
- AWS EC2 (Elastic Compute Cloud)
- Amazon EBS (Elastic Block Store)
- EBS Snapshots
- AWS Regions (Mumbai & Ohio)
- Apache Web Server (httpd)
- Linux

---

## 🏗️ Architecture Diagram
Region A (Mumbai) → EBS Volume → Snapshot → Copy → Region B (Ohio)
↓
Create Volume
↓
EC2 Instance
↓
Restored Application


---

## 🔄 Workflow

1. Launch EC2 instance in Region A (ap-south-1 - Mumbai)
2. Install Apache and deploy a sample web application
3. Create an EBS snapshot from the root volume
4. Copy the snapshot to Region B (us-east-2 - Ohio)
5. Create a new EBS volume from the copied snapshot
6. Launch a new EC2 instance in Region B
7. Detach default root volume and attach restored volume
8. Start the web server and validate application

---

## ⚙️ Setup Steps

### 🔹 Step 1: Launch EC2 in Region A
- Region: Mumbai (ap-south-1)
- Install Apache:
  sudo yum install httpd -y
  sudo systemctl start httpd
  
Step 2: Deploy Application
cd /var/www/html
sudo vi index.html
Add sample HTML content and access using public IP.

Step 3: Create Snapshot
Go to EC2 → Volumes
Select root volume
Click Create Snapshot
🔹 Step 4: Copy Snapshot to Region B
Select snapshot
Click Copy Snapshot
Choose Region: Ohio (us-east-2)
🔹 Step 5: Restore in Region B
Create volume from copied snapshot
Ensure correct Availability Zone
🔹 Step 6: Launch EC2 in Region B
Create new EC2 instance
Detach default root volume
Attach restored volume

Step 7: Start Application
sudo systemctl start httpd
Access using public IP
Verify application is working

✅ Key Features
Cross-region backup
Disaster recovery solution
Data replication across regions
High availability support
📈 Benefits
Protects against regional failures
Ensures data safety
Quick recovery of applications
Reliable backup strategy
🚀 Future Enhancements
Automate backup using AWS Backup
Use S3 for additional backup storage
Implement multi-region active-active setup
Add monitoring with CloudWatch

👨‍💻 Author

Harshavardhan
BCA Student | Aspiring Cloud & DevOps Engineer

