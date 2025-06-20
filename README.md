# Automated Threat-Flagging & File Quarantine Pipeline Using AWS Serverless Stack
   ( The whole infrastructure was deployed using Terraform, following infrastructure-as-code best practices.)


# Real-World Example 
Imagine a medical research center receiving hundreds of diagnostic image files (like X-rays, MRIs, reports) from external sources. Some might be:

- Mistaken uploads

- Corrupt or suspicious files

- Malicious attachments

This system automatically scans, logs, and quarantines such files for review, preventing system disruption or data risk.

# Main Problem

Organizations often ingest files from multiple sources.
Without automation, it’s hard to detect or isolate suspicious files quickly.

# Solution (What I Built)

I created a fully serverless, scalable pipeline using:

- Amazon S3 for secure file intake

- AWS Lambda for detection & response

- Amazon DynamoDB for logging file metadata

- Amazon SNS for real-time alerts

- API Gateway for external/manual triggers

# How It Works

- Files uploaded to an S3 input bucket automatically trigger Lambda.

- Lambda evaluates the file name (mock logic for now).

- If flagged as "suspicious":

   - The file is moved to a quarantine bucket

   - A log entry is created in DynamoDB

   - A notification is sent via SNS

- The same logic can also be triggered manually via API Gateway.

# 💡 Limitations (Current & Future Enhancements)

 This version detects suspicious files by filename only (e.g. "suspicious_report.pdf").

 Future versions will include:

 - Real malware detection via integrated antivirus or machine learning

# What I Learned

- Deploying multi-service apps using Terraform modules

- Writing a Lambda function that integrates with 3 services (S3, DynamoDB, SNS)

- Solving IAM permission issues (e.g., S3 GetObject, environment vars)

- Structuring code for multiple triggers (S3 + API Gateway)

- Debugging CloudWatch logs and fixing Python runtime errors

# Key Technologies

- AWS S3, Lambda, DynamoDB, SNS, API Gateway

- Terraform (IaC)

- Python (Lambda logic)

# 📷 Screenshots and details

  Screenshots of the working system including DynamoDB logs, CloudWatch outputs, SNS email alerts, S3 bucket contents, and API Gateway are available in the images folder. All code is shared in this repository as structured files.
