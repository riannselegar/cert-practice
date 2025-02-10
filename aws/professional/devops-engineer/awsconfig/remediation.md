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

By combining **AWS Config** with **SSM Documents**, **Lambda**, and **EventBridge**, you can create a robust remediation strategy for both supported and unsupported services. Let me know if you need further clarification!