# AWS Certified DevOps Engineer - Professional (DOP-C02) Exam Guide

The **AWS Certified DevOps Engineer - Professional (DOP-C02)** exam is designed for individuals who perform a DevOps engineer role. It validates technical expertise in provisioning, operating, and managing distributed systems and services on AWS. Below is a detailed breakdown of the exam, its domains, and the services you need to focus on.

---

## Exam Overview

- **Number of Questions**: 65 scored questions + 10 unscored questions
- **Question Types**: Multiple choice and multiple response
- **Passing Score**: 750 (scaled score of 100–1,000)
- **Time**: 180 minutes
- **Domains**:
  - Domain 1: SDLC Automation (22%)
  - Domain 2: Configuration Management and IaC (17%)
  - Domain 3: Resilient Cloud Solutions (15%)
  - Domain 4: Monitoring and Logging (15%)
  - Domain 5: Incident and Event Response (14%)
  - Domain 6: Security and Compliance (17%)

---

## Domain 1: SDLC Automation (22%)

### Key Topics:
- Implementing CI/CD pipelines
- Integrating automated testing
- Managing artifacts
- Deployment strategies for instance, container, and serverless environments

### AWS Services:
1. **AWS CodePipeline**: Orchestrates CI/CD workflows.
2. **AWS CodeBuild**: Compiles source code, runs tests, and produces artifacts.
3. **AWS CodeDeploy**: Automates application deployments to EC2, Lambda, or on-premises.
4. **AWS CodeArtifact**: Secure artifact repository for dependencies.
5. **Amazon ECR**: Container image repository.
6. **AWS Lambda**: Serverless compute for running code.
7. **Amazon S3**: Storage for build artifacts.
8. **AWS Secrets Manager**: Manages secrets like API keys and passwords.

### Gotchas:
- Understand deployment strategies like **blue/green** and **canary**.
- Know how to secure pipelines using **IAM roles** and **Secrets Manager**.
- Be familiar with **artifact lifecycle management** and **versioning**.

---

## Domain 2: Configuration Management and IaC (17%)

### Key Topics:
- Defining cloud infrastructure using IaC
- Automating account provisioning in multi-account environments
- Building automated solutions for large-scale environments

### AWS Services:
1. **AWS CloudFormation**: Declarative IaC for AWS resources.
2. **AWS CDK**: Programmatic IaC using familiar programming languages.
3. **AWS Systems Manager**: Centralized management of resources.
4. **AWS Config**: Tracks configuration changes and compliance.
5. **AWS OpsWorks**: Configuration management using Chef or Puppet.
6. **AWS Service Catalog**: Manages approved templates and products.
7. **AWS Control Tower**: Automates multi-account setup and governance.

### Gotchas:
- Understand **CloudFormation StackSets** for multi-account and multi-region deployments.
- Be familiar with **AWS Config rules** for compliance.
- Know how to use **AWS Systems Manager State Manager** for configuration enforcement.

---

## Domain 3: Resilient Cloud Solutions (15%)

### Key Topics:
- High availability and fault tolerance
- Scalability to meet business requirements
- Automated recovery processes for RTO and RPO

### AWS Services:
1. **Amazon Route 53**: DNS and traffic routing.
2. **Elastic Load Balancing (ELB)**: Distributes traffic across targets.
3. **Amazon RDS**: Managed relational database service.
4. **Amazon DynamoDB**: NoSQL database with global tables.
5. **Amazon S3**: Cross-region replication for data durability.
6. **AWS Backup**: Centralized backup management.
7. **AWS Auto Scaling**: Automatically adjusts capacity to maintain performance.

### Gotchas:
- Understand **multi-AZ** and **multi-region** architectures.
- Be familiar with **disaster recovery strategies** like **pilot light** and **warm standby**.
- Know how to configure **Route 53 health checks** for failover.

---

## Domain 4: Monitoring and Logging (15%)

### Key Topics:
- Collecting, aggregating, and storing logs and metrics
- Auditing and analyzing logs to detect issues
- Automating monitoring and event management

### AWS Services:
1. **Amazon CloudWatch**: Metrics, logs, and alarms.
2. **AWS X-Ray**: Distributed tracing for applications.
3. **AWS Config**: Tracks configuration changes.
4. **AWS CloudTrail**: Logs API activity.
5. **Amazon OpenSearch Service**: Log analytics and visualization.
6. **Amazon Kinesis**: Real-time data streaming.
7. **Amazon QuickSight**: Business intelligence and visualization.

### Gotchas:
- Understand **CloudWatch Logs Insights** for querying logs.
- Be familiar with **anomaly detection alarms** in CloudWatch.
- Know how to use **Kinesis Data Firehose** for log ingestion.

---

## Domain 5: Incident and Event Response (14%)

### Key Topics:
- Managing event sources
- Implementing configuration changes in response to events
- Troubleshooting system and application failures

### AWS Services:
1. **Amazon EventBridge**: Event bus for routing events.
2. **AWS Health Dashboard**: Provides service health updates.
3. **AWS Systems Manager OpsCenter**: Centralized incident management.
4. **AWS CloudTrail**: Tracks API activity.
5. **AWS Lambda**: Automates responses to events.

### Gotchas:
- Understand **event-driven architectures** using EventBridge.
- Be familiar with **root cause analysis** using CloudTrail and CloudWatch.
- Know how to use **AWS Systems Manager Automation Documents (SSM Documents)** for remediation.

---

## Domain 6: Security and Compliance (17%)

### Key Topics:
- Identity and access management at scale
- Automating security controls and data protection
- Security monitoring and auditing

### AWS Services:
1. **AWS IAM**: Manages access to AWS resources.
2. **AWS Organizations**: Centralized account management.
3. **AWS Security Hub**: Centralized security posture management.
4. **Amazon GuardDuty**: Threat detection.
5. **AWS Config**: Compliance tracking.
6. **AWS Secrets Manager**: Securely stores secrets.
7. **Amazon Macie**: Sensitive data discovery.
8. **AWS Key Management Service (KMS)**: Encryption key management.

### Gotchas:
- Understand **IAM permission boundaries** and **SCPs** in AWS Organizations.
- Be familiar with **AWS Config rules** for compliance automation.
- Know how to use **GuardDuty findings** to trigger automated responses.

---

## Additional Resources

1. **AWS Documentation**:
   - [AWS DevOps Engineer Professional Exam Guide](https://aws.amazon.com/certification/certified-devops-engineer-professional/)
   - [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
   - [AWS Security Best Practices](https://docs.aws.amazon.com/security/)

2. **Whitepapers**:
   - [CI/CD on AWS](https://d1.awsstatic.com/whitepapers/DevOps/CI_CD_on_AWS.pdf)
   - [AWS Disaster Recovery](https://d1.awsstatic.com/whitepapers/aws-disaster-recovery.pdf)

3. **Hands-On Labs**:
   - [AWS Skill Builder](https://skillbuilder.aws/)
   - [Qwiklabs](https://www.qwiklabs.com/)

4. **Practice Exams**:
   - [AWS Practice Exams](https://aws.amazon.com/certification/practice-exams/)

5. **Books**:
   - *AWS Certified DevOps Engineer Professional Study Guide* by Marko Sluga

---

By focusing on the domains, understanding the services, and practicing hands-on, you’ll be well-prepared for the AWS Certified DevOps Engineer - Professional exam. Good luck! 🚀