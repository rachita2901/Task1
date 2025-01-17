# Cloud & DevOps Engineer Assessment

This repository contains the solution for the Cloud & DevOps Engineer Assessment, where I deployed a simple web application in a cloud-based Kubernetes environment. The solution ensures proper logging and monitoring.

#Solution Components

1. Terraform IAC Templates
   Terraform templates used to provision cloud infrastructure on AWS. These scripts automate the creation of resources like virtual networks, storage, and Kubernetes clusters.

2. Kubernetes Deployment Files
   Kubernetes YAML files for deploying the containerized web application to the Kubernetes cluster. These include deployments, services.

3. Monitoring with Prometheus
   Prometheus configuration to monitor the health and performance of the deployed application. This setup includes necessary scrape configurations and alerting rules.

4. Dockerfile
   A simple Dockerfile used to containerize the web application. The container runs a static page as part of the application.

#Deployment Instructions

### Prerequisites

- Terraform: Ensure Terraform is installed. Follow [this link](https://www.terraform.io/downloads.html) to download Terraform.
- Kubernetes Cluster: A cloud-based Kubernetes cluster (e.g., Elastic Kubernetes Service) should be provisioned. You can use the provided Terraform templates for provisioning.
- kubectl: Install kubectl to interact with the Kubernetes cluster. Follow the [kubectl installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/) for setup.

### Steps to Deploy

1. Provision Cloud Infrastructure:
   - Navigate to the `iac/` directory and initialize the Terraform environment:
      terraform init
   - Before applying the changes check any resoruces need to be created or modified
     terrafrom plan      
   - Apply the Terraform configuration to provision the infrastructure:
     terraform apply
   
2. Containerize the Application:
   - Build the Docker image for the web application:
     docker build -t web-app .
   - Push the image to a Docker registry (e.g., Docker Hub).

3. Deploy to Kubernetes:
   - Apply the Kubernetes YAML files to deploy the application:
     kubectl apply -f kubernetes/
    
4. Set up Monitoring:
   - Install Prometheus in your Kubernetes cluster. You can use Helm or apply the necessary configurations manually.
   - Ensure the Prometheus configuration file is correctly set up to scrape metrics from your application.

5. Access the Web Application:
   - Use 'kubectl' to get the external IP.

### Troubleshooting

- If the application is not accessible, check the Kubernetes pod status:
  kubectl get pods
- If Prometheus metrics are not visible, check if Prometheus is properly scraping the application.
