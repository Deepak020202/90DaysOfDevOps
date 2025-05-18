# Week 8: Terraform (Infrastructure as Code) Challenge

This set of tasks is designed as part of the 90DaysOfDevOps challenge to simulate complex, real-world scenarios you might encounter on the job or in technical interviews. By completing these tasks on the [online_shop repository](https://github.com/Amitabh-DevOps/online_shop), you'll gain practical experience with advanced Terraform topics, including provisioning, state management, variables, modules, workspaces, resource lifecycle management, drift detection, and environment management.


---

## Task 1: Install Terraform, Initialize, and Provision a Basic Resource

**Scenario:**  
Begin by installing Terraform, initializing a project, and provisioning a basic resource (e.g., an AWS EC2 instance) to validate your setup.

**Steps:**
1. **Install Terraform:**  
   - Download and install Terraform on your local machine.
   
   ![image](https://github.com/user-attachments/assets/ee8aa5b1-ee3b-4dbe-b604-79e5b5007ffe)

2. **Initialize a Terraform Project:**  
   - Create a new directory for your Terraform project.
   - Run `terraform init` to initialize the project.

![image](https://github.com/user-attachments/assets/844908f7-0bb9-46b3-b640-0bc2456a288d)

3. **Provision a Basic Resource:**  
   - Create a configuration file (e.g., `main.tf`) to provision an AWS EC2 instance (or a similar resource for your cloud provider).
   - Run `terraform apply` and confirm the changes.
   - 
![image](https://github.com/user-attachments/assets/f8a5b7ce-6630-4bcc-88e3-a3e2757cecc3)


     
4. **Document in `solution.md`:**
### Include the installation steps, your `main.tf` file, and the output of your `terraform apply` command.
- Terraform Installation on Linux (Ubuntu/Debian)
- Step 1: Update Packages
```
sudo apt-get update && sudo apt-get upgrade -y
```
- Step 2: Install Required Dependencies
```
sudo apt-get install -y gnupg software-properties-common curl
```
- Step 3: Add the HashiCorp GPG Key
```
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```
- step 4: Add the Official HashiCorp Repository
```
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```
- step 5: Install Terraform
```
sudo apt update
sudo apt install terraform -y
```
**Interview Questions:**
### How does Terraform manage resource creation and state?
 ---> 
 - 1.Reads your configuration files (.tf)
These files declare what infrastructure you want — like EC2 instances, VPCs, or S3 buckets.

- 2.Plans what needs to change
Terraform compares what you want (your config) vs what exists (in the state file).
→Example: If your config says “create 2 EC2 instances” and none exist, it will plan to create 2.

### What is the significance of the `terraform init` command in a new project?
---> 
- Terraform uses a file called terraform.tfstate to keep track of the real infrastructure it has created.
- Think of the state file as a “receipt” — it records:
- What resources were created
- Their IDs and properties
- How they relate to your .tf config

---

## Task 2: Manage Terraform State with a Remote Backend

**Scenario:**  
Ensuring state consistency is critical when multiple team members work on infrastructure. Configure a remote backend (e.g., AWS S3 with DynamoDB for locking) to store your Terraform state file.

**Steps:**
1. **Configure a Remote Backend:**  
   - Create a backend configuration in your `main.tf` or a separate backend file to configure a remote backend.

![image](https://github.com/user-attachments/assets/079156e6-82bc-49ec-baac-be165dde5509)

2. **Reinitialize Terraform:**  
   - Run `terraform init` to reinitialize your project with the new backend.

 ![image](https://github.com/user-attachments/assets/2df2d044-4857-4142-82f5-077095052065)


![image](https://github.com/user-attachments/assets/1c37c622-da46-47b7-a921-57f8bfa96423)

     
3. **Document in `solution.md`:**  
   - Include the backend configuration details.
   
  ```backend "s3" {
  bucket = "bucket-backend-tff"
  key = "terraform.tfstate"
  region = "ap-south-1"
  dynamodb_table = "Dynamo-Table"
```
   - Explain the benefits of using a remote backend and state locking in collaborative environments.
     1. Prevent Conflicts with State Locking
    
     2. Centralized State with Remote Backend
    
     3. Backup and Recovery

     4. Better Team Workflow
     
**Interview Questions:**
### Why is remote state management important in Terraform?
--->
1. Centralized Source of Truth
All team members access one shared state file, stored in the cloud (e.g., AWS S3).

2. Supports State Locking
When you use services like DynamoDB with S3, Terraform can lock the state file while one person is applying changes.

3. Version History / Rollback
Services like AWS S3 or Terraform Cloud support state file versioning.

### How does state locking prevent conflicts during collaborative updates?
--->
Using a remote backend with locking (like AWS S3 + DynamoDB):

1. Dev A starts terraform apply –> Lock is acquired in DynamoDB.
2. Dev B tries terraform apply –> Terraform shows a lock error.
3. Dev B must wait until the lock is released before making changes.

---

## Task 3: Use Variables, Outputs, and Workspaces

**Scenario:**  
Improve the flexibility and reusability of your Terraform configuration by using variables, outputs, and workspaces to manage multiple environments.

**Steps:**
1. **Define Variables and Outputs:**  
   - Create a `variables.tf` file to define configurable parameters (e.g., region, instance type).

   ![image](https://github.com/user-attachments/assets/3752f594-5082-49aa-8616-a6b4ceaea0f2)


   - Create an `outputs.tf` file to output key information (e.g., public IP address of the EC2 instance).

     ![image](https://github.com/user-attachments/assets/16d7247e-157a-4898-9cbb-068bcc5e8b12)

2. **Implement Workspaces:**  
   - Use `terraform workspace new` to create separate workspaces for different environments (e.g., dev, staging, prod).

![image](https://github.com/user-attachments/assets/2e5dc93b-dfa2-493d-861a-b053f5b0917b)

![image](https://github.com/user-attachments/assets/7635efe5-7455-41a7-a829-ab81e6c7273a)

  
3. **Document in `solution.md`:**  
### Include your `variables.tf`, `outputs.tf`, and a summary of your workspace setup.

- 1.variables.tf = Accepts input values like environment name, tags, region, etc.
- 2.outputs.tf =	Exposes important info per environment (e.g., IPs, URLs)
- 3.Workspaces	= Keeps each environment isolated by using separate state files
  
### Explain how these features enable dynamic and multi-environment deployments.

- 1. variables.tf – Inject Environment-Specific Values
This file defines input variables that make your configuration dynamic.

- 2. outputs.tf – Get Useful Info Per Environment
This file prints values like public IP, instance ID, or DNS name after Terraform runs.

- 3. Workspaces – Keep Environments Isolated
Workspaces let you create separate state files for each environment.

**Interview Questions:**
### How do variables and outputs enhance the reusability of Terraform configurations?
--->
- Variables Make Code Dynamic
Variables allow you to parameterize your Terraform configuration. Instead of hardcoding values (like instance types, region, etc.), you use variables that can change based on input.

- Outputs Expose Key Resource Info
Outputs display values from your resources — like IP addresses, instance IDs, or names — after terraform apply.

### What is the purpose of workspaces in Terraform, and how would you use them in a production scenario?
--->
- A workspace = a separate instance of your infrastructure managed with its own Terraform state file.
- Without workspaces, you'd need to duplicate your code for each environment (like dev.tf, prod.tf).
  Workspaces let you:
  1. Use a single configuration
  2. Keep state isolated
  3. Avoid conflicts between environments

## Task 4: Create and Use Terraform Modules

**Scenario:**  
Enhance reusability by creating a Terraform module for commonly used resources, and integrate it into your main configuration.

**Steps:**
1. **Create a Module:**  
   - In a separate directory (e.g., `modules/ec2_instance`), create a module with `main.tf`, `variables.tf`, and `outputs.tf` for provisioning an EC2 instance.

![image](https://github.com/user-attachments/assets/d1a856ec-c133-4090-be4c-797ce4ef5dff)


![image](https://github.com/user-attachments/assets/d5bb7d5a-8bd0-4732-8d57-f342f3d7422b)

     
2. **Reference the Module:**  
   - Update your main configuration to call the module using a `module` block.

![image](https://github.com/user-attachments/assets/e2d15f1f-e81a-43b7-b1c1-96c4ef4b2e71)

![image](https://github.com/user-attachments/assets/633c239f-229a-4240-adc4-b516c582c14f)

     
3. **Document in `solution.md`:**  
#### Provide the module code and the main configuration.
```
module "ec2_instance" {
  source  = "terraform-aws-modules/ec2-instance/aws"

  name = "auto-instance"

  ami           = "ami-0e35ddab05955cf57" # Amazon Linux 2023 AMI
  instance_type = "t2.micro"
  key_name      = aws_key_pair.my_key.key_name

  subnet_id              = data.aws_subnet.default_subnet.id
  vpc_security_group_ids = [aws_security_group.my_sg.id]
  monitoring             = true

  tags = {
    Terraform   = "true"
    Environment = "dev"
  }
}
```

#### Explain how modules promote consistency and reduce code duplication.
--->
##### How Modules Promote Consistency
- Standardized Configuration:
All environments (dev, test, prod) use the same logic by calling the same module. This ensures uniform naming, tagging, and settings across infrastructure.

- Single Source of Truth:
Any update to the module (like enabling logging on S3 buckets) automatically applies to all environments using that module — reducing the risk of inconsistency.

#### How Modules Reduce Code Duplication
-  Without Modules:
You'd copy-paste the same EC2 block 15 times (5 per environment × 3).
This leads to:

Repetitive code

Difficult maintenance

Higher chances of manual errors

- With Modules:
You write the EC2 logic once inside a module and call it multiple times with different variables.

**Interview Questions:**
### What are the advantages of using modules in Terraform?
--->

### How would you structure a module for reusable infrastructure components?
--->
- 1. Reusability = Write once, use anywhere.
- 2. Organization = Break your Terraform code into smaller, manageable components.
- 3. Maintainability = If a change is needed (e.g., enable monitoring), you update the module — not every instance.
- 4. Consistency = Modules ensure uniform settings for naming, tags, security policies, etc., across all resources and environments.
---

## Task 5: Resource Dependencies and Lifecycle Management

**Scenario:**  
Ensure correct resource creation order and safe updates by managing dependencies and customizing resource lifecycles.

**Steps:**
1. **Define Resource Dependencies:**  
   - Use the `depends_on` meta-argument in your configuration to specify dependencies explicitly.

![image](https://github.com/user-attachments/assets/9197ed52-5c36-4399-bc2e-bb381277a35d)
  
2. **Configure Resource Lifecycles:**  
   - Add lifecycle blocks (e.g., `create_before_destroy`) in your resource definitions to manage updates safely.
  
![image](https://github.com/user-attachments/assets/c04ae16a-f1d0-4ef5-bf57-ccdb5fc93a8a)

3. **Document in `solution.md`:**  
#### Include examples of resource dependencies and lifecycle configurations in your code.
--->
`depends_on    = [aws_security_group.web_sg]`
- Ensures AWS EC2 instance is launched only after the security group is created.
- Prevents errors like: “Security group not found.”
  
#### Explain how these settings prevent downtime during updates.
---> 
- Protects critical infrastructure (e.g., databases, backup buckets) from being deleted.
- Forces the user to manually remove this lifecycle rule before Terraform can delete the resource.

**Interview Questions:**
#### How does Terraform handle resource dependencies?
---> 
- Terraform handles resource dependencies automatically through dependency graphing, and manually using the depends_on keyword.
- Sometimes resources are not directly referenced, but one still needs to wait for the other. In such cases, use depends_on.

#### Can you explain the purpose of the `create_before_destroy` lifecycle argument?
---> 
- When a resource needs to be replaced (for example, changing an immutable attribute like an AMI in an EC2 instance), Terraform by default:
- Destroys the old resource.
- Then creates the new one.
  
- This can cause downtime if the old resource is in production (e.g., EC2 instance, load balancer, etc.).
- With create_before_destroy = true, Terraform does this instead:
- Creates the new resource first.Once it’s successfully created, it destroys the old one.

## Task 6: Infrastructure Drift Detection and Change Management

**Scenario:**  
In production, changes might occur outside of Terraform. Use Terraform commands to detect infrastructure drift and manage changes.

**Steps:**
1. **Detect Drift:**  
   - Run `terraform plan` to identify differences between your configuration and the actual infrastructure.

![image](https://github.com/user-attachments/assets/96d85fb0-3eeb-44f4-8006-89cf59fcd1ae)


2. **Reconcile Changes:**  
#### Describe your approach to updating the state or reapplying configurations when drift is detected.
---> You changed the instance type of an EC2 instance via AWS Console from t2.micro to t2.small.
- Run terraform plan: shows EC2 instance will be replaced (back to t2.micro)
- You decide the new size is correct → update your Terraform config to t2.small
- Run terraform apply: Terraform now reflects the new size in its state

3. **Document in `solution.md`:**  
#### Q) Include examples of drift detection and your strategy for reconciling differences.
--->

#### Q) Reflect on the importance of change management in infrastructure as code.
--->
- Scenario:
A new S3 bucket was created manually in AWS (not using Terraform).

- Detection:
Terraform won’t detect it because it only knows about what’s defined in .tf files.

- To bring it under Terraform’s control
`terraform import aws_s3_bucket.example bucket-name`

**Interview Questions:**
#### Q) What is infrastructure drift, and why is it a concern in production environments?
--->  
- Infrastructure drift occurs when the actual state of your infrastructure changes outside of Terraform, meaning changes are made manually
- 
#### Q)  How would you resolve discrepancies between your Terraform configuration and actual infrastructure?
---> Drift a Concern in Production
- 1.Inconsistent State
Terraform believes the infrastructure is one way, but reality is different — leading to unexpected behavior.
- 2.Unpredictable Changes
Applying Terraform changes may accidentally override critical manual changes, causing downtime or data loss.
- 3.Security Risks
Manually changed firewall rules or IAM policies may open up vulnerabilities.
- 4.Debugging Complexity
It becomes hard to troubleshoot when infrastructure doesn’t match the code, increasing time to resolution.
- 5.Non-compliance
Manual changes bypass auditing, versioning, and approval processes, leading to compliance violations.


## Task 7: (Optional) Dynamic Pipeline Parameterization for Terraform

**Scenario:**  
Enhance your Terraform configurations by using dynamic input parameters and conditional logic to deploy resources differently based on environment-specific values.

**Steps:**
1. **Enhance Variables with Conditionals:**  
   - Update your `variables.tf` to include default values and conditional expressions for environment-specific configurations.

![image](https://github.com/user-attachments/assets/6bfca218-91c4-47ee-859a-e8a34858ee9b)

2. **Apply Conditional Logic:**  
   - Use conditional expressions in your resource definitions to adjust attributes based on variable values.

![image](https://github.com/user-attachments/assets/2b3dda45-02f5-40c8-9587-22b018ad2597)

3. **Document in `solution.md`:**  
#### Q) Explain how dynamic parameterization improves flexibility.
--->
- Dynamic parameterization in Terraform refers to using variables and input values (instead of hardcoded values) to define infrastructure. It allows users to customize configurations at runtime, making modules and resources reusable and flexible.
  
#### Q) Include sample outputs demonstrating different configurations.

![image](https://github.com/user-attachments/assets/751dab9d-a512-4d1d-ad1d-3b82e955f2c6)

 
**Interview Questions:**
#### Q) How do conditional expressions in Terraform improve configuration flexibility?
---> 
- Conditional expressions in Terraform improve configuration flexibility by allowing you to dynamically assign values based on conditions—without duplicating code. This makes your infrastructure adaptive, reusable, and easier to manage across different environments or use cases.

#### Q) Provide an example scenario where dynamic parameters are critical in a deployment pipeline.
--->
##### The team maintains separate AWS infrastructure for:
- Development (dev)
- Staging (staging)
- Production (prod)

##### Each environment requires:
- Different instance sizes
- Different number of instances
- Different regions
- Different tags for billing and audit

You use Terraform modules for infrastructure as code and deploy using GitHub Actions CI/CD.


### **Bonus Task: Multi-Environment Setup with Terraform & Ansible **

**Scenario:**  
Set up **AWS infrastructure** for multiple environments (dev, staging, prod) using **Terraform** for provisioning and **Ansible** for configuration. This includes installing both tools, creating dynamic inventories, and automating Nginx configuration across environments.

1. **Install Tools:**  
   - Install **Terraform** and **Ansible** on your local machine.

2. **Provision AWS Infrastructure with Terraform:**  
   - Create Terraform files to spin up EC2 instances (or similar resources) in dev, staging, and prod.
   - Apply configurations (e.g., `terraform apply -var-file="dev.tfvars"`) for each environment.

3. **Configure Hosts with Ansible:**  
   - Generate **dynamic inventories** (or separate inventory files) based on Terraform outputs.
   - Write a playbook to install and configure **Nginx** across all environments.
   - Run `ansible-playbook -i <inventory> nginx_setup.yml` to automate the setup.

4. **Automate & Document:**  
   - Ensure infrastructure changes are version-controlled.
   - Place all steps, commands, and observations in `solution.md`.

**Interview Questions :**
- **Terraform & Ansible Integration:** How do you share Terraform outputs (host details) with Ansible inventories?
- **Multi-Environment Management:** What strategies ensure consistency while keeping dev, staging, and prod isolated?
- **Nginx Configuration:** How do you handle environment-specific differences for Nginx setups?

---
