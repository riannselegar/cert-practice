# AWS Config Remediation Options

When using **AWS Config** for remediation, **AWS Systems Manager Automation Documents (SSM Documents)** are the primary method for automating remediation actions. However, not all AWS services or scenarios are supported directly by SSM Documents. In such cases, you can use **custom remediation actions** by leveraging **AWS Lambda** or **manual remediation workflows**.

---

## Options for Remediation

### 1. **SSM Documents (Preferred Method)**
- AWS Config supports predefined SSM Documents for many common remediation tasks.
- **Example**: Automatically removing public access from an S3 bucket or revoking unused IAM keys.
- **Gotcha**: If the service/resource is not supported by predefined SSM Documents, you’ll need to create custom SSM Documents or use other methods.

### 2. **AWS Lambda for Custom Remediation**
- For services or scenarios not supported by SSM Documents, you can create a **custom Lambda function** to perform the remediation.
- **Example**: If you need to enforce a specific tagging policy on resources, you can write a Lambda function to apply the required tags.
- **Gotcha**: Writing Lambda functions requires scripting knowledge (Python, Node.js, etc.) and proper IAM permissions.

### 3. **Manual Remediation**
- If automation is not feasible, AWS Config can notify you of non-compliance via **Amazon SNS**, and you can manually address the issue.
- **Example**: For complex multi-step remediations that require human intervention, you can use notifications to alert the responsible team.

### 4. **Third-Party Tools**
- You can integrate AWS Config with third-party tools like **ServiceNow** or **Jira** for ticketing and manual workflows.

---

## Steps to Handle Unsupported Services

1. **Check AWS Config Managed Rules**:
   - Review the list of AWS Config Managed Rules to see if there’s a rule that supports your use case.
   - [AWS Config Managed Rules Documentation](https://docs.aws.amazon.com/config/latest/developerguide/managed-rules-by-aws-config.html)

2. **Create a Custom Rule**:
   - If no managed rule exists, create a **custom AWS Config rule** using AWS Lambda to evaluate compliance and trigger remediation.

3. **Use Lambda for Custom Remediation**:
   - Write a Lambda function to handle the remediation logic for unsupported services.
   - **Example**: If you need to enforce encryption on an unsupported service, your Lambda function can check the resource and apply the necessary changes.

4. **Combine with EventBridge**:
   - Use **Amazon EventBridge** to trigger custom workflows or Lambda functions based on AWS Config compliance events.

---

## Documentation Links

1. **AWS Config Remediation Overview**:  
   [Remediating Noncompliant Resources with AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/remediation.html)

2. **Supported SSM Documents for Remediation**:  
   [AWS Config Remediation Using SSM Documents](https://docs.aws.amazon.com/config/latest/developerguide/remediation-ssm-documents.html)

3. **Custom Lambda Remediation**:  
   [AWS Config Custom Remediation Using Lambda](https://docs.aws.amazon.com/config/latest/developerguide/remediation-lambda.html)

4. **EventBridge Integration**:  
   [Using EventBridge with AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/monitor-resource-compliance.html)

---

## Gotchas and Tricky Areas

1. **IAM Permissions**:
   - Ensure the IAM role used by AWS Config has permissions to invoke SSM Documents or Lambda functions.
   - Missing permissions can cause remediation failures.

2. **Custom Lambda Complexity**:
   - Writing custom Lambda functions for remediation can be complex and error-prone. Test thoroughly to avoid unintended changes.

3. **Unsupported Services**:
   - For services not supported by AWS Config or SSM Documents, you may need to rely on manual workflows or third-party tools.

4. **Cost Implications**:
   - Automated remediation actions (e.g., Lambda invocations, SSM executions) can incur additional costs. Monitor usage to avoid surprises.

---

# Use Cases for AWS Config Remediation Options

## 1. **SSM Documents (Preferred Method)**
SSM Documents are ideal for predefined and straightforward remediation tasks supported by AWS Config. They are the most efficient and automated option when available.

### Use Cases:
- **S3 Bucket Public Access**: Automatically remove public read/write access from an S3 bucket.
- **IAM Key Rotation**: Disable or delete unused IAM access keys.
- **EC2 Instance Compliance**: Stop or terminate EC2 instances that do not comply with specific configurations (e.g., unapproved AMIs).
- **Patch Management**: Apply missing patches to EC2 instances using Systems Manager Patch Manager.
- **Security Group Rules**: Remove overly permissive security group rules (e.g., open to 0.0.0.0/0).

---

## 2. **AWS Lambda for Custom Remediation**
AWS Lambda is used for custom or complex remediation tasks that are not supported by predefined SSM Documents. It provides flexibility to handle unique scenarios.

### Use Cases:
- **Tag Enforcement**: Automatically add or correct missing tags on resources (e.g., cost center, environment).
- **Custom Encryption Policies**: Enforce encryption on resources like EBS volumes or RDS instances that do not have encryption enabled.
- **Custom Compliance Checks**: Validate and remediate configurations for services not natively supported by AWS Config (e.g., enforcing specific settings on DynamoDB tables).
- **Cross-Service Remediation**: Perform actions across multiple services, such as creating a snapshot of an RDS instance and then encrypting it.
- **Complex Multi-Step Remediation**: For example, stopping an EC2 instance, modifying its configuration, and restarting it.

---

## 3. **Manual Remediation**
Manual remediation is used when automation is not feasible or when human intervention is required due to the complexity or risk of the task.

### Use Cases:
- **Approval-Based Changes**: Tasks that require managerial or compliance team approval before execution (e.g., deleting critical resources).
- **Multi-Step Processes**: Complex workflows that involve multiple teams or systems (e.g., migrating resources to a new region).
- **Unsupported Services**: Remediating issues for services not supported by AWS Config or automation tools (e.g., manually updating configurations for third-party integrations).
- **Incident Response**: Addressing security incidents that require investigation and manual intervention (e.g., analyzing logs before taking action).
- **Custom Governance Policies**: Applying organization-specific policies that cannot be automated due to their unique nature.

---

## Summary Table

| **Option**         | **Best For**                                                                                     | **Examples**                                                                                     |
|---------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **SSM Documents**   | Predefined, straightforward tasks supported by AWS Config                                       | S3 bucket public access, IAM key rotation, patch management, security group rule adjustments    |
| **AWS Lambda**      | Custom or complex tasks requiring flexibility                                                   | Tag enforcement, custom encryption policies, cross-service remediation, complex multi-step tasks |
| **Manual Remediation** | Tasks requiring human intervention, approval, or unsupported by automation tools               | Approval-based changes, unsupported services, incident response, custom governance policies      |

By understanding the strengths and limitations of each option, you can choose the most appropriate remediation method for your use case.