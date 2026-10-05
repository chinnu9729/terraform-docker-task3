# Infrastructure as Code with Terraform

## Project Overview

This project demonstrates Infrastructure as Code (IaC) using Terraform to provision and manage a Docker container.

The infrastructure was created on an Ubuntu AWS EC2 instance using Terraform and the Docker provider. An Nginx Docker container was provisioned, verified, and then destroyed using Terraform commands.

## Objective

Provision a local Docker container using Terraform and demonstrate the complete infrastructure lifecycle:

* Initialize Terraform
* Validate the configuration
* Create an execution plan
* Provision Docker resources
* Verify the running container
* Inspect Terraform state
* Destroy the infrastructure

## Technologies Used

* AWS EC2
* Ubuntu Linux
* Terraform
* Docker
* Docker Provider
* Nginx
* Git & GitHub

## Architecture

```text
AWS EC2 Ubuntu
      |
      v
   Terraform
      |
      v
 Docker Provider
      |
      +----> Nginx Docker Image
      |
      v
 terraform-nginx Container
      |
      v
 Port 8080 -> Container Port 80
```

## Terraform Resources

The Terraform configuration creates:

1. Docker Nginx image
2. Docker Nginx container

The container is named:

```text
terraform-nginx
```

Port mapping:

```text
EC2 localhost:8080 -> Container:80
```

## Terraform Commands Used

### Initialize Terraform

```bash
terraform init
```

### Format the configuration

```bash
terraform fmt
```

### Validate configuration

```bash
terraform validate
```

### Create execution plan

```bash
terraform plan
```

### Provision infrastructure

```bash
terraform apply
```

### Check Terraform state

```bash
terraform state list
```

### Inspect container state

```bash
terraform state show docker_container.nginx
```

### Verify Docker container

```bash
docker ps
```

### Test Nginx

```bash
curl http://localhost:8080
```

### Destroy infrastructure

```bash
terraform destroy
```

## Result

Terraform successfully provisioned the Docker Nginx container.

The application was verified using:

```bash
curl http://localhost:8080
```

The Nginx welcome page was returned successfully.

After verification, the infrastructure was destroyed using:

```bash
terraform destroy
```

This demonstrated the complete Terraform lifecycle from provisioning to destruction.

## Key Learning Outcomes

* Understanding Infrastructure as Code
* Working with Terraform providers
* Creating Docker resources using Terraform
* Understanding Terraform plan and apply
* Managing Terraform state
* Verifying infrastructure independently
* Destroying infrastructure safely
* Using GitHub for project documentation and submission

## Interview Questions

### 1. What is Infrastructure as Code?

Infrastructure as Code is the practice of managing and provisioning infrastructure through configuration files instead of manually creating resources.

### 2. How does Terraform work?

Terraform uses configuration files to define infrastructure. It compares the desired configuration with the current state and creates, updates, or removes resources to achieve the desired state.

### 3. What is Terraform state?

Terraform state is a file that keeps track of the infrastructure resources managed by Terraform.

### 4. What is the difference between terraform plan and terraform apply?

`terraform plan` previews the changes Terraform intends to make.

`terraform apply` actually performs those changes.

### 5. What is a Terraform provider?

A provider is a plugin that allows Terraform to interact with a specific platform or service, such as AWS, Docker, Azure, or Kubernetes.

### 6. Why should Terraform state files not be committed to a public GitHub repository?

Terraform state can contain infrastructure information and potentially sensitive values. Therefore, state files should normally be excluded using `.gitignore`.

## Project Structure

```text
terraform-docker-task3/
│
├── main.tf
├── .gitignore
├── README.md
├── execution-logs.txt
│
└── screenshots/
    ├── 01-terraform-validate.png
    ├── 02-terraform-init.png
    ├── 03-terraform-plan.png
    ├── 04-terraform-apply.png
    ├── 05-docker-container.png
    ├── 06-terraform-state.png
    └── 07-terraform-destroy.png
```

## Conclusion

This project successfully demonstrates the use of Terraform for Infrastructure as Code by provisioning, verifying, managing, and destroying a Docker-based Nginx application.
