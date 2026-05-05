---
title: "Build production-ready applications without infrastructure complexity using Amazon ECS Express Mode"
url: "https://aws.amazon.com/blogs/aws/build-production-ready-applications-without-infrastructure-complexity-using-amazon-ecs-express-mode/"
date: "Fri, 21 Nov 2025 21:34:45 +0000"
author: "Donnie Prakoso"
feed_url: "https://aws.amazon.com/blogs/aws/category/compute/amazon-elastic-container-service/feed/"
---
<p>Deploying containerized applications to production requires navigating hundreds of configuration parameters across load balancers, auto scaling policies, networking, and security groups. This overhead delays time to market and diverts focus from core application development.</p> 
<p>Today, I’m excited to announce Amazon ECS Express Mode, a new capability from <a href="https://aws.amazon.com/ecs/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">Amazon Elastic Container Service (Amazon ECS)</a> that helps you launch highly available, scalable containerized applications with a single command. ECS Express Mode automates infrastructure setup including domains, networking, load balancing, and auto scaling through simplified APIs. This means you can focus on building applications while deploying with confidence using <a href="https://aws.amazon.com/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">Amazon Web Services (AWS)</a> best practices. Furthermore, when your applications evolve and require advanced features, you can seamlessly configure and access the full capabilities of the resources, including Amazon ECS.</p> 
<p>You can get started with Amazon ECS Express Mode by navigating to the <a href="https://console.aws.amazon.com/ecs/">Amazon ECS console</a>.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100534" height="910" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-01.png" width="1920" /></p> 
<p>Amazon ECS Express Mode provides a simplified interface to the Amazon ECS service resource with new integrations for creating commonly used resources across AWS. ECS Express Mode automatically provisions and configures ECS clusters, task definitions, Application Load Balancers, auto scaling policies, and Amazon Route 53 domains from a single entry point.</p> 
<p><span style="text-decoration: underline;"><strong>Getting started with ECS Express Mode<br /> </strong></span>Let me walk you through how to use Amazon ECS Express Mode. I’ll focus on the console experience, which provides the quickest way to deploy your containerized application.</p> 
<p>For this example, I’m using a simple container image application running on Python with the Flask framework. Here’s the <code>Dockerfile</code> of my demo, which I have pushed to an <a href="https://aws.amazon.com/ecr/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">Amazon Elastic Container Registry (Amazon ECR)</a> repository:</p> 
<pre><code class="language-dockerfile">
# Build stage
FROM python:3.6-slim as builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --user -r requirements.txt gunicorn

# Runtime stage
FROM python:3.6-slim
WORKDIR /app
COPY --from=builder /root/.local /root/.local
COPY app.py .
ENV PATH=/root/.local/bin:$PATH
EXPOSE 80
CMD ["gunicorn", "--bind", "0.0.0.0:80", "app:app"]
</code></pre> 
<p>On the Express Mode page, I choose <strong>Create</strong>. The interface is streamlined — I specify my container image URI from Amazon ECR, then select my task execution role and infrastructure role. If you don’t already have these roles, choose <b>Create new role</b> in the drop down to have one created for you from the <a href="https://aws.amazon.com/iam/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">AWS Identity and Access Management (IAM)</a> managed policy.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100535" height="871" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-02.png" width="1920" /></p> 
<p>If I want to customize the deployment, I can expand the <strong>Additional configurations</strong> section to define my cluster, container port, health check path, or environment variables.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100536" height="945" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-03.png" width="1060" /></p> 
<p>In this section, I can also adjust CPU, memory, or scaling policies.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100537" height="608" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-04.png" width="1060" /></p> 
<p>Setting up logs in <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html">Amazon CloudWatch Logs</a> is something I always configure so I can troubleshoot my applications if needed. When I’m happy with the configurations, I choose <strong>Create</strong>.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100538" height="591" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-04-1.png" width="1060" /></p> 
<p>After I choose <strong>Create</strong>, Express Mode automatically provisions a complete application stack, including an Amazon ECS service with <a href="https://aws.amazon.com/fargate/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">AWS Fargate</a> tasks, Application Load Balancer with health checks, auto scaling policies based on CPU utilization, security groups and networking configuration, and a custom domain with an AWS provided URL. I can also follow the progress in <strong>Timeline view</strong> on the <strong>Resources</strong> tab.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100540" height="1643" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-05.png" width="1264" /></p> 
<p>If I need to do a programmatic deployment, the same result can be achieved with a single <a href="https://aws.amazon.com/cli/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">AWS Command Line Interface (AWS CLI)</a> command:</p> 
<pre><code class="lang-bash">aws ecs create-express-gateway-service \
--image [ACCOUNT_ID].ecr.us-west-2.amazonaws.com/myapp:latest \
--execution-role-arn arn:aws:iam::[ACCOUNT_ID]:role/[IAM_ROLE] \
--infrastructure-role-arn arn:aws:iam::[ACCOUNT_ID]:role/[IAM_ROLE]</code></pre> 
<p>After it’s complete, I can see my application URL in the console and access my running application immediately.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100539" height="493" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-07.png" width="1123" /></p> 
<p>After the application is created, I can see the details by visiting the specified cluster, or the default cluster if I didn’t specify one, in the ECS service to monitor performance, view logs, and manage the deployment.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100544" height="1584" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-09-1.png" width="3024" /></p> 
<p>When I need to update my application with a new container version, I can return to the console, select my Express service, and choose <strong>Update</strong>. I can use the interface to specify a new image URI or adjust resource allocations.</p> 
<p><img alt="" class="aligncenter size-full wp-image-100545" height="1392" src="https://d2908q01vomqb2.cloudfront.net/da4b9237bacccdf19c0760cab7aec4a8359010b0/2025/11/08/news-2025-11-ecs-express-08.png" width="2932" /></p> 
<p>Alternatively, I can use the AWS CLI for updates:</p> 
<pre><code class="language-bash">aws ecs update-express-gateway-service \
  --service-arn arn:aws:ecs:us-west-2:[ACCOUNT_ID]:service/[CLUSTER_NAME]/[APP_NAME] \
  --primary-container '{
    "image": "[IMAGE_URI]"
  }'
</code></pre> 
<p>I find the entire experience reduces setup complexity while still giving me access to all the underlying resources when I need more advanced configurations.</p> 
<p><span style="text-decoration: underline;"><strong>Additional things to know<br /> </strong></span>Here are additional things about ECS Express Mode:</p> 
<ul> 
 <li><strong>Availability</strong> – ECS Express Mode is available in all <a href="https://docs.aws.amazon.com/glossary/latest/reference/glos-chap.html#region">AWS Regions</a> at launch.</li> 
 <li><strong><a href="https://aws.amazon.com/what-is/iac/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">Infrastructure as Code</a> support</strong> – You can use IaC tools such as <a href="https://aws.amazon.com/cloudformation/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">AWS CloudFormation</a>, <a href="https://aws.amazon.com/cdk/?trk=c4ea046f-18ad-4d23-a1ac-cdd1267f942c&amp;sc_channel=el">AWS Cloud Development Kit (CDK)</a>, or Terraform to deploy your applications using Amazon ECS Express Mode.</li> 
 <li><strong>Pricing</strong> – There is no additional charge to use Amazon ECS Express Mode. You pay for AWS resources created to launch and run your application.</li> 
 <li><strong>Application Load Balancer sharing</strong> – The ALB created is automatically shared across up to 25 ECS services using host-header based listener rules. This helps distribute the cost of the ALB significantly.</li> 
</ul> 
<p>Get started with Amazon ECS Express Mode through the Amazon ECS console. Learn more on the <a href="https://docs.aws.amazon.com/AmazonECS/latest/developerguide/express-service-overview.html">Amazon ECS documentation</a> page.</p> 
<p>Happy building!<br /> — <a href="https://www.linkedin.com/in/donnieprakoso">Donnie</a></p>
