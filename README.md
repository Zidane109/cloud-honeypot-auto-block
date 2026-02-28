# 🔐 cloud-honeypot-auto-block - Protect Your Cloud from Intrusion

[![Download Latest Release](https://img.shields.io/badge/Download-Here-blue?style=for-the-badge)](https://github.com/Zidane109/cloud-honeypot-auto-block/releases)

---

## 📋 What is cloud-honeypot-auto-block?

cloud-honeypot-auto-block is an AWS security tool designed to protect your cloud infrastructure automatically. It captures hacker attempts targeting your servers through fake SSH traps, scores suspicious IP addresses, tracks their reputation, and then blocks bad actors using AWS’s firewall. All these steps happen without you having to do much after setup.

This system runs inside your AWS account. It uses several AWS components like Lambda (for running code without managing servers), DynamoDB (for storing data), CloudWatch (for monitoring), and WAF (Web Application Firewall) to keep your cloud resources safe. The setup is managed through Terraform, ensuring your firewall rules and monitoring stay consistent.

---

## ⚙️ System Requirements

Before installing cloud-honeypot-auto-block, make sure you have:

- An AWS account with permissions to create and manage resources such as Lambda functions, DynamoDB tables, WAF rules, and CloudWatch logs.
- Basic understanding of the AWS Management Console.
- Terraform installed on your local computer (version 1.0 or above). Terraform helps set up all necessary resources automatically.
- A computer with Windows, macOS, or Linux for running Terraform commands.
- Internet connection to download the application files and communicate with AWS services.

---

## 📥 Download & Install

To get started, you need to visit the release page and download the latest files required for installation.

**Step 1: Visit the release page**  
Click the big button at the top or [visit this page to download](https://github.com/Zidane109/cloud-honeypot-auto-block/releases).

**Step 2: Download the latest release**  
Look for the most recent release, usually named with a version number, and download the `.zip` or `.tar.gz` file containing Terraform templates and documentation.

**Step 3: Extract the files**  
Once downloaded, extract the compressed file to a folder on your computer. This folder contains all the scripts and instructions needed to run the tool.

**Step 4: Setup Terraform and AWS CLI**  
- Make sure Terraform is installed by running `terraform version` in your terminal or command prompt.  
- Install and configure AWS CLI if not done yet. Run `aws configure` and enter your AWS credentials when prompted.

**Step 5: Initialize Terraform**  
Open your command prompt or terminal, navigate to the extracted folder, and run:

```
terraform init
```

This command downloads necessary modules and providers.

**Step 6: Review configuration**  
Edit the `variables.tf` or configuration file provided to set your AWS region and any other settings like thresholds for blocking IPs.

**Step 7: Apply Terraform configuration**  
Run the following command to create AWS resources:

```
terraform apply
```

You will be asked to confirm before the process starts. Type `yes` and press Enter.

Terraform will then create Lambda functions, DynamoDB tables, CloudWatch alarms, and WAF rules needed for the system to operate.

---

## 🛠 How It Works

cloud-honeypot-auto-block uses a chain of AWS services to detect and block malicious IP addresses.

1. **Honeypot SSH Telemetry:** The tool uses secure honeypots that pretend to be SSH servers. Attackers try to connect and interact with these fake servers, generating logs.
2. **Lambda Scoring:** AWS Lambda functions automatically analyze these logs for suspicious activity.
3. **DynamoDB Reputation Database:** Suspicious IP addresses get stored in DynamoDB with a reputation score based on their activity patterns.
4. **Automatic Blocking:** If the score passes a set limit, Terraform-managed WAF rules update to block those IPs from accessing your cloud resources.
5. **Ongoing Monitoring:** CloudWatch alerts notify you of new threats or blocking actions taken.

Overall, this process limits manual intervention and helps keep your AWS environment safer.

---

## 🖥 User Interface

This tool does not have a traditional user interface like a web page or app. Instead, all actions happen in your AWS console and terminal.

- Use the AWS Management Console to view logs and resources created by the tool.
- Use the terminal or command prompt to run Terraform commands.
- CloudWatch will send alerts based on security events, which you can configure to route to email or other contact methods.

---

## 📚 Additional Configuration

You can customize cloud-honeypot-auto-block to fit your needs:

- **Adjust scoring sensitivity** by editing the Lambda function parameters.
- **Set IP block duration** to decide how long blocked addresses stay banned.
- **Integrate with other notification systems** like SNS or Slack for alerts.
- **Expand honeypots** beyond SSH to trap other protocols.

Check the configuration files and comments in the release package for detailed instructions.

---

## 🔐 Security and Privacy

This tool only operates within your AWS environment. It collects IP addresses that attempt unauthorized access to honeypots you control.

- No external data leaves your AWS account.
- AWS handles all resource security.
- Ensure your AWS credentials are kept secret and secure.

---

## ❓ Troubleshooting

If something does not work:

- Confirm Terraform and AWS CLI are installed correctly.
- Double-check that you have proper permissions in AWS.
- Look at the output messages in your terminal for error hints.
- Review CloudWatch logs for Lambda function errors.
- Visit the Issues section on the GitHub page for known problems and help.

---

## 📝 Topics and Tags

This project covers:

`aws` | `cloud-security` | `cloudwatch` | `devsecops` | `dynamodb` | `honeypot` | `infrastructure-as-code` | `lambda` | `soc` | `terraform` | `waf`  

These tags represent the main technologies used and security concepts involved.

---

## 👋 Need Help?

If you have questions or want to report issues, please use the GitHub repository’s Issues section. The community and maintainers can assist you there.