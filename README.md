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

## 📁 Project Structure

terraform-jenkins-vpc/
├── ec2-instance/
│ ├── main.tf # Provisions Jenkins EC2
│ ├── variables.tf
│ └── outputs.tf
├── jenkins-vpc-pipeline/
│ ├── main.tf # Terraform to create VPC
│ ├── variables.tf
│ └── outputs.tf
├── scripts/
│ └── jenkins-install.sh # Installs Jenkins and plugins
└── README.md
