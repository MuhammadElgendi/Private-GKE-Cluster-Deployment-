# Project Overview
This project creates a virtual private cloud (VPC) on Google Cloud Platform (GCP) with two subnets: a management subnet and a restricted subnet.

## Project Output
![image](https://user-images.githubusercontent.com/28235504/214977647-36374783-34ad-486c-9abf-4bcd3a143e10.png)


## Management Subnet
The management subnet contains the following resources:

## NAT gateway
Private virtual machine (VM)
Restricted Subnet
  - The restricted subnet contains the following resources:
      - Private standard GKE cluster (private control plane)

## Constraints
  - The restricted subnet must not have access to the internet
  - All images deployed on GKE must come from GCR or Artifacts registry.
  - The VM must be private.
  - Deployment must be exposed to public internet with a public HTTP load balancer.
  - All infrastructure is to be created on GCP using Terraform.
  - Deployment on GKE can be done by Terraform or manually by kubectl tool.
  - The code to be built/dockerized and pushed to GCR is located at: https://github.com/atefhares/DevOps-Challenge-Demo-Code
  - Do not use the default compute service account while creating the GKE cluster. Create a custom service account and attach it to the nodes.
  - Only the management subnet can connect to the GKE cluster.

### Usage
  - Clone the repository from https://github.com/atefhares/DevOps-Challenge-Demo-Code
  - Install terraform
  - Run terraform init to initialize the project
  - Run terraform plan to preview the changes that will be made
  - Run terraform apply to create the resources
  - Run kubectl commands to deploy the application on GKE
  - To delete the resources, run terraform destroy
  - Note: Make sure you have the correct credentials set up to authenticate with GCP before running the terraform commands.
   
## Additional Steps
  - Build and push the Docker image of the application to GCR or Artifacts registry.
  - Create a custom service account for the GKE cluster, and assign the appropriate roles to it.
  - Use the custom service account while creating the GKE cluster.
  - Create a public HTTP load balancer to expose the deployment to the public internet.
  - Configure the management subnet to have access to the GKE cluster and the restricted subnet to not have access to the internet.
  - Update the application deployment files with the correct image repository and tag.
  - Use kubectl to deploy the application on the GKE cluster.

## Conclusion
This project demonstrates the use of Terraform to provision a VPC and its resources, and the use of GKE to deploy a private containerized application. The project also showcases the use of custom service accounts, GCR and public load balancer. By following the instructions above, you should be able to recreate the same infrastructure and deploy the application on GCP.

