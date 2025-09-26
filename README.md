# AWS IAM Project Report

## Objective
The objective of this project was to install the AWS CLI, create an IAM role, IAM policy, and IAM user, then configure permissions by assigning the user to the role and attaching a policy.

---

## Step 0: Installed AWS CLI
Before working with IAM resources, I installed the AWS CLI on my Ubuntu system.

1. I downloaded the AWS CLI:
   ```bash
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
````

2. I extracted the ZIP content:

   ```bash
   unzip awscliv2.zip
   ```

3. I installed the AWS CLI:

   ```bash
   sudo ./aws/install
   ```

4. I confirmed the installation:

   ```bash
   aws --version
   ```

---

## Step 1: Created an IAM Role

I created an IAM role in AWS with a trust policy that allowed an IAM user to assume it.

### Example AWS CLI command:

```bash
aws iam create-role \
  --role-name MyDemoRole \
  --assume-role-policy-document '{
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Principal": { "AWS": "arn:aws:iam::ACCOUNT_ID:user/MyDemoUser" },
        "Action": "sts:AssumeRole"
      }
    ]
  }'
```

---

## Step 2: Created an IAM Policy

I wrote an IAM policy in JSON format that granted **S3 read-only access**.
I then created it as a customer-managed policy.

### Example AWS CLI command:

```bash
aws iam create-policy \
  --policy-name MyS3ReadOnlyPolicy \
  --policy-document '{
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Action": ["s3:ListBucket", "s3:GetObject"],
        "Resource": ["arn:aws:s3:::*"]
      }
    ]
  }'
```

---

## Step 3: Created an IAM User

I created an IAM user to represent an individual identity that required access.

### Example AWS CLI command:

```bash
aws iam create-user --user-name MyDemoUser
```

Optionally, I generated access keys for CLI/API use:

```bash
aws iam create-access-key --user-name MyDemoUser
```

---

## Step 4: Assigned the IAM User to the Role

I updated the trust policy of the IAM role so that the IAM user could assume it.
This allowed the user to temporarily inherit the role’s permissions.

### Example AWS CLI command to allow the user to assume the role:

```bash
aws iam update-assume-role-policy \
  --role-name MyDemoRole \
  --policy-document '{
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Principal": { "AWS": "arn:aws:iam::ACCOUNT_ID:user/MyDemoUser" },
        "Action": "sts:AssumeRole"
      }
    ]
  }'
```

The user could then assume the role using:

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::ACCOUNT_ID:role/MyDemoRole \
  --role-session-name DemoSession
```

---

## Step 5: Attached the IAM Policy to the User

I also attached the IAM policy directly to the IAM user to give them permissions.

### Example AWS CLI command:

```bash
aws iam attach-user-policy \
  --user-name MyDemoUser \
  --policy-arn arn:aws:iam::ACCOUNT_ID:policy/MyS3ReadOnlyPolicy
```

---

## Outcome

At the end of the project, I successfully:

* Installed and verified the AWS CLI
* Created an IAM role with a trust policy
* Created a reusable IAM policy defining permissions
* Created an IAM user with login credentials
* Configured the user to assume the role
* Attached the IAM policy to the user for direct permissions

This setup gave me a secure and flexible way to manage identity and access in AWS.

```

---

Do you want me to also add a **Mermaid diagram** in the Markdown showing the relationship between the user, role, and policy? That way your report has both text, commands, and a visual.
```
