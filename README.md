# Amazon ECS (amazon-ecs)
Amazon Elastic Container Service (ECS) is a fully managed container orchestration service that makes it easy to deploy, manage, and scale containerized applications.

**URL:** [Visit APIs.json URL](https://aws.amazon.com/ecs/)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Amazon, Aws, Containers, Docker, Ecs, Orchestration

## Timestamps

- **Created:** 2024 
- **Modified:** 2026-04-18 

## APIs

### Amazon ECS API
The Amazon ECS API provides programmatic access to manage containerized applications using Docker containers.

**Human URL:** [https://aws.amazon.com/ecs/](https://aws.amazon.com/ecs/)

#### Tags:

 - Cloud, Containers, Docker, Microservices, Orchestration

#### Properties

- [Documentation](https://docs.aws.amazon.com/ecs/)
- [OpenAPI](openapi/amazon-ecs-openapi.yml)
- [APIReference](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/Welcome.html)
- [GettingStarted](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/getting-started.html)
- [Pricing](https://aws.amazon.com/ecs/pricing/)
- [CLI](https://docs.aws.amazon.com/cli/latest/reference/ecs/)

### Amazon ECS Service Connect API
Amazon ECS Service Connect provides management of service-to-service communication as Amazon ECS configuration, building both service discovery and a service mesh for connecting services within and across clusters and VPCs.

**Human URL:** [https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-connect.html](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-connect.html)

#### Tags:

 - Containers, Microservices, Networking, Service-Discovery, Service-Mesh

#### Properties

- [Documentation](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-connect.html)
- [APIReference](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ServiceConnectConfiguration.html)
- [GitHubRepository](https://github.com/aws/amazon-ecs-service-connect-agent)

### Amazon ECS Anywhere API
Amazon ECS Anywhere extends Amazon ECS to support registering external instances such as on-premises servers or virtual machines to your Amazon ECS cluster, allowing you to run and manage containerized workloads on your own infrastructure.

**Human URL:** [https://aws.amazon.com/ecs/anywhere/](https://aws.amazon.com/ecs/anywhere/)

#### Tags:

 - Containers, Edge, Hybrid-Cloud, On-Premises, Orchestration

#### Properties

- [Documentation](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs-anywhere.html)
- [GettingStarted](https://aws.amazon.com/ecs/anywhere/getting-started/)
- [Tutorials](https://github.com/aws-containers/ecs-anywhere-tutorial)

### AWS Copilot CLI
AWS Copilot is an open source command line interface that simplifies building, releasing, and operating production-ready containerized applications on Amazon ECS and AWS Fargate, providing common cloud architectures and workflows.

**Human URL:** [https://aws.amazon.com/containers/copilot/](https://aws.amazon.com/containers/copilot/)

#### Tags:

 - Cli, Containers, Deployment, Devops, Fargate

#### Properties

- [Documentation](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Copilot.html)
- [GitHubRepository](https://github.com/aws/copilot-cli)
- [GettingStarted](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/getting-started-aws-copilot-cli.html)

## Common Properties

- [Documentation](https://docs.aws.amazon.com/ecs/)
- [Pricing](https://aws.amazon.com/ecs/pricing/)
- [FAQ](https://aws.amazon.com/ecs/faqs/)
- [Features](https://aws.amazon.com/ecs/features/)
- [GettingStarted](https://aws.amazon.com/ecs/getting-started/)
- [Resources](https://aws.amazon.com/ecs/resources/)
- [Partners](https://aws.amazon.com/ecs/partners/)
- [Blog](https://aws.amazon.com/blogs/aws/category/compute/amazon-elastic-container-service/)
- [StatusPage](https://status.aws.amazon.com/)
- [SDK](https://aws.amazon.com/tools/)
- [CLI](https://docs.aws.amazon.com/cli/latest/reference/ecs/)
- [Security](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/security.html)
- [Compliance](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/security-compliance.html)
- [BestPractices](https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/intro.html)
- [Troubleshooting](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/troubleshooting.html)
- [Console](https://console.aws.amazon.com/ecs/home)
- [KnowledgeCenter](https://repost.aws/tags/TAd-wgX2x3QgSxyelEN6raFg/amazon-elastic-container-service)
- [ChangeLog](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/document_history.html)
- [GitHubOrganization](https://github.com/aws)

## Features

| Name | Description |
|------|-------------|
| Fully Managed Container Orchestration | Run and manage Docker containers at scale without managing the underlying infrastructure or control plane. |
| AWS Fargate Integration | Run containers serverlessly without provisioning or managing EC2 instances using AWS Fargate launch type. |
| Service Auto Scaling | Automatically scale container workloads based on CloudWatch metrics, target tracking, or step scaling policies. |
| Service Connect | Built-in service discovery and service mesh for connecting containerized services within and across clusters. |
| ECS Anywhere | Extend ECS to on-premises and edge infrastructure to run containers on your own servers and virtual machines. |
| Capacity Providers | Manage compute capacity with capacity provider strategies for optimal resource allocation across EC2 and Fargate. |
| Task Definitions | Define containerized applications as task definitions with CPU, memory, networking, and IAM role configurations. |
| Container Insights | Monitor container performance metrics and logs with CloudWatch Container Insights for operational visibility. |

## Use Cases

| Name | Description |
|------|-------------|
| Microservices Architecture | Deploy and manage microservices with independent scaling, deployment, and lifecycle management per service. |
| Batch Processing | Run batch computing workloads using ECS tasks with automatic scaling and job scheduling. |
| CI/CD Pipeline Deployment | Integrate with AWS CodePipeline and CodeDeploy for automated blue/green and rolling deployments of containerized applications. |
| Hybrid Cloud Workloads | Run containerized workloads across AWS cloud and on-premises environments using ECS Anywhere. |
| Machine Learning Inference | Deploy ML models as containerized inference endpoints with auto-scaling based on demand. |

## Integrations

| Name | Description |
|------|-------------|
| AWS Fargate | Serverless compute engine for running containers without managing underlying EC2 instances. |
| Amazon ECR | Private container registry for storing, managing, and deploying Docker container images. |
| AWS CloudFormation | Infrastructure as code for provisioning and managing ECS clusters, services, and task definitions. |
| Elastic Load Balancing | Distribute traffic across containers with Application Load Balancer and Network Load Balancer integration. |
| Amazon CloudWatch | Monitor container metrics, logs, and alarms with CloudWatch and Container Insights. |
| AWS IAM | Fine-grained access control for ECS tasks and services using IAM roles and policies. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [Amazon ECS API](openapi/amazon-ecs-openapi.yml)

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [Amazon ECS API](capabilities/shared/ecs.yaml) -- 28 operations for container orchestration

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Container Orchestration](capabilities/container-orchestration.yaml) | ECS | 18 | DevOps Engineer |

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
**FN:** Amazon Web Services

**Email:** support@aws.amazon.com
