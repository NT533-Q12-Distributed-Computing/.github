# NT533 – Distributed Computing  
## Final Project: Cloud-Native Distributed System on Amazon EKS

This GitHub organization is used to **manage all laboratories and the final project**
for the course **NT533 – Distributed Computing**.

It contains the complete source code, infrastructure definitions, configuration
automation, and documentation related to the design and deployment of a
cloud-native distributed system.

---

## Final Project Overview

This final project presents the **design and implementation of a highly available
distributed computing system** for microservices-based applications deployed on
**Amazon Elastic Kubernetes Service (EKS)**.

The primary objective of the project is to build a **fault-tolerant, scalable, and
resilient distributed architecture** capable of maintaining stable service
availability under varying workload conditions and infrastructure failures.

Within the project scope, a Kubernetes cluster is deployed on Amazon EKS following
a **Multi–Availability Zone (Multi-AZ)** model. The system integrates container
orchestration, load balancing, and application lifecycle management mechanisms to
ensure that application components continue to operate even in the presence of
node-level or Availability Zone failures.

This project emphasizes real-world distributed system principles, including
high availability, horizontal scalability, and infrastructure resilience.

---

## 1. Architecture Overview

The system architecture is designed following **cloud-native and distributed
computing best practices**, with a clear separation between infrastructure
provisioning and system configuration.

Infrastructure resources are provisioned using **Terraform** with a
**module-based architecture**, while higher-level configuration and operational
tasks are handled by dedicated automation tooling.

Detailed infrastructure implementation can be found in the Terraform Hub repository:

👉 **Terraform Hub**  
https://github.com/NT533-Q12-Distributed-Computing/terraform-hub

Terraform modules are organized to manage:

- Networking and routing
- Security and IAM
- Compute resources for Kubernetes platforms
- Supporting cloud-native infrastructure components

Terraform outputs are intentionally structured to enable seamless integration with
external automation tools and operational workflows.

---

## 1.1 Staging Environment

The **staging environment** serves as a controlled platform for provisioning and
validating a Kubernetes-ready infrastructure before applying similar architectural
patterns to production environments.

![Staging Environment Architecture](images/staging-env.png)

### Staging Environment Characteristics

- Deployment across multiple Availability Zones
- A dedicated VPC with isolated public and private subnets
- Private subnets for Kubernetes nodes and internal services
- Public subnets reserved for controlled management access
- Dedicated infrastructure for observability components
- Controlled outbound internet access via a NAT Gateway

The staging environment is primarily used to support a
**self-managed k0s Kubernetes cluster** deployed on EC2 instances.
It focuses on validating infrastructure correctness, network isolation,
and Kubernetes compatibility prior to production deployment.

---

## 1.2 Production Environment

The **production environment** represents a highly available, secure, and
cloud-native Kubernetes platform deployed on
**Amazon Elastic Kubernetes Service (EKS)**.

This environment is designed to closely reflect real-world enterprise Kubernetes
deployments on AWS, with an emphasis on scalability, resilience, and operational
best practices.

![Production Environment Architecture](images/prod-env.png)

### Production Environment Overview

The production architecture is deployed within a dedicated **AWS VPC** and spans
**multiple Availability Zones (AZs)** to ensure high availability and fault tolerance.

At a high level, the production environment consists of:

- An Amazon EKS cluster deployed across multiple private subnets
- Worker nodes distributed evenly across Availability Zones
- Kubernetes workloads running as containerized microservices
- A centralized observability infrastructure
- Secure management access through a controlled VPN entry point
- Public access to applications via an Application Load Balancer (ALB)
- Controlled outbound internet access via a NAT Gateway

This design follows AWS and Kubernetes best practices by isolating application
workloads in private subnets while exposing only well-defined entry points to the
public internet.

---

### Production Architecture Characteristics

#### Multi-AZ and High Availability Design

- The VPC is segmented across multiple Availability Zones
- Each Availability Zone contains one or more private subnets
- EKS worker nodes are distributed across all AZs
- Kubernetes scheduling mechanisms provide resilience against
  node-level and AZ-level failures

---

#### Amazon EKS Platform

- The Kubernetes control plane is fully managed by Amazon EKS
- Worker nodes operate exclusively in private subnets
- Node groups are designed for scalability and fault tolerance
- Kubernetes-native mechanisms handle pod scheduling and recovery

---

#### Application Traffic Flow

- External client traffic is routed through an
  **Application Load Balancer (ALB)**
- The ALB forwards traffic to Kubernetes services within the cluster
- Only explicitly defined services are exposed publicly
- Internal cluster communication remains private and isolated

---

#### Observability Infrastructure

- Observability components are provisioned as dedicated infrastructure
- Core capabilities include:
  - Metrics collection
  - Log aggregation
  - Distributed tracing
- This separation improves system stability and reduces the blast radius
  of monitoring components during failure scenarios

---

#### Secure Network Access

- Management access is provided through a controlled VPN entry point
- No direct administrative access is exposed to the public internet
- Infrastructure access follows the principle of least privilege

---

## Author

This project is developed as part of the **NT533 – Distributed Computing** course,
with a focus on **cloud-native system design**, **distributed computing principles**,
and **high-availability Kubernetes architectures**.
