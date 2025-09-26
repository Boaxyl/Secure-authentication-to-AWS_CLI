## 📘 AWS CLI, APIs, and Authentication – Project Documentation

### 🔧 1. Understanding AWS CLI

The **AWS Command Line Interface (CLI)** is a tool that enables users to interact with AWS services from the terminal. It supports nearly all AWS services and allows automation through scripts.

- **Installation**:  
  AWS CLI can be installed via package managers like `apt`, `yum`, or directly from AWS's installer.
  
- **Basic Usage**:  
  ```bash
  aws ec2 describe-instances
  aws s3 ls
  ```

- **Configuration**:  
  ```bash
  aws configure
  ```
  This sets up:
  - Access Key ID
  - Secret Access Key
  - Default region
  - Output format

---

### 🌐 2. Understanding AWS APIs

AWS provides **RESTful APIs** for all its services. These APIs allow programmatic access to resources using HTTPS requests.

- **API Actions**: Each AWS service has a set of actions like `CreateBucket`, `RunInstances`, etc.
- **Authentication**: Requests must be signed using AWS Signature Version 4.
- **Tools**: While you can use raw HTTP requests, the AWS CLI and SDKs abstract this complexity.

---

### 🔐 3. Authenticating to AWS API from Terminal

Authentication is handled via **IAM credentials**, which are configured using the CLI:

- **Permanent credentials**: Access key and secret key from IAM user.
- **Temporary credentials**: Via STS or IAM roles (especially in EC2).
- **Profiles**: You can manage multiple sets of credentials:
  ```bash
  aws configure --profile dev
  aws s3 ls --profile dev
  ```

---

### ✅ 4. Verification of Deployment Status

After deploying resources, use CLI commands to verify:

- **EC2 Instance**:
  ```bash
  aws ec2 describe-instances --query "Reservations[*].Instances[*].State.Name"
  ```

- **S3 Bucket**:
  ```bash
  aws s3 ls
  ```

---

Would you like me to help you turn this into a full Markdown report or include sample bash functions for automation? I can even help you write a submission paragraph that ties it all together.
  
.  


