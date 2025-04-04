# Week 6 Solutions : Jenkins ( CI/CD ) Basics and Advanced real world challenge  

---

## Task 1: Create a Jenkins Pipeline Job for CI/CD

**Scenario:**  
Create an end-to-end CI/CD pipeline for a sample application.

**Steps:**
1. **Set Up a Pipeline Job:**  
   - Create a new Pipeline job in Jenkins.
   - Write a basic Jenkinsfile that automates the build, test, and deployment of a sample application (e.g., a simple web app).  
   - Suggested stages: **Build**, **Test**, **Deploy**.
2. **Run and Verify the Pipeline:**  
   - Trigger the pipeline and ensure each stage runs successfully.
   - Verify the execution by checking console logs and, if applicable, using `docker ps` to confirm container status.
3. **Document in `solution.md`:**  
   - Include your Jenkinsfile code and explain the purpose of each stage.
   - Note any issues you encountered and how you resolved them.

** Questions:**
- How do declarative pipelines streamline the CI/CD process compared to scripted pipelines?
- What are the benefits of breaking the pipeline into distinct stages?

# Solution 

## Task1.1 **Set Up a Pipeline Job:**  

![image](https://github.com/user-attachments/assets/741b1e53-b62d-416d-bdcc-5415dfee2449)

![image](https://github.com/user-attachments/assets/5126bf92-1e3e-469d-a7e7-e487fa004ab1)

## Task1.2 **using docker ps to confirm container status.**

![image](https://github.com/user-attachments/assets/23c22501-df66-4384-9b3e-313d8084bea9)

## Task 1.3  Pipeline code
```
pipeline{
    agent any;
    stages{
        stage("Code Build "){
            steps{
        echo " Code Buid is succesufully "
            }
        }
        stage("code test"){
            steps{
                echo "Code is succesfully tested"
            }
        }
        stage("code deploy"){
            steps{
                echo "Code is succesfully deployed!!!"
                sh "docker ps"
            }
        }
    }
}
```
** Questions:**
### 1. How do declarative pipelines streamline the CI/CD process compared to scripted pipelines?

### Answer--> declarative pipelines streamline the CI/CD process by providing a simple, structured way to define workflows with minimal scripting. This makes them more accessible, maintainable, and less error-prone compared to scripted pipelines, which are better suited for highly customized or complex workflows.

### 2. What are the benefits of breaking the pipeline into distinct stages?

### Answer--> Breaking the pipeline into distinct stages offers many advantages:

   1.Improved clarity and readability, making it easier to understand the pipeline's flow.

   2.Better maintainability with modular design and easier updates.

   3.Parallel execution to speed up the pipeline.

   4.Clearer error isolation and easier troubleshooting.

   5.Granular notifications and better control over pipeline execution.

   6.Efficient resource management by tailoring resources for specific stages.

   7.Compliance and auditing by tracking each stage's execution and results.

## Task 2: Build a Multi-Branch Pipeline for a Microservices Application

**Scenario:**  
You have a microservices-based application with multiple components stored in separate Git repositories. Your goal is to create a multi-branch pipeline that builds, tests, and deploys each service concurrently.

**Steps:**
1. **Set Up a Multi-Branch Pipeline Job:**  
   - Create a new multi-branch pipeline in Jenkins.
   - Configure it to scan your Git repository (or repositories) for branches.
2. **Develop a Jenkinsfile for Each Service:**  
   - Write a Jenkinsfile that includes stages for **Checkout**, **Build**, **Test**, and **Deploy**.  
   - Include parallel stages if applicable (e.g., running tests for different services concurrently).
3. **Document in `solution.md`:**  
   - List the Jenkinsfile(s) used, explain your pipeline design, and describe how multi-branch pipelines help manage microservices deployments in production.

** Questions:**
- How does a multi-branch pipeline improve continuous integration for microservices?
- What challenges might you face when merging feature branches in a multi-branch pipeline?

# Solution :-

### Running multi stage pipeline that include Code clone , build test and deploy to run the Flask app and SQL web application using docker tool.

![image](https://github.com/user-attachments/assets/8a0fbf83-9eee-431c-9f4d-02ed284b61e4)



![image](https://github.com/user-attachments/assets/5324eb6e-8391-49be-a2d5-f954914b681c)

** Questions:**
## 1.How does a multi-branch pipeline improve continuous integration for microservices?

### Answer --> Multi-branch pipelines allow Jenkins to dynamically create and manage pipelines for each branch in a repository. This is particularly useful for microservices in production for the following reasons:

### ✅ 1. Isolated Testing for Different Features

Developers can work on feature branches (feature/new-auth), and Jenkins will automatically detect and run a separate pipeline for that branch.

This ensures new changes don’t affect the stable code until merged into main or develop.

### ✅ 2. CI/CD for Multiple Services

In a microservices architecture, each service may have its own repository and pipeline.

Multi-branch pipelines allow Jenkins to trigger builds only for changed microservices, reducing deployment time.

### ✅ 3. Automated PR Testing

When a developer opens a pull request (PR), Jenkins can automatically test the branch before merging.

This ensures only high-quality code enters production.

### ✅ 4. Easier Rollbacks & Hotfixes

If a deployment fails, you can quickly switch to a previous branch and deploy a stable version.

Separate pipelines for hotfix branches allow rapid bug fixes without affecting ongoing development.

### ✅ 5. Parallel Deployments for Different Environments
You can define different branches for different environments:

develop → Staging

main → Production

Jenkins runs different pipelines for each environment, ensuring safe deployments.

## 2. What challenges might you face when merging feature branches in a multi-branch pipeline?
### Answer :-  while merging feature branches in a multi-branch pipeline conflict error are comes 
### How to avoid this ?
### 1.Always rebase your feature branch with latest master before merge
### 2.enkins should run tests/builds on PRs before allowing merges
### 3.Only allow merge if Jenkins pipeline shows green status

---

## Task 3: Configure and Scale Jenkins Agents/Nodes

**Scenario:**  
Your build workload has increased, and you need to configure multiple agents (across different OS types) to distribute the load.

**Steps:**
1. **Set Up Multiple Agents:**  
   - Configure at least two agents (e.g., one Linux-based and one Windows-based) in Jenkins.
   - Use Docker containers or VMs to simulate different environments.
2. **Label Agents:**  
   - Assign labels (e.g., `linux`, `windows`) and modify your Jenkinsfile to run appropriate stages on the correct agent.
3. **Run Parallel Jobs:**  
   - Create jobs that run in parallel across these agents.
4. **Document in `solution.md`:**  
   - Explain how you configured and verified each agent.
   - Describe the benefits of distributed builds in terms of speed and reliability.

** Questions:**
- What are the benefits and challenges of using distributed agents in Jenkins?
- How can you ensure that jobs are assigned to the correct agent in a multi-platform environment?

# Solution :- 
## setup agnet 

![image](https://github.com/user-attachments/assets/0a0f9ea6-daeb-488a-a847-07d19a5b66e6)


![image](https://github.com/user-attachments/assets/4f98c49a-3adc-4738-b245-7d0427b50758)

## Label Agent 
![image](https://github.com/user-attachments/assets/7e86b0fb-2089-422e-be9b-cda336743eae)

## To simulate environments running jenkins in docker container
![image](https://github.com/user-attachments/assets/01ffcf95-dfde-404d-8308-65b6f688baa2)


## Run parellel agent Job
![image](https://github.com/user-attachments/assets/0ea7d8ae-a055-47b7-bdd2-1a801dbd91b7)


![image](https://github.com/user-attachments/assets/b69a98f3-bf05-4369-a78b-3858fc45aacf)

** Questions:**
## 1. Explain how you configured and verified each agent ?
## Answer :- to verify agent via ssh these steps are involved -
### 1. create a node/agent
### 2. generate ssh-key on master agent
### 3. upload private key on jenkins 
### 4. add public key of master into private ssh file in agent-node's   

## 2.Describe the benefits of distributed builds in terms of speed and reliability.
## Answer :-
## Speed Improvement
### 1.Parallel Execution
### 2.Load Balancing
### 3.Faster Feedback Loop
## Improved Reliability
### 1.Failure Isolation
### 2.High Availability
### 3.Scalability



## Jenkinsfile for agents
```
pipeline { 
    agent {label "Dev"};
    stages{
        stage(" Code Clone "){
            steps{
        git branch: "master", url: "https://github.com/Deepak020202/two-tier-flask-app.git"
            }
        }
        stage("Code Build "){
            steps{
        sh "docker build -t flask-app ."
            }
        }
        stage("code test"){
            steps{
                echo "code is testedd"
            }
        }
        stage("code deploy"){
            steps{
                sh 'docker-compose up -d'
            }
        }
    }
}
```

---

## Task 4: Implement and Test RBAC in a Multi-Team Environment

**Scenario:**  
In a large organization, different teams (developers, testers, and operations) require different levels of access to Jenkins. You need to configure RBAC to secure your CI/CD pipeline.

**Steps:**
1. **Configure RBAC:**  
   - Use Matrix-based security or the Role Strategy Plugin to create roles (e.g., Admin, Developer, Tester).
   - Define permissions for each role.
2. **Create Test Accounts:**  
   - Simulate real-world usage by creating user accounts for each role and verifying access.
3. **Document in `solution.md`:**  
   - Include screenshots or logs of your RBAC configuration.
   - Explain the importance of access control and provide a potential risk scenario that RBAC helps mitigate.

** Questions:**
- Why is RBAC essential in a CI/CD environment, and what are the consequences of weak access control?
- Can you describe a scenario where inadequate RBAC could lead to security issues?

# Solution :-

1. **Configure RBAC:**  
### Use Matrix-based security or the Role Strategy Plugin to create roles (e.g., Admin, Developer, Tester).

![image](https://github.com/user-attachments/assets/5cf310ee-7279-4faa-a86d-40bb684abe38)

![image](https://github.com/user-attachments/assets/3817141b-81f0-4db8-b544-106db9b198f9)

### Define permissions for each role.

![image](https://github.com/user-attachments/assets/3730d1c0-3d61-4376-9db7-27d5ccbdb50d)

![image](https://github.com/user-attachments/assets/dbd3782e-8185-480e-86a2-b9573a0fe985)

2. **Create Test Accounts:**  
## Simulate real-world usage by creating user accounts for each role and verifying access.
### after implementing RBAC the Jhon user unable to access **manage jenkins tab ** 

![image](https://github.com/user-attachments/assets/e8cd091e-0edb-4480-802c-f3836d113e78)

** Questions:**
## Why is RBAC essential in a CI/CD environment, and what are the consequences of weak access control?
### Answer :- Consequences of Weak Access Control:
1.Unauthorized Code Changes – Developers with excessive privileges could push unapproved changes, introducing vulnerabilities.

2.Exposure of Sensitive Credentials – Weak access control might allow unauthorized users to access secrets like API keys or database credentials.

3.Deployment Failures & Downtime – If unauthorized users trigger deployments or modify pipeline configurations, it could lead to service disruptions.

4.Data Leaks & Compliance Violations – A lack of RBAC enforcement can expose sensitive information, leading to non-compliance with regulations like GDPR or HIPAA.

5.Compromised Build Environment – Attackers or insiders with elevated permissions could inject malicious code into the pipeline. 

## Can you describe a scenario where inadequate RBAC could lead to security issues?-
### Answer :- A junior developer has full administrative access to the CI/CD pipeline. One day, they accidentally expose AWS credentials in a public repository. A malicious actor finds these credentials and gains unauthorized access to the production environment, leading to data theft and service downtime.
---

## Task 5: Develop and Integrate a Jenkins Shared Library

**Scenario:**  
You are working on multiple pipelines that share common tasks (like code quality checks or deployment steps). To avoid duplication and ensure consistency, you need to develop a Shared Library.

**Steps:**
1. **Create a Shared Library Repository:**  
   - Set up a separate Git repository that hosts your shared library code.
   - Develop reusable functions (e.g., a function for sending notifications or a common test stage).
2. **Integrate the Library:**  
   - Update your Jenkinsfile(s) from previous tasks to load and use the shared library.
   - Use syntax similar to:
     ```groovy
     @Library('my-shared-library') _
     pipeline {
         // pipeline code using shared functions
     }
     ```
3. **Document in `solution.md`:**  
   - Provide code examples from your shared library.
   - Explain how this approach improves maintainability and reduces errors.

** Questions:**
- How do shared libraries contribute to code reuse and maintainability in large organizations?
- Provide an example of a function that would be ideal for a shared library and explain its benefits.

---

## Task 6: Integrate Vulnerability Scanning with Trivy

**Scenario:**  
Security is critical in CI/CD. You must ensure that the Docker images built in your pipeline are free from known vulnerabilities.

**Steps:**
1. **Add a Vulnerability Scan Stage:**  
   - Update your Jenkins pipeline to include a stage that runs Trivy on your Docker image:
     ```groovy
     stage('Vulnerability Scan') {
         steps {
             sh 'trivy image <your-username>/sample-app:v1.0'
         }
     }
     ```
2. **Configure Fail Criteria:**  
   - Optionally, set the stage to fail the build if critical vulnerabilities are detected.
3. **Document in `solution.md`:**  
   - Summarize the scan output, note the vulnerabilities and severity, and describe any remediation steps.
   - Reflect on the importance of automated security scanning in CI/CD pipelines.

**Interview Questions:**
- Why is integrating vulnerability scanning into a CI/CD pipeline important?
- How does Trivy help improve the security of your Docker images?

---

## Task 7: Dynamic Pipeline Parameterization

**Scenario:**  
In production environments, pipelines need to be flexible and configurable. Implement dynamic parameterization to allow the pipeline to accept runtime parameters (such as target environment, version numbers, or deployment options).

**Steps:**
1. **Modify Your Jenkinsfile:**  
   - Update your Jenkinsfile to accept parameters. For example:
     ```groovy
     pipeline {
         agent any
         parameters {
             string(name: 'TARGET_ENV', defaultValue: 'staging', description: 'Deployment target environment')
             string(name: 'APP_VERSION', defaultValue: '1.0.0', description: 'Application version to deploy')
         }
         stages {
             stage('Build') {
                 steps {
                     echo "Building version ${params.APP_VERSION} for ${params.TARGET_ENV} environment..."
                     // Build commands here
                 }
             }
             // Add other stages as needed
         }
     }
     ```
2. **Run the Parameterized Pipeline:**  
   - Trigger the pipeline and provide different parameter values to observe how the pipeline behavior changes.
3. **Document in `solution.md`:**  
   - Explain how parameterization makes the pipeline dynamic.
   - Include sample outputs and discuss how this flexibility is useful in a production CI/CD environment.

** Questions:**
- How does pipeline parameterization improve the flexibility of CI/CD workflows?
- Provide an example of a scenario where dynamic parameters would be critical in a deployment pipeline.

---

## Task 8: Integrate Email Notifications for Build Events

**Scenario:**  
Automated notifications keep teams informed about build statuses. Configure Jenkins to send email alerts upon build completion or failure.

**Steps:**
1. **Configure SMTP Settings:**  
   - Set up SMTP details in Jenkins under "Manage Jenkins" → "Configure System".
2. **Update Your Jenkinsfile:**  
   - Add a stage that uses the `emailext` plugin to send notifications:
     ```groovy
     stage('Notify') {
         steps {
             emailext (
                 subject: "Build Notification: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                 body: "The build has completed successfully. Check details at: ${env.BUILD_URL}",
                 recipientProviders: [[$class: 'DevelopersRecipientProvider']]
             )
         }
     }

     ```
# Solution :

![image](https://github.com/user-attachments/assets/7364d1d3-9f6d-4a6e-ba3f-9e44bb5d39ca)

![image](https://github.com/user-attachments/assets/54f87c65-8aa2-4c47-a986-fed8606ead1c)

![image](https://github.com/user-attachments/assets/ad031a7b-75c7-4e02-ab36-35daef1ae244)

![image](https://github.com/user-attachments/assets/af1f9e99-9c7e-4d1e-9501-9bb2ee2fcabd)

![image](https://github.com/user-attachments/assets/bdf21bc3-7dc5-4f0f-903b-45fde468cc10)

     ---
4. **Test the Notification:**  
   - Trigger the pipeline and verify that an email is sent.
5. **Document in `solution.md`:**  
   - Explain your configuration steps, note any challenges, and describe how you resolved them.

**Interview Questions:**
- What are the advantages of automating email notifications in CI/CD?
- How would you troubleshoot issues if email notifications fail to send?

---

## Task 9: Troubleshooting, Monitoring & Advanced Debugging

**Scenario:**  
Real-world CI/CD pipelines sometimes fail. Demonstrate how you would troubleshoot and monitor your Jenkins environment.

**Steps:**
1. **Troubleshooting:**  
   - Simulate a pipeline failure (e.g., by introducing an error in the Jenkinsfile) and document your troubleshooting process.
   - Use commands like `docker logs` and review Jenkins console output.
2. **Monitoring:**  
   - Describe methods for monitoring Jenkins, such as using system logs or monitoring plugins.
3. **Advanced Debugging:**  
   - Add debugging statements (e.g., `echo` commands) in your Jenkinsfile to output environment variables or intermediate results.
   - Use Jenkins' "Replay" feature to test modifications without committing changes.
4. **Document in `solution.md`:**  
   - Provide a detailed account of your troubleshooting, monitoring, and debugging strategies.
   - Reflect on how these practices help maintain a stable CI/CD environment.

** Questions:**
- How would you approach troubleshooting a failing Jenkins pipeline?
- What are some effective strategies for monitoring Jenkins in a production environment?

# Solution 

![image](https://github.com/user-attachments/assets/22e6a058-fe34-4a76-8ff3-a3296cab761b)


---

## How to Submit

1. **Push Your Final Work to GitHub:**  
   - Ensure all files (e.g., Jenkinsfile, configuration scripts, `solution.md`, etc.) are committed and pushed to your repository.

2. **Create a Pull Request (PR):**  
   - Open a PR from your branch (e.g., `jenkins-challenge`) to the main repository.
   - **Title:**  
     ```
     Week 6 Challenge - DevOps Batch 9: Jenkins CI/CD Challenge
     ```
   - **PR Description:**  
     - Summarize your approach, list key commands/configurations, and include screenshots or logs as evidence.

3. **Share Your Experience on LinkedIn:**  
   - Write a post summarizing your Jenkins challenge experience.
   - Include key takeaways, challenges faced, and insights (e.g., agent configuration, RBAC, shared libraries, vulnerability scanning, and troubleshooting).
   - Use the hashtags: **#90DaysOfDevOps #Jenkins #CI/CD #DevOps #InterviewPrep**
   - Optionally, provide links to your repository or blog posts detailing your journey.

---


## TrainWithShubham Resources for Jenkins CI/CD

- **[Jenkins Short notes](https://www.trainwithshubham.com/products/64aac20780964e534608664d?dgps_u=l&dgps_s=ucpd&dgps_t=cp_u&dgps_u_st=p&dgps_uid=66c972da3795a9659545d71a)**  
- **[Jenkins One-Shot Video](https://youtu.be/XaSdKR2fOU4?si=eDmLQMSSh_eMPT_p)** 
- **[TWS blog on Jenkins CI/CD](https://trainwithshubham.blog/automate-cicd-spring-boot-banking-app-jenkins-docker-github/)**  

## Additional Resources

- **[Jenkins Official Documentation](https://www.jenkins.io/doc/)**  
- **[Jenkins Pipeline Documentation](https://www.jenkins.io/doc/book/pipeline/)**  
- **[Jenkins Agents and Nodes](https://www.jenkins.io/doc/book/managing/nodes/)**  
- **[Jenkins RBAC & Role Strategy Plugin](https://plugins.jenkins.io/role-strategy/)**  
- **[Jenkins Shared Libraries](https://www.jenkins.io/doc/book/pipeline/shared-libraries/)**  
- **[Trivy Vulnerability Scanner](https://trivy.dev/latest/docs/scanner/vulnerability/)**  

---

Complete these tasks, answer the interview questions in your documentation, and use your work as a reference to prepare for real-world DevOps challenges and technical interviews.
