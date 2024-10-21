# Production-Level-Blue-Green-Deployment-CICD-Pipeline

Certainly! Here’s a structured summary based on the provided video script for your project documentation on implementing a Blue-Green Deployment CI/CD pipeline. You can adjust the content as needed to fit your style and include additional details specific to your implementation.

---

# Project Documentation: Blue-Green Deployment CI/CD Pipeline

## 1. Introduction

This project demonstrates the implementation of a Blue-Green Deployment strategy within a CI/CD pipeline. The primary objective is to enable seamless application upgrades with zero downtime, ensuring a smooth transition between different application versions.

## 2. Overview

The Blue-Green Deployment strategy involves maintaining two identical environments—Blue and Green. The application is initially deployed in the Blue environment. When upgrades or new features are developed, the application is deployed in the Green environment. Traffic is then switched from Blue to Green, allowing for a live update without any downtime. 

### Key Benefits:
- **Zero Downtime**: Users can access the application without interruptions during upgrades.
- **Easy Rollback**: If issues arise after switching, traffic can be redirected back to the Blue environment quickly.

## 3. Project Scope

- **Environment Setup**: Set up an Amazon EKS cluster for deployment.
- **Application Configuration**: Deploy a Java and MySQL application.
- **CI/CD Pipeline**: Configure a CI/CD pipeline to automate the deployment process and traffic switching.
- **Tools Used**: AWS EKS, Jenkins, SonarQube, Nexus, Docker, Kubernetes.

## 4. Deployment Strategy

### 4.1 Initial Deployment

1. **Blue Environment**: 
   - Deploy the initial version (Version 1) of the application in the Blue environment, including the MySQL database and application pods.
   - The application pod will be connected to the MySQL service using a Cluster IP for internal communication.
   - Expose the application through a LoadBalancer service type.

### 4.2 Upgrading to Green Environment

1. **Green Environment**:
   - When new features are developed, deploy Version 2 of the application in the Green environment.
   - Configure the LoadBalancer to direct traffic from the Blue environment to the Green environment.

### 4.3 Traffic Switching

- Implement the CI/CD pipeline to manage the deployment process:
  - Use a parameterized build to select the environment (Blue or Green).
  - Execute the pipeline stages to switch traffic seamlessly.

## 5. Infrastructure Setup

### 5.1 Create Virtual Machine

To set up the infrastructure for the Blue-Green Deployment, a virtual machine will be created to run Terraform commands for creating the EKS cluster.

1. **VM Configuration**:
   - **Name and Tags**: Ubuntu-Server
   - **Application and OS**: Ubuntu Server 24.04 LTS (HVM), SSD Volume Type
   - **Instance Type**: t2.medium
   - **Key Pair**: [Insert key pair details here]

   ![Virtual Machine Configuration](https://github.com/user-attachments/assets/6943d650-dd9a-43e7-bcaf-8fd3b09de668)

2. **Connect to VM**:
   - Use SSH or a tool like MobaXterm to connect to the virtual machine.

   ![Connect to VM](https://github.com/user-attachments/assets/71d292cb-d5ec-4133-8482-7282687eddc8)

### 5.2 Open Necessary Ports

Ensure that the necessary ports are open in the security group for communication. This step is crucial for allowing traffic between the various components of the EKS cluster and the application.

---

Feel free to add any additional details or instructions based on your project's specific requirements!

2. **EKS Cluster Configuration**:
   - Deploy and configure the EKS cluster to host the application and manage Kubernetes resources.
