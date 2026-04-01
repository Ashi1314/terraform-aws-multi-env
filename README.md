
# Terraform AWS Multi-Environment Setup

This project demonstrates how to provision and manage AWS infrastructure using Terraform across multiple environments (dev, staging, prod) using a modular and scalable approach.

---

## 🚀 Features

- Multi-environment setup (dev, staging, prod)
- Reusable Terraform modules
- Environment-specific configurations using `.tfvars`
- Remote state management (S3 + DynamoDB recommended)
- Scalable and DRY (Don't Repeat Yourself) architecture
- Easy CI/CD integration (GitHub Actions / Jenkins)

---

## 📂 Project Structure

terraform-aws-multi-env/

├── modules/
│   ├── ec2/
│   ├── vpc/
│   └── ...

├── environments/
│   ├── dev/
│   ├── staging/
│   └── prod/

├── main.tf
├── variables.tf
├── outputs.tf
└── backend.tf

---

## ⚙️ Prerequisites

- Terraform (>= 1.x)
- AWS CLI configured
- AWS account with proper IAM permissions

---

## 🔧 Setup & Usage

git clone https://github.com/Ashi1314/terraform-aws-multi-env.git
cd terraform-aws-multi-env

terraform init

terraform plan -var-file=environments/dev/terraform.tfvars
terraform apply -var-file=environments/dev/terraform.tfvars

---

## 🔐 Remote State (Recommended)

Example:

terraform {
  backend "s3" {
    bucket         = "my-terraform-state"
    key            = "dev/terraform.tfstate"
    region         = "ap-south-1"
    dynamodb_table = "terraform-lock"
  }
}

---

## 🔄 CI/CD Integration

- GitHub Actions
- Jenkins
- AWS CodePipeline

Workflow:
1. Code push
2. Terraform init
3. Terraform plan
4. Approval
5. Terraform apply

---

## 📌 Use Cases

- Infrastructure automation
- Multi-environment deployments
- DevOps learning projects

---

## ⭐ Support

If you like this project, give it a ⭐ on GitHub!
