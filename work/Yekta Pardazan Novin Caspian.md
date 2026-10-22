---
title: "AWS Flight Pricing Platform — Yekta Pardazan Novin Caspian"
date: 2026-01-01
type: project
lang: en
layout: case-study
role: "Platform / DevOps Engineer"
technologies:
  - AWS
  - Amazon EKS
  - Kubernetes
  - Terraform
  - Docker
  - Jenkins
  - GitHub
  - Amazon ECR
  - Amazon RDS
  - Amazon S3
  - IAM
  - Prometheus
  - Grafana
permalink: /work/yekta-pardazan/
---

# AWS Flight Pricing Platform

**Role:** Platform / DevOps Engineer  
**Period:** March 2023 – January 2026  
**Platform:** AWS, Amazon EKS, Terraform, Kubernetes

## Overview

I worked on the infrastructure and delivery workflows for a high-availability B2B flight-pricing platform that aggregated airline and travel-agency data from multiple sources.

The platform ran on AWS, using Amazon EKS to orchestrate containerized workloads, Amazon RDS for PostgreSQL, and Amazon S3 for object storage. Its workload mix included API services, data ingestion, data processing, batch jobs, and supporting platform components.

My work focused on AWS infrastructure provisioning, Kubernetes workload placement, Terraform automation, container delivery, IAM and workload security, monitoring, and production troubleshooting.

The key engineering challenges involved keeping infrastructure changes isolated across environments, matching compute capacity to workload requirements, maintaining private image access, and controlling AWS permissions at workload level.

## My Role and Contributions

My responsibilities covered the implementation and operation of platform infrastructure and delivery workflows.

- Provisioned and managed AWS infrastructure using Terraform.
- Worked with Amazon EKS, VPC networking, IAM, EC2 capacity, Amazon ECR, Amazon RDS, and Amazon S3.
- Managed Kubernetes node groups and workload placement to address different resource and availability requirements.
- Supported Docker image build and delivery workflows using GitHub and Jenkins.
- Applied infrastructure deployment safeguards across development, staging, and production.
- Implemented workload-level AWS access using IAM Roles for Service Accounts (IRSA).
- Investigated Kubernetes scheduling, resource-pressure, registry-connectivity, and IAM permission issues.
- Used Prometheus and Grafana to support infrastructure and workload monitoring.
- Worked with Trivy, SonarQube, and JFrog as part of the software delivery toolchain.

My contribution focused on platform and DevOps engineering. It did not mean ownership of every application or the entire platform architecture.

## Architecture

The platform had two connected business flows: collecting and processing flight-pricing data from multiple sources, and serving customer requests through API workloads. The diagram separates the data flow from the external API access path and the Kubernetes/AWS configuration layer.

<figure style="margin: 1.5rem 0;">
  <svg viewBox="0 0 1000 1010" role="img" aria-labelledby="yekta-architecture-title yekta-architecture-desc" xmlns="http://www.w3.org/2000/svg" style="display:block;width:100%;height:auto;max-width:1000px;margin:0 auto;">
    <title id="yekta-architecture-title">Yekta flight-pricing platform architecture</title>
    <desc id="yekta-architecture-desc">Two flows are shown: external flight and travel-agency data is ingested and processed on EKS, then stored in S3 and RDS PostgreSQL; B2B customer requests enter through an ALB and reach API workloads. Ingress rules and the AWS Load Balancer Controller are shown as the configuration layer for the ALB. A Kubernetes Service provides stable in-cluster access to selected API pods.</desc>
    <defs>
      <marker id="yekta-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L0,6 L9,3 z" fill="#64748b"/></marker>
      <marker id="yekta-arrow-blue" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L0,6 L9,3 z" fill="#2563eb"/></marker>
    </defs>
    <rect x="1" y="1" width="998" height="1008" rx="18" fill="#f8fafc" stroke="#cbd5e1"/>
    <text x="500" y="36" text-anchor="middle" font-size="21" font-weight="700" fill="#0f172a">YEKTA FLIGHT-PRICING PLATFORM</text>
    <text x="500" y="60" text-anchor="middle" font-size="13" fill="#475569">High-level architecture • data platform and customer API</text>

    <rect x="290" y="82" width="420" height="66" rx="12" fill="#e2e8f0" stroke="#94a3b8"/>
    <text x="500" y="109" text-anchor="middle" font-size="17" font-weight="700" fill="#0f172a">Airline and travel-agency sources</text>
    <text x="500" y="130" text-anchor="middle" font-size="13" fill="#334155">External flight and pricing data</text>
    <path d="M500 148 V177" stroke="#64748b" stroke-width="2.5" marker-end="url(#yekta-arrow)"/>

    <rect x="290" y="183" width="420" height="68" rx="12" fill="#dbeafe" stroke="#60a5fa"/>
    <text x="500" y="211" text-anchor="middle" font-size="17" font-weight="700" fill="#1e3a8a">Data-ingestion workloads</text>
    <text x="500" y="233" text-anchor="middle" font-size="13" fill="#1e40af">Amazon EKS • containerized workloads</text>
    <path d="M500 251 V280" stroke="#64748b" stroke-width="2.5" marker-end="url(#yekta-arrow)"/>

    <rect x="290" y="286" width="420" height="68" rx="12" fill="#dbeafe" stroke="#60a5fa"/>
    <text x="500" y="314" text-anchor="middle" font-size="17" font-weight="700" fill="#1e3a8a">Data-processing workloads</text>
    <text x="500" y="336" text-anchor="middle" font-size="13" fill="#1e40af">Processing and batch capacity on EKS</text>
    <path d="M500 354 V378 H255 V401" fill="none" stroke="#64748b" stroke-width="2.5" marker-end="url(#yekta-arrow)"/>
    <path d="M500 378 H745 V401" fill="none" stroke="#64748b" stroke-width="2.5" marker-end="url(#yekta-arrow)"/>

    <rect x="90" y="407" width="330" height="82" rx="12" fill="#dcfce7" stroke="#4ade80"/>
    <text x="255" y="439" text-anchor="middle" font-size="19" font-weight="700" fill="#14532d">Amazon S3</text>
    <text x="255" y="463" text-anchor="middle" font-size="14" fill="#166534">Object storage</text>
    <rect x="580" y="407" width="330" height="82" rx="12" fill="#dcfce7" stroke="#4ade80"/>
    <text x="745" y="439" text-anchor="middle" font-size="19" font-weight="700" fill="#14532d">Amazon RDS</text>
    <text x="745" y="463" text-anchor="middle" font-size="14" fill="#166534">PostgreSQL • relational data</text>

    <text x="500" y="532" text-anchor="middle" font-size="17" font-weight="700" fill="#0f172a">Customer API access path</text>
    <rect x="45" y="553" width="210" height="70" rx="12" fill="#e2e8f0" stroke="#94a3b8"/>
    <text x="150" y="581" text-anchor="middle" font-size="17" font-weight="700" fill="#0f172a">B2B customers</text>
    <text x="150" y="603" text-anchor="middle" font-size="13" fill="#334155">HTTPS API requests</text>
    <path d="M255 588 H300" stroke="#2563eb" stroke-width="2.5" marker-end="url(#yekta-arrow-blue)"/>

    <rect x="310" y="553" width="210" height="70" rx="12" fill="#dbeafe" stroke="#60a5fa"/>
    <text x="415" y="581" text-anchor="middle" font-size="18" font-weight="700" fill="#1e3a8a">AWS ALB</text>
    <text x="415" y="603" text-anchor="middle" font-size="13" fill="#1e40af">HTTP/HTTPS routing</text>
    <path d="M520 588 H565" stroke="#2563eb" stroke-width="2.5" marker-end="url(#yekta-arrow-blue)"/>

    <rect x="575" y="553" width="365" height="70" rx="12" fill="#dbeafe" stroke="#60a5fa"/>
    <text x="757" y="581" text-anchor="middle" font-size="18" font-weight="700" fill="#1e3a8a">API workloads on EKS</text>
    <text x="757" y="603" text-anchor="middle" font-size="13" fill="#1e40af">ALB forwards to configured targets</text>

    <rect x="575" y="647" width="365" height="68" rx="12" fill="#f1f5f9" stroke="#94a3b8"/>
    <text x="757" y="674" text-anchor="middle" font-size="17" font-weight="700" fill="#0f172a">API Pods</text>
    <text x="757" y="696" text-anchor="middle" font-size="13" fill="#334155">Replicas can scale independently</text>
    <path d="M757 623 V641" stroke="#64748b" stroke-width="2.5" marker-end="url(#yekta-arrow)"/>

    <rect x="60" y="647" width="455" height="68" rx="12" fill="#fef3c7" stroke="#f59e0b"/>
    <text x="287" y="674" text-anchor="middle" font-size="17" font-weight="700" fill="#92400e">Kubernetes Service (ClusterIP)</text>
    <text x="287" y="696" text-anchor="middle" font-size="13" fill="#92400e">Stable in-cluster endpoint for selected API Pods</text>
    <path d="M515 681 H565" stroke="#64748b" stroke-width="2.5" marker-end="url(#yekta-arrow)"/>

    <text x="500" y="757" text-anchor="middle" font-size="17" font-weight="700" fill="#0f172a">Ingress configuration layer</text>
    <rect x="75" y="779" width="360" height="74" rx="12" fill="#ede9fe" stroke="#a78bfa"/>
    <text x="255" y="808" text-anchor="middle" font-size="17" font-weight="700" fill="#5b21b6">Kubernetes Ingress</text>
    <text x="255" y="831" text-anchor="middle" font-size="13" fill="#6d28d9">Declares host/path routing rules</text>
    <rect x="565" y="779" width="360" height="74" rx="12" fill="#ede9fe" stroke="#a78bfa"/>
    <text x="745" y="808" text-anchor="middle" font-size="17" font-weight="700" fill="#5b21b6">AWS Load Balancer Controller</text>
    <text x="745" y="831" text-anchor="middle" font-size="13" fill="#6d28d9">Watches resources and configures ALB</text>
    <path d="M435 816 H558" fill="none" stroke="#7c3aed" stroke-width="2.5" stroke-dasharray="7 6" marker-end="url(#yekta-arrow)"/>
    <path d="M745 779 V740 H415 V630" fill="none" stroke="#7c3aed" stroke-width="2.5" stroke-dasharray="7 6" marker-end="url(#yekta-arrow)"/>
    <text x="500" y="873" text-anchor="middle" font-size="12" fill="#6d28d9">Dashed arrows = configuration/control relationship, not request traffic</text>

    <rect x="55" y="897" width="890" height="83" rx="12" fill="#ffffff" stroke="#cbd5e1"/>
    <text x="75" y="922" font-size="14" font-weight="700" fill="#0f172a">Platform delivery and operations</text>
    <text x="75" y="946" font-size="13" fill="#334155">GitHub → Jenkins → Docker build → Amazon ECR</text>
    <text x="75" y="966" font-size="13" fill="#334155">Terraform → AWS infrastructure • Prometheus / Grafana → monitoring</text>
  </svg>
  <figcaption style="margin-top:0.75rem;color:#64748b;font-size:0.92rem;line-height:1.5;">
    <strong>How to read this architecture:</strong> the upper flow collects and processes source data before storing it in S3 and RDS. The lower flow serves B2B API requests through the ALB to the configured API targets. Ingress declares routing rules, while the AWS Load Balancer Controller watches Kubernetes resources and configures the ALB. The Service provides a stable in-cluster endpoint for API pods. The exact ALB target type and traffic path depend on the cluster configuration.
  </figcaption>
</figure>

Amazon EKS provided the orchestration layer for containerized application workloads. Amazon RDS and S3 supported the platform’s data requirements, while Amazon ECR stored container images used by Kubernetes workloads.

The diagram is a high-level architecture view. It separates the application data path from the control relationship used to configure load balancing; the exact target type and routing details depend on the deployed configuration.

Delivery and infrastructure workflows remained separate: Terraform managed AWS infrastructure, while GitHub and Jenkins supported source changes, builds, and image publication.

## Kubernetes Workload Isolation

### Dedicated node groups

The platform used separate node groups for different workload categories rather than treating all worker nodes as one shared pool.

| Workload category | Capacity approach | Engineering rationale |
|---|---|---|
| System | On-Demand | Maintain predictable capacity for core platform components |
| API | On-Demand | Support application workloads requiring predictable performance |
| Ingestion | Mixed capacity | Balance compute requirements, availability, and cost |
| Data processing | Dedicated capacity | Accommodate workloads with distinct resource requirements |
| Batch | Spot | Reduce compute costs for interruption-tolerant jobs |
| Security | Dedicated On-Demand capacity | Separate security-related components from general application workloads |

This public summary intentionally omits exact instance types, configured node-count ranges, and purchasing percentages.

### Scheduling and capacity decisions

Kubernetes taints, tolerations, and affinity rules provided controls for directing workloads to their intended node groups.

The design balanced three competing requirements:

1. **Availability:** Keep critical application workloads on predictable On-Demand capacity.
2. **Cost:** Use Spot capacity where workload interruption tolerance made it appropriate.
3. **Isolation:** Reduce competition between workloads with different CPU and memory requirements.

The choice of Spot was workload-dependent rather than a blanket cost-saving measure. Batch processing could use more aggressive scaling, while API workloads required a more predictable capacity strategy.

## Infrastructure as Code with Terraform

Terraform was used to provision and manage AWS infrastructure, including VPC resources, IAM configuration, EC2 capacity, and EKS-related infrastructure.

The infrastructure workflow used:

- Version-controlled Terraform configuration.
- Amazon S3 for remote state storage.
- DynamoDB for state locking.
- Environment-specific configuration for development, staging, and production.

Remote state allowed infrastructure state to be managed outside individual workstations, while state locking helped coordinate concurrent Terraform operations.

A production incident involving incorrect backend configuration exposed the need for stronger separation between environment selection and infrastructure execution. The resulting safeguards are described in the first troubleshooting case below.

## CI/CD and Container Delivery

The delivery workflow used GitHub, Jenkins, Docker, and Amazon ECR.

The main stages were:

1. Source code was maintained in GitHub.
2. Jenkins supported the build and delivery workflow.
3. Docker images were built for application workloads.
4. Images were published to Amazon ECR.
5. Kubernetes workloads consumed the published images.

Trivy and SonarQube supported security and code-quality checks within the delivery toolchain. JFrog was used for artifact management.

Separating image creation and registry publication from infrastructure provisioning made the responsibilities of the build and infrastructure workflows clearer.

## IAM, Workload Identity, and Security

### IAM Roles for Service Accounts

Some Kubernetes workloads needed access to AWS services, including S3 and AWS-related storage operations.

I implemented IAM Roles for Service Accounts (IRSA) to provide workload-specific AWS permissions through Kubernetes service accounts.

The implementation involved:

- Enabling the EKS cluster's OIDC identity integration.
- Creating IAM roles for the workloads that required AWS access.
- Associating the roles with the relevant Kubernetes service accounts.
- Aligning workload permissions with their specific AWS access requirements.

This reduced reliance on shared worker-node IAM permissions for workloads that needed different access levels.

The approach supported least-privilege access by making AWS permissions more specific to workload identity instead of assigning all permissions at node level.

### Private registry connectivity

The platform also required a secure path for private-subnet worker nodes to retrieve container images from Amazon ECR.

VPC endpoint configuration, DNS, security groups, and IAM permissions were important parts of this connectivity path. A failure in this layer caused a deployment incident described below.

## Monitoring and Observability

Prometheus and Grafana supported monitoring of infrastructure and Kubernetes workloads.

The operational focus included resource pressure, workload behavior, and application symptoms such as increased latency. Kubernetes resource metrics and scheduling information helped investigate whether issues were related to workload configuration or available node capacity.

Monitoring was also relevant when validating infrastructure and scheduling changes. Where a quantified improvement is reported, it should reflect an actual measurement rather than an assumed result.

## Selected Engineering Challenges

### 1. Terraform State Isolation and Production Safety

**Problem**

The platform used Terraform across development, staging, and production, with remote state stored in S3 and locking managed through DynamoDB.

A team member intended to apply a change to staging, but the backend configuration pointed to the production state. The changes intended for staging were consequently applied to production, modifying resources unexpectedly and introducing state drift and potential downtime risk.

**Investigation and root cause**

I investigated the Terraform execution and identified two contributing weaknesses:

- The backend configuration did not correctly isolate the intended environment.
- The workflow lacked sufficient validation before applying infrastructure changes.

The incident showed that separate environment configurations are not enough when the execution process does not verify which environment and state are being targeted.

**Remediation**

I introduced four safeguards:

1. **Separate state paths:** Enforced distinct S3 state-key paths for development, staging, and production.
2. **Plan review:** Made `terraform plan` a required review step before applying changes.
3. **Production approval:** Routed production infrastructure changes through controlled CI/CD pipelines with manual approval.
4. **Pre-apply validation:** Added checks to verify the intended environment and backend configuration before Terraform execution.

**Outcome**

These controls strengthened environment isolation and reduced the risk of unintended production changes. They also made infrastructure changes more reviewable and established a more controlled process for production deployments.

**Engineering lesson:** Terraform state isolation is part of production change management. Backend configuration, plan review, and deployment authorization need to work together.

### 2. EKS ImagePullBackOff After Moving Worker Nodes to Private Subnets

**Problem**

During a security-hardening initiative, worker nodes were moved into private subnets to reduce direct Internet exposure.

After the change, newly deployed pods entered the `ImagePullBackOff` state because the worker nodes could not retrieve their container images from Amazon ECR.

**Investigation**

I used `kubectl describe pod` to inspect the affected workloads and investigated worker-node connectivity and VPC networking behavior.

The investigation connected the deployment failure to the network path required for private-subnet nodes to access the container registry.

**Root cause**

The required Amazon ECR VPC endpoints had not been configured after the worker nodes were moved into private subnets.

Without the required private connectivity, the nodes could not retrieve images from ECR through the intended network path.

**Resolution**

I configured the required ECR interface VPC endpoints and validated the associated security-group and DNS configuration.

**Validation and impact**

After private connectivity was established, the nodes were able to pull the required images and the affected deployments recovered. The environment could retain private worker-node networking without relying on direct Internet access for image retrieval.

**Engineering lesson:** A Kubernetes deployment can fail because of an underlying cloud-networking dependency. Successful image delivery requires the registry, network path, DNS, and access controls to work together.

### 3. Workload-Level IAM Permissions with IRSA

**Problem**

Some workloads needed access to AWS services, including S3, while a storage CSI driver required permissions for AWS-related storage operations.

Some pods encountered `AccessDenied` errors because the existing IAM permissions were not appropriate for every workload.

**Investigation**

I reviewed pod logs and investigated the permissions available to the failing workloads.

Some AWS access depended on the worker-node IAM role. This approach was insufficient for workloads with different permission requirements: workloads that did not need AWS access were unaffected, while some applications and storage operations lacked the permissions they required.

**Resolution**

I implemented IRSA by enabling OIDC integration, creating dedicated IAM roles, and associating those roles with Kubernetes service accounts.

This allowed supported workloads to obtain AWS permissions through their own service-account identity instead of relying solely on the shared node role.

**Security impact**

The change improved workload-level permission isolation and supported least-privilege access. It also reduced the need to grant broad worker-node permissions to support individual applications.

**Engineering lesson:** Workload identity is a critical part of EKS security. Dedicated IAM roles associated with service accounts provide a more granular access model than relying on a shared node role.

## Capacity and Cost Optimization

The platform used different EC2 instance families and purchasing strategies to reflect workload requirements.

Spot capacity was used for selected ingestion and batch workloads, while On-Demand instances supported system and API workloads. Dedicated node groups provided a way to manage capacity and workload placement independently.

Infrastructure cost optimization involved matching capacity to workload behavior rather than minimizing instance cost in isolation. Reliability, interruption tolerance, scaling requirements, and operational recovery all influenced the appropriate capacity strategy.

## Operational Outcomes

The work focused on improving the repeatability of infrastructure provisioning, controlling production changes, and aligning Kubernetes capacity with application requirements.

The reported outcomes included:

- Reducing infrastructure provisioning effort from days to hours.
- Moving from weekly releases to multiple releases per day.
- Achieving approximately 30% lower infrastructure cost through capacity and node-group optimization.
- Supporting a platform handling several hundred thousand transactions per day.

These figures describe the reported operational results associated with the platform. Their measurement basis and attribution should remain consistent with the actual project records and the specific changes I contributed to.

## Constraints and Engineering Considerations

The work involved several connected operational concerns:

- **Environment isolation:** Terraform backend configuration and deployment controls needed to prevent cross-environment changes.
- **Workload scheduling:** Node-group separation and Kubernetes placement policies needed to reflect different resource profiles.
- **Private networking:** Worker nodes needed secure registry connectivity after moving into private subnets.
- **Workload identity:** AWS permissions needed to match the access requirements of individual workloads.
- **Capacity strategy:** Spot and On-Demand capacity needed to balance cost against availability and interruption tolerance.
- **Observability:** Resource metrics and application symptoms needed to be considered together during troubleshooting.

These concerns reinforced that reliable platform engineering requires coordination between Kubernetes, cloud infrastructure, security, and delivery workflows.

## Technologies

**Cloud and infrastructure:** AWS, Amazon EKS, EC2, VPC, IAM, Amazon ECR, Amazon RDS for PostgreSQL, Amazon S3, Terraform

**Containers and orchestration:** Docker, Kubernetes, node groups, taints and tolerations, affinity rules, Cluster Autoscaler

**Infrastructure delivery:** Terraform remote state, S3 backend, DynamoDB state locking, CI/CD approval controls

**Workload identity and networking:** IAM Roles for Service Accounts (IRSA), OIDC, VPC endpoints, security groups

**Build, security, and artifacts:** GitHub, Jenkins, Trivy, SonarQube, JFrog

**Monitoring:** Prometheus, Grafana

## What I Learned

This work reinforced the importance of connecting infrastructure design with operational safeguards.

Terraform state isolation and production approval controls protect against unintended infrastructure changes. Kubernetes node-group separation helps align workload placement and capacity with application requirements. Private-subnet deployments depend on the correct registry connectivity, and IRSA provides a more granular model for granting AWS permissions to workloads.

Across these areas, effective platform engineering means investigating failures across the full dependency chain—from Kubernetes configuration and IAM permissions to VPC networking and infrastructure automation.

*Sensitive infrastructure identifiers and configuration details have been omitted.*
