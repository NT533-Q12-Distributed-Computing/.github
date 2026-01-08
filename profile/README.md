# NT533 – Distributed Computing

This GitHub organization is used to **manage all laboratories and the final project**
for the course **NT533 – Distributed Computing**.

It contains the complete source code, infrastructure definitions, automation scripts,
and technical documentation related to the design and deployment of a
**cloud-native distributed system**.

---

## Final Project

### Cloud-Native Highly Available Amazon EKS System for Microservices Applications

This is the **final project** of the NT533 – Distributed Computing course.

The project focuses on the **design and implementation of a highly available
distributed system on Amazon Elastic Kubernetes Service (EKS)** for
microservices-based applications.

The main objectives of the final project include:

- Designing a fault-tolerant distributed architecture
- Deploying Kubernetes clusters in a Multi–Availability Zone (Multi-AZ) configuration
- Ensuring service continuity under node-level and Availability Zone failures
- Applying real-world cloud-native and distributed system principles
- Demonstrating scalability, resilience, and operational stability

The final system reflects production-oriented design patterns commonly used
in modern cloud-native platforms.

---

### 1. Overview

This organization consolidates all practical work and the final project developed
throughout the NT533 course, with a focus on **distributed computing principles**,
**cloud-native system design**, and **high-availability architectures**.

The primary technical scope of the work includes:

- Infrastructure provisioning using Infrastructure as Code (IaC)
- Kubernetes-based distributed systems
- Multi–Availability Zone (Multi-AZ) deployments on AWS
- Fault tolerance, scalability, and resilience for microservices architectures
- Clear separation between infrastructure, platform, and application layers

---

### 2. Cloud Architecture

The system architecture follows **cloud-native and distributed computing best practices**,
with a clear separation between **infrastructure provisioning** and
**configuration / operational workflows**.

#### 2.1 Infrastructure Provisioning with Terraform

The infrastructure layer is provisioned using **Terraform** with a
**module-based architecture**.

Each Terraform module is responsible for a specific layer of the infrastructure,
including:

- Networking and routing
- Security and IAM
- Compute resources for Kubernetes platforms
- Supporting cloud-native components

Terraform outputs are intentionally structured to be consumed by
external automation tools, enabling seamless integration with
configuration management and operational workflows.

For detailed infrastructure implementation, refer to:  
👉 **[terraform-hub](https://github.com/NT533-Q12-Distributed-Computing/terraform-hub)**

---

### 2.2 Staging Environment

The **staging environment** serves as a controlled platform for
provisioning and validating a Kubernetes-ready infrastructure
before applying similar architectural patterns to production
environments.

![Staging Environment Architecture](../images/staging-env.png)

#### Staging Environment Characteristics

- Deployment across multiple Availability Zones
- A dedicated VPC with isolated private and public subnets
- Private subnets for Kubernetes nodes and internal services
- Public subnets reserved for controlled management access
- Dedicated infrastructure for observability components
- Controlled outbound internet access via a NAT Gateway

The staging environment is primarily used to support a
**self-managed k0s Kubernetes cluster** deployed on EC2 instances.
It focuses on validating infrastructure correctness, network isolation,
and Kubernetes compatibility prior to production deployment.

---

#### 2.3 Production Environment

The **production environment** represents a highly available,
secure, and cloud-native Kubernetes platform deployed on
**Amazon Elastic Kubernetes Service (EKS)**.

This environment is designed to closely reflect real-world
enterprise Kubernetes deployments on AWS, with an emphasis on
scalability, resilience, and operational best practices.

![Production Environment Architecture](../images/prod-env.png)

### Production Environment Overview

The production architecture is deployed within a dedicated
**AWS VPC** and spans **multiple Availability Zones (AZs)** to
ensure high availability and fault tolerance.

At a high level, the production environment consists of:

- An Amazon EKS cluster deployed across multiple private subnets
- Worker nodes distributed evenly across Availability Zones
- Kubernetes workloads running as containerized microservices
- A centralized observability infrastructure
- Secure management access through a controlled VPN entry point
- Public access to applications via an Application Load Balancer (ALB)
- Controlled outbound internet access via a NAT Gateway

This design follows AWS and Kubernetes best practices by isolating
application workloads in private subnets while exposing only
well-defined entry points to the public internet.

---

## Author

Developed as part of the **NT533 – Distributed Computing** course, with a focus on:

- Cloud-native system design  
- Distributed computing principles  
- High-availability Kubernetes architectures  
