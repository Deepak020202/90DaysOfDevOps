# Week 7 : Kubernetes Basics & Advanced Challenges

This set of tasks is designed as part of the 90DaysOfDevOps challenge to simulate real-world scenarios you might encounter on the job or in technical interviews. By completing these tasks on the [SpringBoot BankApp](https://github.com/Amitabh-DevOps/Springboot-BankApp), you'll gain practical experience with advanced Kubernetes topics, including architecture, core objects, networking, storage management, configuration, autoscaling, security & access control, job scheduling, and bonus topics like Helm, Service Mesh, or AWS EKS.

> [!IMPORTANT]
>
>  1. Fork the [SpringBoot BankApp](https://github.com/Amitabh-DevOps/Springboot-BankApp) and implement all tasks on your fork.  
>  2. Document all steps, commands, screenshots, and observations in a file named `solution.md` within your fork.  
>  3. Submit your `solution.md` file in the Week 7 (Kubernetes) task folder of the 90DaysOfDevOps repository.

---

## Task 1: Understand Kubernetes Architecture & Deploy a Sample Pod

**Scenario:**  
Familiarize yourself with Kubernetes’ control plane and worker node components, then deploy a simple Pod manually.

**Steps:**
1. **Study Kubernetes Architecture:**  
   - Review the roles of control plane components (API Server, Scheduler, Controller Manager, etcd, Cloud Controller) and worker node components (Kubelet, Container Runtime, Kube Proxy).
2. **Deploy a Sample Pod:**  
   - Create a YAML file (e.g., `pod.yaml`) to deploy a simple Pod (such as an NGINX container).
   - Apply the YAML using:
     ```bash
     kubectl apply -f pod.yaml
     ```
3. **Document in `solution.md`:**  
   - Describe the Kubernetes architecture components.
   - Include your Pod YAML and explain each section.

> [!NOTE]
> 
> **Interview Questions:**
>  - Can you explain how the Kubernetes control plane components work together and the role of etcd in this architecture?
>  - If a Pod fails to start, what steps would you take to diagnose the issue?

# Solution :-
1. **Study Kubernetes Architecture:**
## Answer:- In Kubernetes architecture total 8 componentes also it is called k8's. In architecture two main component is Control plan and worker node
## Control-Plane Component :-
### 1. API Server (`kube-apiserver`)

**Role:**  
- Entry point for all administrative tasks (via `kubectl`, UI, or API).  
- Validates and processes REST requests.  
- Communicates with etcd.

**Example:**  
When you run **kubectl apply -f pod.yml** your request goes to the API Server. It checks if the YAML is valid and passes it on to the next component.

### 2. Scheduler (`kube-scheduler`)

**Role:**  
Decides which worker node a pod should run on.

- Monitors for newly created pods that don’t have a node assigned.
- Matches pod requirements (like CPU, memory, affinity/anti-affinity, taints, and tolerations) with available nodes.
- Selects the most suitable node based on policies and resource availability.

**Example:**  
If your pod requires 2 CPUs, the scheduler checks each node’s available resources.  
It finds a node with at least 2 CPUs free and assigns the pod to that node for deployment.

### 3. Controller Manager (`kube-controller-manager`)

**Role:**  
- Watches the state of the cluster by interacting with the API Server.  
- Runs various background controllers to maintain the desired state of the cluster.  
- Controllers include:
  - **Node Controller** – Handles node failures.
  - **Replication Controller** – Ensures the desired number of pod replicas are running.
  - **Deployment Controller** – Manages rollouts and rollbacks of deployments.
  - **Endpoint Controller**, **Namespace Controller**, and more.

**Example:**  
If a pod crashes, the Replication Controller notices that the actual number of running pods is less than the desired count.  
It immediately creates a new pod to maintain the defined replica count.

### 4. etcd

**Role:**  
- The cluster’s distributed key-value store.  
- Stores all cluster data including:
  - Configuration data
  - Secrets
  - State information
  - Metadata

**Example:**  
When you define a deployment (e.g., 3 replicas of an Nginx pod), that configuration is saved in etcd.  
If the cluster is restarted or scaled, Kubernetes uses this data to restore or maintain the desired state.

### 5. Cloud Controller Manager

**Role:**  
- Integrates Kubernetes with your cloud provider (AWS, Azure, GCP).  
- Manages cloud-specific components such as:
  - Load balancers
  - Persistent volumes
  - Cloud-specific networking and routing

**Example:**  
When you create a `Service` of type `LoadBalancer`, the Cloud Controller communicates with the cloud provider’s API to provision an external load balancer and connect it to your service.

## Worker-Node

### 6. Kubelet

- **Role**: Agent on each node that ensures containers are running.
- **Responsibilities**:
  - Communicates with the API Server.
  - Works with the container runtime to launch and monitor pods.

### Example
> If the API Server instructs the Kubelet to run a pod, Kubelet pulls the image via the container runtime and ensures it stays healthy.

---

### 7. Container Runtime

- **Role**: Runs the actual containers (e.g., Docker, containerd).
- **Responsibilities**:
  - Works closely with the Kubelet to start and manage containers.
  - Pulls container images.
  - Starts and stops containers as directed.

### Example
> When a pod is assigned to a node, the container runtime pulls the image and runs the containers inside the pod.

---

### 8. Kube Proxy

- **Role**: Manages network rules and traffic routing.
- **Responsibilities**:
  - Uses `iptables` or `IPVS` to route traffic.
  - Ensures networking rules are correctly applied on the node.

### Example
> When you access a Kubernetes service, Kube Proxy routes the request to the correct pod on the correct node.

# 2. **Deploy a Sample Pod:**  
## Answer :- First created config file to create master and worker node 

![image](https://github.com/user-attachments/assets/3961b34e-b283-4dc8-b45f-e4b07cde2ff6)

## Secound create namespacefile for other component 

```
kind: Namespace
apiVersion: v1

metadata:
  name: nginx-ns
```
## Third created pod file for creating pod

```
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod
  namespace: nginx-ns

spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```
![image](https://github.com/user-attachments/assets/0bc7d605-bcdd-4f56-9890-512a93319dce)

# 
---

## Task 2: Deploy and Manage Core Kubernetes Objects

**Scenario:**  
Deploy core Kubernetes objects for the SpringBoot BankApp application, including Deployments, ReplicaSets, StatefulSets, DaemonSets, and use Namespaces to isolate resources.

**Steps:**
1. **Create a Namespace:**  
   - Write a YAML file to create a Namespace for the SpringBoot BankApp application.
   - Apply the YAML:
     ```bash
     kubectl apply -f namespace.yaml
     ```
2. **Deploy a Deployment:**  
   - Create a YAML file for a Deployment (within your Namespace) that manages a set of Pods running a component of SpringBoot BankApp.
   - Verify that a ReplicaSet is created automatically.
3. **Deploy a StatefulSet:**  
   - Write a YAML file for a StatefulSet (for example, for a database component) and apply it.
4. **Deploy a DaemonSet:**  
   - Create a YAML file for a DaemonSet to run a Pod on every node.
5. **Document in `solution.md`:**  
   - Include the YAML files for the Namespace, Deployment, StatefulSet, and DaemonSet.
   - Explain the differences between these objects and when to use each.

> [!NOTE]
>
> **Interview Questions:**
>  - How does a Deployment ensure that the desired state of Pods is maintained in a cluster?
>  - Can you explain the differences between a Deployment, StatefulSet, and DaemonSet, and provide an example scenario for each?

---

## Task 3: Networking & Exposure – Create Services, Ingress, and Network Policies

**Scenario:**  
Expose your SpringBoot BankApp application to internal and external traffic by creating Services and configuring an Ingress, while using Network Policies to secure communication.

**Steps:**
1. **Create a Service:**  
   - Write a YAML file for a Service of type ClusterIP.
   - Modify the Service type to NodePort or LoadBalancer and apply the YAML.
2. **Configure an Ingress:**  
   - Create an Ingress resource to route external traffic to your application.
3. **Implement a Network Policy:**  
   - Write a YAML file for a Network Policy that restricts traffic to your application Pods.
4. **Document in `solution.md`:**  
   - Include the YAML files for your Service, Ingress, and Network Policy.
   - Explain the differences between Service types and the roles of Ingress and Network Policies.

> [!NOTE]
> 
> **Interview Questions:**
>  - How do NodePort and LoadBalancer Services differ in terms of exposure and use cases?
>  - What is the role of a Network Policy in Kubernetes, and can you describe a scenario where it is essential?

---

## Task 4: Storage Management – Use Persistent Volumes and Claims

**Scenario:**  
Deploy a component of the SpringBoot BankApp application that requires persistent storage by creating Persistent Volumes (PV), Persistent Volume Claims (PVC), and a StorageClass for dynamic provisioning.

**Steps:**
1. **Create a Persistent Volume and Claim:**  
   - Write YAML files for a static PV and a corresponding PVC.
2. **Deploy an Application Using the PVC:**  
   - Modify a Pod or Deployment YAML to mount the PVC.
3. **Document in `solution.md`:**  
   - Include your PV, PVC, and application YAML.
   - Explain how StorageClasses facilitate dynamic storage provisioning.

> [!NOTE]
>
>  **Interview Questions:**
>  - What are the main differences between a Persistent Volume and a Persistent Volume Claim?
>  - How does a StorageClass simplify storage management in Kubernetes?

---

## Task 5: Configuration & Secrets Management with ConfigMaps and Secrets

**Scenario:**  
Deploy a component of the SpringBoot BankApp application that consumes external configuration and sensitive data using ConfigMaps and Secrets.

**Steps:**
1. **Create a ConfigMap:**  
   - Write a YAML file for a ConfigMap containing configuration data.
2. **Create a Secret:**  
   - Write a YAML file for a Secret containing sensitive information.
3. **Deploy an Application:**  
   - Update your application YAML to mount the ConfigMap and Secret.
4. **Document in `solution.md`:**  
   - Include the YAML files and explain how the application uses these resources.

> [!NOTE]
> 
> **Interview Questions:**
>  - How would you update a running application if a ConfigMap or Secret is modified?
>  - What measures do you take to secure Secrets in Kubernetes?

---

## Task 6: Autoscaling & Resource Management

**Scenario:**  
Implement autoscaling for a component of the SpringBoot BankApp application using the Horizontal Pod Autoscaler (HPA). Optionally, explore Vertical Pod Autoscaling (VPA) and ensure the Metrics Server is running.

**Steps:**
1. **Deploy an Application with Resource Requests:**  
   - Deploy an application with defined resource requests and limits.
2. **Create an HPA Resource:**  
   - Write a YAML file for an HPA that scales the number of replicas based on CPU or memory usage.
3. **(Optional) Implement VPA & Metrics Server:**  
   - Optionally, deploy a VPA and verify that the Metrics Server is running.
4. **Document in `solution.md`:**  
   - Include the YAML files and explain how HPA (and optionally VPA) work.
   - Discuss the benefits of autoscaling in production.

> [!NOTE]
> 
> **Interview Questions:**
>  - What is the process by which the Horizontal Pod Autoscaler scales an application?
>  - In what scenarios would vertical scaling (VPA) be more beneficial than horizontal scaling (HPA)?

---

## Task 7: Security & Access Control

**Scenario:**  
Secure your Kubernetes cluster by implementing Role-Based Access Control (RBAC) and additional security measures.

### Part A: RBAC Implementation
**Steps:**
1. **Configure RBAC:**  
   - Create roles and role bindings using YAML files for specific user groups (e.g., Admin, Developer, Tester).
2. **Create Test Accounts:**  
   - Simulate real-world usage by creating user accounts for each role and verifying access.
3. **Optional Enhancement:**  
   - Simulate an unauthorized action (e.g., a Developer attempting to delete a critical resource) and document how RBAC prevents it.
   - Analyze RBAC logs (if available) to verify that unauthorized access attempts are recorded.
4. **Document in `solution.md`:**  
   - Include screenshots or logs of your RBAC configuration.
   - Describe the roles, permissions, and potential risks mitigated by proper RBAC implementation.

> [!NOTE] 
> 
> **Interview Questions:**
>  - How do RBAC policies help secure a multi-team Kubernetes environment?
>  - Can you provide an example of how improper RBAC could compromise a cluster?

### Part B: Additional Security Controls
**Steps:**
1. **Set Up Taints & Tolerations:**  
   - Apply taints to nodes and specify tolerations in your Pod specifications.
2. **Define a Pod Disruption Budget (PDB):**  
   - Write a YAML file for a PDB to ensure a minimum number of Pods remain available during maintenance.
3. **Document in `solution.md`:**  
   - Include the YAML files and explain how taints, tolerations, and PDBs contribute to cluster stability and security.

> [!NOTE]
> 
> **Interview Questions:**
>  - How do taints and tolerations ensure that critical workloads are isolated from interference?
>  - Why are Pod Disruption Budgets important for maintaining application availability?

---

## Task 8: Job Scheduling & Custom Resources

**Scenario:**  
Manage scheduled tasks and extend Kubernetes functionality by creating Jobs, CronJobs, and a Custom Resource Definition (CRD).

**Steps:**
1. **Create a Job and CronJob:**  
   - Write YAML files for a Job (a one-time task) and a CronJob (a scheduled task).
2. **Create a Custom Resource Definition (CRD):**  
   - Write a YAML file for a CRD and use `kubectl` to create a custom resource.
3. **Document in `solution.md`:**  
   - Include the YAML files and explain the use cases for Jobs, CronJobs, and CRDs.
   - Reflect on how CRDs extend Kubernetes capabilities.

> [!NOTE]
> 
> **Interview Questions:**
>  - What factors would influence your decision to use a CronJob versus a Job?
>  - How do CRDs enable custom extensions in Kubernetes?

---

## Task 9: Bonus Task: Advanced Deployment with Helm, Service Mesh, or EKS

**Scenario:**  
For an added challenge, deploy a component of the SpringBoot BankApp application using Helm, implement a basic Service Mesh (e.g., Istio), or deploy your cluster on AWS EKS.

**Steps:**
1. **Helm Deployment:**  
   - Create a Helm chart for your application.
   - Deploy the application using Helm and perform an update.
   - *OR*
2. **Service Mesh Implementation:**  
   - Deploy a basic Service Mesh (using Istio, Linkerd, or Consul) and demonstrate traffic management between services.
   - *OR*
3. **Deploy on AWS EKS:**  
   - Set up an EKS cluster and deploy your application there.
4. **Document in `solution.md`:**  
   - Include your Helm chart files, Service Mesh configuration, or EKS deployment details.
   - Explain the advantages of using Helm, a Service Mesh, or EKS in a production environment.

> [!NOTE]
> 
> **Interview Questions:**
>  - How does Helm simplify application deployments in Kubernetes?
>  - What are the benefits of using a Service Mesh in a microservices architecture?
>  - How does deploying on AWS EKS compare with managing your own Kubernetes cluster?
---

## Additional Resources

- **[Kubernetes Official Documentation](https://kubernetes.io/docs/)**
- **[Kubernetes Concepts](https://kubernetes.io/docs/concepts/)**
- **[Helm Documentation](https://helm.sh/docs/)**
- **[Istio Documentation](https://istio.io/latest/docs/)**
- **[Kubernetes RBAC](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)**
- **[Kubernetes Networking](https://kubernetes.io/docs/concepts/services-networking/)**
- **[Kubernetes Storage](https://kubernetes.io/docs/concepts/storage/)**
- **[Kubernetes Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)**
- **[Kubernetes Custom Resource Definitions](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)**

---
