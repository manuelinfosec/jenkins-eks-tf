# terraform-jenkins-eks

## Deploying an EKS Cluster with Terraform and Jenkins Pipeline

This repository provides a setup for deploying an EKS (Elastic Kubernetes Service) cluster on AWS using Terraform and a Jenkins pipeline for automation.

### Project Structure

* **Jenkinsfile:** Defines the Jenkins pipeline stages for provisioning the EKS cluster and deploying applications.
* **README.md:** (You are here!) This file describes the project structure and usage.
* **EKS/**: Contains Terraform configuration files for the EKS cluster:
    * `backend.tf` (optional): Configures Terraform state backend (e.g., remote storage).
    * `data.tf`: Defines data sources used by Terraform configurations.
    * `main.tf`: The main Terraform configuration file for the EKS cluster.
    * `provider.tf`: Defines the Terraform provider for AWS.
    * `terraform.tfvars`: Stores Terraform variables specific to your environment (replace with your values).
    * `variables.tf`: Defines default or reusable Terraform variables.
    * **ConfigurationFiles/**: Stores configuration files for your EKS applications (replace with your own):
        * `deployment.yaml`: Example deployment YAML file for your application.
        * `service.yaml`: Example service YAML file for your application.
* **Jenkins Server/**: Contains Terraform configuration files for the Jenkins server on EC2:
    * `.gitignore`: Specifies files to be ignored by Git version control.
    * `backend.tf` (optional): Configures Terraform state backend (e.g., remote storage).
    * `data.tf`: Defines data sources used by Terraform configurations.
    * `jenkins-install.sh`: Script for installing and configuring Jenkins (modify as needed).
    * `main.tf`: The main Terraform configuration file for the Jenkins server.
    * `provider.tf`: Defines the Terraform provider for AWS.
    * `README.md` (optional): Documentation specific to the Jenkins server configuration.
    * `terraform.tfvars`: Stores Terraform variables specific to your Jenkins server environment (replace with your values).
    * `variables.tf`: Defines default or reusable Terraform variables for the Jenkins server.

### Usage

**Prerequisites:**

* An AWS account with appropriate permissions.
* Terraform installed and configured.
* Basic understanding of Terraform and Jenkins.

**Steps:**

1. **Configure Terraform and Jenkins Environments:**
    * Update `terraform.tfvars` files (EKS and Jenkins) with your specific AWS credentials, region, and desired configurations.
    * Update `jenkins-install.sh` (optional) to customize Jenkins installation on EC2.
    * Update `deployment.yaml` and `service.yaml` with your application configurations.
2. **Deploy Jenkins Server (Optional):**
    * Run `terraform init` in the `Jenkins Server` directory.
    * Run `terraform plan` to review the planned changes.
    * Run `terraform apply` to provision the Jenkins server on AWS.
3. **Deploy EKS Cluster:**
    * Run `terraform init` in the `EKS` directory.
    * Run `terraform plan` to review the planned changes for the EKS cluster.
    * Run `terraform apply` to provision the EKS cluster on AWS.
4. **Configure Jenkins Pipeline (Manual):**
    * Access your Jenkins server and create a new pipeline job.
    * Integrate the Terraform workflow for deploying your application to the EKS cluster.
    * Refer to the Jenkins documentation for detailed pipeline configuration.

**Additional Notes:**

* This is a basic example, and you might need to modify it based on your specific requirements.
* Secure your Terraform state and access credentials appropriately.
* Configure security groups, IAM roles, and other AWS resources as needed for your application.

**For further details:**

* Refer to the official documentation for Terraform: [https://developer.hashicorp.com/terraform/docs](https://developer.hashicorp.com/terraform/docs)
* Refer to the official documentation for Jenkins: [https://www.jenkins.io/doc/](https://www.jenkins.io/doc/)