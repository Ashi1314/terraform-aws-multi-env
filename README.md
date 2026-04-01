 Terraform AWS Multi-Environment

## 📖 Overview
This project demonstrates how to manage AWS infrastructure using Terraform for multiple environments:

- Development (dev)
- Staging
- Production (prod)

It follows best practices like modular design, reusable code, and environment isolation.

---

## 🚀 Key Features

- Multi-environment support
- Reusable Terraform modules
- Clean folder structure
- Remote state support (S3 + DynamoDB)
- Scalable and production-ready design

---

## 📂 Project Structure

terraform-aws-multi-env/

modules/                # Reusable modules (VPC, EC2, etc.)

environments/           # Environment-specific configs
  ├── dev/
  ├── staging/
  └── prod/

main.tf                 # Main configuration  
variables.tf            # Input variables  
outputs.tf              # Outputs  
backend.tf              # Remote backend config  

---

## ⚙️ Prerequisites

- Terraform (>= 1.x)
- AWS CLI configured
- AWS account with proper IAM permissions

---

## 🔧 Setup Instructions

### 1. Clone Repository


git clone https://github.com/Ashi1314/terraform-aws-multi-env.git

cd terraform-aws-multi-env


### 2. Initialize Terraform
terraform init


### 3. Run for Dev Environment
terraform plan -var-file=environments/dev/terraform.tfvars
terraform apply -var-file=environments/dev/terraform.tfvars


---

## 🌍 Multi-Environment Concept

- Each environment has its own `.tfvars` file  
- Same modules are reused across all environments  
- Ensures consistency and avoids duplication  

---

## 🔐 Remote State Setup (Recommended)

Use S3 + DynamoDB:

terraform {
backend "s3" {
bucket = "my-terraform-state"
key = "dev/terraform.tfstate"
region = "ap-south-1"
dynamodb_table = "terraform-lock"
}
}


---

## 🔄 CI/CD Integration

Supported tools:
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

## 📊 Architecture Diagram

Developer
↓
Terraform
↓
| AWS Infrastructure |

↓ ↓ ↓
Dev Staging Prod



---

## 💡 Use Cases

- Infrastructure automation
- Multi-environment deployment
- DevOps learning projects
- Production-ready setups

---

## 🧠 Learning Outcomes

- Terraform modules
- State management
- Environment isolation
- Real-world DevOps workflow

---

## ⭐ Support
