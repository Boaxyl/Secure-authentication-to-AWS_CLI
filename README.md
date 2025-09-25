# Secure-authentication-to-AWS_CLI

# My AWS IAM and CLI Setup Report

## Identity and Access Management (IAM) Tasks

1. **I created an IAM Role**  
   - I went to the IAM console in AWS Management Console.  
   - I chose **Roles** > **Create role**.  
   - I selected a trusted entity (AWS service).  
   - I configured permissions, tags, and named the role.  
   - I completed creating the role.

2. **I created an IAM Policy**  
   - In the IAM console, I went to **Policies** > **Create policy**.  
   - I defined JSON permissions using the visual editor.  
   - I reviewed and created the policy.

3. **I created an IAM User**  
   - In the IAM console, I went to **Users** > **Add user**.  
   - I provided a username and selected the access type (programmatic, console, or both).  
   - I assigned permissions.  
   - I finished creating the user.

4. **I assigned the User to the IAM Role**  
   - I allowed the user to assume the role.  
   - I edited the trust policy of the role to include the user.  
   - I attached it using the AWS console.

5. **I attached the IAM Policy to the User**  
   - I went to the IAM user in the console.  
   - I selected the **Permissions** tab > **Add permissions**.  
   - I attached the created IAM policy.

6. **I created Programmatic Access Credentials**  
   - I went to the IAM user details.  
   - Under **Security credentials**, I created an **Access key**.  
   - I saved the **Access Key ID** and **Secret Access Key** securely.  

---

## AWS CLI Installation on Windows

1. **I downloaded AWS CLI v2**  
   - I visited the [official AWS website](https://aws.amazon.com/cli/).  
   - I downloaded the Windows installer for AWS CLI version 2.

2. **I ran the Installer**  
   - I launched the downloaded `.msi` installer.  
   - I followed the on-screen instructions to complete the installation.
  

3. **I verified the Installation**  
   - I opened **Command Prompt**.  
   - I ran:  
     ```bash
     aws --version
     ``` 
   - I saw output like:  
     ```
     aws-cli/2.x.x Python/3.x Windows/x86_64
     ```
