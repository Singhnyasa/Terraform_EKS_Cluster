# AWS EKS Cluster Architecture

## Project Overview

This project explores the architecture of Amazon Elastic Kubernetes Service (Amazon EKS) for running containerized applications on AWS.

The architecture uses a custom Amazon VPC with public and private subnets distributed across three Availability Zones to support high availability, network isolation, and scalable application deployment.


## Architecture Components

- **Amazon EKS:** Provides a managed Kubernetes control plane for orchestrating containerized applications.
- **Amazon VPC:** Provides an isolated network environment using the CIDR block `10.0.0.0/16`.
- **Availability Zones:** Distributes worker nodes across three Availability Zones to improve availability.
- **Public Subnets:** Host internet-facing components, such as an Application Load Balancer, and NAT Gateways where configured.
- **Private Subnets:** Host EC2 worker nodes that run Kubernetes workloads without requiring direct public IP addresses.
- **Internet Gateway:** Enables internet connectivity for resources with appropriate routing and security rules.
- **NAT Gateways:** Allow resources in private subnets to initiate outbound internet connections when required.
- **Application Load Balancer:** Routes incoming HTTP/HTTPS traffic to application workloads through the appropriate Kubernetes service and ingress configuration.
- **Amazon EC2 Worker Nodes:** Provide compute capacity for running Kubernetes pods.
- **Docker Hub:** Acts as a container image registry from which worker nodes can pull application images.
- **kubectl:** Command-line tool used by Kubernetes administrators to communicate with the EKS cluster.



## Application Traffic Flow

1. Application users send requests to the application's public endpoint.
2. The load balancer receives incoming traffic and routes it to the appropriate application workload.
3. Kubernetes schedules application pods on worker nodes in the private subnets.
4. Worker nodes pull container images from Docker Hub when required and permitted by the network configuration.
5. NAT Gateways provide outbound internet access to private resources when needed.
6. Administrators use `kubectl` to manage Kubernetes resources through the EKS API endpoint.

## High Availability and Security

- Distribute worker nodes across multiple Availability Zones.
- Keep application worker nodes in private subnets.
- Configure security groups and network access rules according to least-privilege principles.
- Use IAM roles and policies for EKS administration and worker-node permissions.
- Configure load balancing and health checks for application availability.
- Use appropriate monitoring, logging, and scaling configurations.

## Technologies Used

- Amazon Web Services (AWS)
- Amazon EKS
- Amazon VPC
- Amazon EC2
- Kubernetes
- Docker
- Docker Hub
- kubectl
- Application Load Balancer
- NAT Gateway
- IAM

## Key Learnings

- Understanding Amazon EKS architecture and managed Kubernetes control planes.
- Designing VPC networking across multiple Availability Zones.
- Understanding public and private subnet separation.
- Learning how load balancing, container registries, and Kubernetes worker nodes interact.
- Understanding the fundamentals of secure and highly available Kubernetes deployments.

## Future Enhancements

- Provision the infrastructure using Terraform.
- Deploy an application using Kubernetes Deployments and Services.
- Configure AWS Load Balancer Controller and Ingress.
- Implement CI/CD using GitHub Actions or Jenkins.
- Add Prometheus and Grafana for monitoring.
- Configure autoscaling and centralized logging.

