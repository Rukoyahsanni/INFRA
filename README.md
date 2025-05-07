# 🚀 Terraform-Jenkins-AWS Infrastructure Deployment

This project automates the provisioning of a Jenkins CI/CD server using **Terraform** and **AWS EC2**, and demonstrates how to use Jenkins pipelines to further deploy AWS infrastructure — specifically a custom **VPC** — via infrastructure-as-code.

---

## 📌 Project Overview

The deployment process includes:

1. **Terraform provisioning** of an EC2 instance on AWS.
2. **Installation and configuration of Jenkins** on the EC2 instance.
3. Jenkins setup to:
   - Install required plugins
   - Store and manage AWS credentials securely
4. **Pipeline creation in Jenkins** to:
   - Run a Terraform script that deploys a **custom VPC** on AWS

---

## 🛠️ Tools & Technologies

- **Terraform** – Infrastructure as Code (IaC)
- **AWS EC2** – Virtual server for Jenkins
- **Jenkins** – CI/CD automation tool
- **AWS IAM** – Credential and permission management
- **GitHub** – Source control and pipeline triggers

---


---

## ⚙️ Setup Instructions

### 1. Provision Jenkins EC2 with Terraform

```bash
cd INFRA
terraform init
terraform validat
terraform plan
terraform apply --auto-approve
```
This spins up an EC2 instance and uses the terraform provisioner block in the ec2.tf file to install jenkins and print our website URL

### 2. Configure Jenkins
- Complete initial setup
- Install plugins: Terraform, AWS Credentials

### 3. Connect Jenkins to AWS
- In Jenkins, go to: Manage Jenkins → Credentials
- Add your AWS Access Key ID and Secret Access Key
- Create a new Pipeline Job

### 4. Jenkins Pipeline to Deploy Custom VPC
In the pipeline configuration:
- Add parameter
- Set up a GitHub repo as the source
- Use a Jenkinsfile to run Terraform from jenkins-vpc-pipeline/

🔐 Security Considerations
1. AWS credentials are stored securely using Jenkins Credentials Manager
2. IAM roles should follow least privilege principle
3. Security group rules should be strict and reviewed

🙋‍♂️ Author
Rukayat Sanni – LinkedIn | GitHub

