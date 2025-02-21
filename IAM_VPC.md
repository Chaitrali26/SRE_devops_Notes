

## IAM [Identity and access management]:

1. IAM is a web service that controls access to AWS resources. It helps with security and operational efficiency by managing user identities, permissions and security policies.
2. In simple words, With IAM, you can manage permissions that control which AWS resources users can access.
3. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.
4. **IAM Users:** Individual accounts created for people who need access to AWS.
5. **IAM Roles:** Used to grant temporary access to AWS resources without using long-term credentials.
6. **IAM groups:** Collections of IAM users that share the same permissions. Groups simplify managing permissions for multiple users.
7. **IAM Policies:** Documents written in JSON that define permissions for IAM users, groups, or roles.
    - Types of Policies:
        1. Managed Policies: AWS-managed or customer-managed reusable policies.
        2. Inline Policies: Policies embedded directly in a user, group, or role.
8. **Authentication Methods:**
    1. Access Keys: For programmatic access (API, CLI, SDK).
    2. Passwords: For access to the AWS Management Console.
    3. Multi-Factor Authentication (MFA): Adds an extra layer of security.

9. If you have large number of IAM users in your organization. How will you manage and audit the IAM permission?
    1. Use IAM Roles Instead of IAM Users
    2. Implement Least Privilege Principle
    3. Utilize AWS Organizations and Service Control Policies (SCPs)
    4. Regularly Review IAM Policies and Permissions
    5. Enable IAM Access Analyzer
    6. Utilize AWS CloudTrail for Auditing or Automate Audits with AWS Config.
    7. Use Permission Boundaries
    8. Implement Reporting and Dashboards using cloudwatch.

10. Ways to protect your IAM credentials:
    1. Use IAM Roles Instead of Access Keys
    2. Limit Permissions with Least Privilege Principle
    3. Enable Multi-Factor Authentication (MFA)
    4. Rotate Access Keys Regularly
    5. Audit IAM Credentials Usage
    6. Implement Strong Password Policies
    7. Limit the Use of Root Account.
    8. you can use AWS cloudtrail to activate IAM activity.

11. Automating IAM password rotation in AWS can be done using AWS services such as AWS Lambda, AWS Identity and Access Management (IAM), and Amazon CloudWatch Events. 
    -   Below are the steps to set up an automated password rotation for IAM users every 90 days.
        1. Create an IAM Policy that grants permissions to change passwords for IAM users by defining the policy.
        2. Attach the Policy to an IAM role that will be used by the Lambda function.
        3. Create a Lambda Function:
            1. Select "Author from Scratch," and provide function name, runtime (e.g., Python or Node.js), and IAM role permissions (attach the policy created earlier).
            2. Add Code to the Lambda Function to change the IAM user passwords.
            3. Deploy the Lambda Function.
        4. Create a CloudWatch Event Rule:
            1. Go to Amazon CloudWatch or EventBridge and create a new rule.
            2. Set the rule to trigger every 90 days. Use a cron expression
                ```
                cron(0 0 1 */3 ? *) # This runs at midnight UTC on the first day of every third month.
                ```
            3. Set the Target of the Rule to invoke the Lambda function. 
            4. Pass parameters in the Input section of the event configuration to specify the IAM user whose password will be rotated
        5. Generate and Store New Passwords:
            - Consider storing the generated passwords securely. You might integrate AWS Secrets Manager in your Lambda function to store and retrieve passwords. This ensures that passwords are managed securely.
        6. Test the Lambda Function manually to ensure it updates the password correctly for the specified user.
        7. Monitor the execution through CloudWatch Logs to confirm that the password rotation occurs correctly at the scheduled intervals.

--------------------------------------------------------------------------------------

## VPC:

-   Virtual private network
-   It is logically isolated virtual network in aws cloud where you can launch aws resources.
-   Each VPC that you create is logicall isolated from other.
-   It allows you to have full control over your virtual networking environment, including selecting your IP address range, creating subnets, configuring route tables, and setting up network gateways.
- **Default VPC:**
    -   Pre-configured VPC that is automatically created for each AWS account in every AWS region.
- **Components of VPC**
    - **Subnets:**
        - Subdivision of VPC's IP address range
        - Can create multiple subnets within a VPC.
    - **Route Tables:**
        - They **control traffic between subnets within the VPC and the internet.**
        - Each subnet must be associated with a route table that specifies the routing rules.
    - **Internet Gateway:**
        - It is a horizontally scalable and highly available AWS-manages gateway that **allows communication between your VPC and the Internet**
    - **NAT Gateway**:
        -   It allows instances in your private subnets to communicate with the internet while blocking inboud traffic initiated from the internet.
        -   It provides internet access for private instance without exposing their IP addresses to the public.
    - **ecurity group:**
        -   Acts as firewall for your instances.
        -   They control inbound and outbound traffic based on user-defined rules.
    - **Network ACLs(access control list)**
        -   subnet level firewall.
    - **VPC peering:**
        -   It enables you to connect multiple VPCs together, allowing them to communicate as if they were on the same network.

-------------------------------------------------------------------------------