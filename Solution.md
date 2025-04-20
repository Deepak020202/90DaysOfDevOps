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

# Solution :-
1. **Study Kubernetes Architecture:**
## Answer:- 

![image](https://github.com/user-attachments/assets/4620ddc1-bb22-4b31-a383-9fd0fbebf10e)

## In Kubernetes architecture total 8 componentes also it is called k8's. In architecture two main component is Control plan and worker node
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

#  Q3.Describe the Kubernetes architecture components.
## Kubernetes architecture -

![image](https://github.com/user-attachments/assets/2c329532-6f46-441e-896b-a3f52d8e18d3)

## 1.Kubernetes Architecture Components

## Master Node (Control Plane)
- **API Server**: Manages cluster API and communication.
- **Scheduler**: Decides which node will run the pod.
- **Controller Manager**: Ensures the cluster is in the desired state.
- **etcd**: Stores cluster data and state.

## Worker Node
- **kubelet**: Ensures containers are running in pods.
- **kube-proxy**: Manages network routing and load balancing.
- **Container Runtime**: Runs containers (e.g., Docker).

## Kubernetes Resources
- **Pod**: The smallest unit in Kubernetes, representing one or more containers.
- **Service**: Exposes pods to other services or external traffic.
- **Deployment**: Manages pod replicas and rolling updates.
- **ReplicaSet**: Ensures the specified number of pod replicas are running.
- **StatefulSet**: Manages stateful applications with stable identities.
- **Namespace**: Organizes and isolates resources within the cluster.
- **ConfigMap & Secret**: Store non-sensitive and sensitive configuration data.
- **Ingress**: Manages external access to services, often HTTP/HTTPS.

## 2.Include your Pod YAML and explain each section.

```
apiVersion: v1                 //specifies that v1 of the Kubernetes API are using
kind: Pod                      //kind refer to the which component of kubernetes are running 

metadata:                       //data are used for run the container
  name: nginx-pod
  namespace: nginx-ns           //refer namespace

spec:
  containers:                   //details of the container inside the pod
    - name: nginx         
      image: nginx:latest
      ports:
        - containerPort: 80
```



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
![image](https://github.com/user-attachments/assets/ea2ea026-92ae-49d4-a2e5-10096e5d9da9)

2. **Deploy a Deployment:**  
   - Create a YAML file for a Deployment (within your Namespace) that manages a set of Pods running a component of SpringBoot BankApp.
   - Verify that a ReplicaSet is created automatically.

![image](https://github.com/user-attachments/assets/37c34d82-c6e3-47e6-ab72-94ac4e372050)

3. **Deploy a StatefulSet:**  
   - Write a YAML file for a StatefulSet (for example, for a database component) and apply it.

![image](https://github.com/user-attachments/assets/0ed68e65-a242-4a79-b189-eba640a8cfa5)


4. **Deploy a DaemonSet:**  
   - Create a YAML file for a DaemonSet to run a Pod on every node.

![image](https://github.com/user-attachments/assets/0812df83-bc83-4073-9993-0e2766d84498)

5. **Document in `solution.md`:**  
   - Include the YAML files for the Namespace, Deployment, StatefulSet, and DaemonSet.
   - Explain the differences between these objects and when to use each.
   - 
**1. namspace.yml**

```
apiVersion: v1
kind: Namespace
metadata:
  name: bankapp-ns
```

**2. deployment.yml**

```
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: bankapp-deploy
  name: bankapp-deploy
  namespace: bankapp-ns
spec:
  replicas: 1
  selector:
    matchLabels:
      app: bankapp-deploy
  template:
    metadata:
      labels:
        app: bankapp-deploy
    spec:
      containers:
      - name: bankapp
        image: deepak0202/bank-app:latest
        ports:
        - containerPort: 8080
```
**3. StatefulSet**

```
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: mysql
  namespace: bankapp-ns
  labels:
    app: mysql
spec:
  serviceName: "mysql"  # Required for stable network IDs
  replicas: 1
  selector:
    matchLabels:
      app: mysql
  template:
    metadata:
      labels:
        app: mysql
    spec:
      containers:
      - name: mysql
        image: mysql:8.0
        ports:
        - containerPort: 3306
        env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-secret
              key: MYSQL_ROOT_PASSWORD
        - name: MYSQL_DATABASE
          valueFrom:
            configMapKeyRef:
              name: bankapp-config
              key: MYSQL_DATABASE

```
**4. Daemon-set.yml**
```
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: bankapp-daemonset
  namespace: bankapp-ns
spec:
  selector:
    matchLabels:
      app: bankapp
  template:
    metadata:
      labels:
        app: bankapp
    spec:
      containers:
      - name: bankapp
        image: deepak0202/bank-app:latest
        ports:
        - containerPort: 8080

```

## Namespace
A **Namespace** is used to logically group and isolate Kubernetes resources within a cluster.  
It helps in organizing environments (like `dev`, `test`, `prod`) or teams by separating their workloads.


## Deployment
A **Deployment** manages **stateless applications**.  
It ensures the desired number of identical Pods are running and handles updates, rollbacks, and scaling easily.

## StatefulSet
A **StatefulSet** is for **stateful applications**.  
It provides stable network identities and persistent storage to each Pod.  
Useful when each instance needs to be uniquely identified and data must persist across restarts.

## DaemonSet
A **DaemonSet** ensures that a **single Pod runs on every node** (or selected nodes) in the cluster.  
Ideal for background tasks or node-specific operations like monitoring and logging.


---

## Task 3: Networking & Exposure – Create Services, Ingress, and Network Policies

**Scenario:**  
Expose your SpringBoot BankApp application to internal and external traffic by creating Services and configuring an Ingress, while using Network Policies to secure communication.

**Steps:**
1. **Create a Service:**  
   - Write a YAML file for a Service of type ClusterIP.
   - Modify the Service type to NodePort or LoadBalancer and apply the YAML.

![image](https://github.com/user-attachments/assets/a5bfdecc-d75a-47e2-b4fe-cdbbe951a9d3)


2. **Configure an Ingress:**  
   - Create an Ingress resource to route external traffic to your application.
  
![image](https://github.com/user-attachments/assets/726c1315-8b47-4809-a171-22ef3d478ede)

3. **Implement a Network Policy:**  
   - Write a YAML file for a Network Policy that restricts traffic to your application Pods.

![image](https://github.com/user-attachments/assets/f617c332-8abd-4535-8902-6c61c651ec24)


4. **Document in `solution.md`:**  
   - Include the YAML files for your Service, Ingress, and Network Policy.
   - Explain the differences between Service types and the roles of Ingress and Network Policies.
**service.yml**
```
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: bankapp-deploy
  name: bankapp-deploy
  namespace: bankapp-ns
spec:
  replicas: 1
  selector:
    matchLabels:
      app: bankapp-deploy
  template:
    metadata:
      labels:
        app: bankapp-deploy
    spec:
      containers:
      - name: bankapp
        image: deepak0202/bank-app:latest
        ports:
        - containerPort: 8080
```
**ingress.yml**
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: bankapp-ingress
  namespace: bankapp-ns
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /$1
spec:
  ingressClassName: nginx
  rules:
  - host: 13.234.120.34.nip.io
    http:
      paths:
      - path: /?(.*)
        pathType: Prefix
        backend:
          service:
            name: bankapp-service
            port:
              number: 8080
      - path: /nginx/?(.*)
        pathType: Prefix
        backend:
          service:
            name: nginx-service
            port:
              number: 80
```
**networkpolicy.yml**
```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: bankapp-restricted-traffic
  namespace: bankapp-ns
spec:
  podSelector:
    matchLabels:
      app: bankapp-deploy
  ingress:
  - from:
    - podSelector:
        matchLabels:
          app: bankapp-deploy
    - namespaceSelector:
        matchLabels:
          name: bankapp-ns
  egress:
  - to:
    - podSelector:
        matchLabels:
          app: mysql
    - namespaceSelector:
        matchLabels:
          name: bankapp-ns
  policyTypes:
  - Ingress
  - Egress
```
---

## Task 4: Storage Management – Use Persistent Volumes and Claims

**Scenario:**  
Deploy a component of the SpringBoot BankApp application that requires persistent storage by creating Persistent Volumes (PV), Persistent Volume Claims (PVC), and a StorageClass for dynamic provisioning.

**Steps:**
1. **Create a Persistent Volume and Claim:**  
   - Write YAML files for a static PV and a corresponding PVC.

![image](https://github.com/user-attachments/assets/e36d17a7-1db2-4d98-872f-1915280e4f54)


2. **Deploy an Application Using the PVC:**  
   - Modify a Pod or Deployment YAML to mount the PVC.

![image](https://github.com/user-attachments/assets/653e956f-07a5-4869-a70c-b2ecfd3a717b)


3. **Document in `solution.md`:**  
   - Include your PV, PVC, and application YAML.
   - Explain how StorageClasses facilitate dynamic storage provisioning.

**persistance-volume-claime**
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv
  namespace: bankapp-ns
spec:
  capacity:
    storage: 10Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain  # Keeps the PV after the PVC is deleted
  storageClassName: standard  # Make sure this matches your cluster's default storage class
  hostPath:
    path: /mnt/data/mysql
    type: DirectoryOrCreate
```
**persistance-volume-claime**

```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pvc
  namespace: bankapp-ns
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
  storageClassName: standard
```
##  Explain how StorageClasses facilitate dynamic storage provisioning.
### When a user creates a PersistentVolumeClaim (PVC) and specifies a storageClassName, Kubernetes automatically provisions a PersistentVolume (PV) based on the configuration defined in the StorageClass.

### ✅ Without StorageClass (Static):
1.You manually create PVs.

2.PVCs bind only if they match size, access mode, and storage class.

3.Time-consuming and error-prone.

### ✅ With StorageClass (Dynamic):

1.PVCs automatically trigger PV creation.

2.Saves time and ensures consistency.

3.Useful for dynamic and on-demand workloads.

---

## Task 5: Configuration & Secrets Management with ConfigMaps and Secrets

**Scenario:**  
Deploy a component of the SpringBoot BankApp application that consumes external configuration and sensitive data using ConfigMaps and Secrets.

**Steps:**
1. **Create a ConfigMap:**  
   - Write a YAML file for a ConfigMap containing configuration data.

![image](https://github.com/user-attachments/assets/fcc38d4f-89a8-4459-9946-1852c0dfc350)

2. **Create a Secret:**  
   - Write a YAML file for a Secret containing sensitive information.

![image](https://github.com/user-attachments/assets/c1d534ac-6947-40b4-bbad-d6cd74bc5ff5)

3. **Deploy an Application:**  
   - Update your application YAML to mount the ConfigMap and Secret.

![image](https://github.com/user-attachments/assets/1f6f95b9-75e3-47d6-bd1e-f25c9590c28e)


4. **Document in `solution.md`:**  
   - Include the YAML files and explain how the application uses these resources.
   
**configmap.yaml**
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: bankapp-config
  namespace: bankapp-ns
data:
  MYSQL_DATABASE: BankDB
  SPRING_DATASOURCE_URL: jdbc:mysql://mysql-svc.bankapp-ns.svc.cluster.local:3306/BankDB?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
  SPRING_DATASOURCE_USERNAME: root
```
**secretes.yml**
```
ubuntu@ip-172-31-44-158:~/Springboot-BankApp/kubernetes$ cat secrets.yaml
apiVersion: v1
kind: Secret
metadata:
  name: mysql-secret
  namespace: bankapp-ns
type: Opaque
data:
  MYSQL_ROOT_PASSWORD: VGVzdEAxMjM=
  SPRING_DATASOURCE_PASSWORD: VGVzdEAxMjM=
```
## How  Application Uses These Resources
**Once the Deployment injects the ConfigMap and Secret as environment variables into your container, your application automatically picks them up at runtime, just like normal environment variables.**

---

## Task 6: Autoscaling & Resource Management

**Scenario:**  
Implement autoscaling for a component of the SpringBoot BankApp application using the Horizontal Pod Autoscaler (HPA). Optionally, explore Vertical Pod Autoscaling (VPA) and ensure the Metrics Server is running.

**Steps:**
1. **Deploy an Application with Resource Requests:**  
   - Deploy an application with defined resource requests and limits.

![image](https://github.com/user-attachments/assets/2dc6213f-bf4c-4817-a465-6f2d06093ed5) 

2. **Create an HPA Resource:**  
   - Write a YAML file for an HPA that scales the number of replicas based on CPU or memory usage.

![image](https://github.com/user-attachments/assets/7615ae70-e39e-4be1-9ffd-67ff60321a6d)

3. **(Optional) Implement VPA & Metrics Server:**  
   - Optionally, deploy a VPA and verify that the Metrics Server is running.

   ![image](https://github.com/user-attachments/assets/7ee5eac5-6aaa-46d9-9f9c-1aefe0077f00)
   

4. **Document in `solution.md`:**  
   - Include the YAML files and explain how HPA (and optionally VPA) work.
   - Discuss the benefits of autoscaling in production.
  
   **hpa.yml**
   
```
   apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: bankapp-hpa
  namespace: bankapp-ns
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: bankapp-deploy
  minReplicas: 1
  maxReplicas: 5
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 30
 ```

**vpa.yml**
```
apiVersion: autoscaling.k8s.io/v1
kind: VerticalPodAutoscaler
metadata:
  name: mysql-vpa
  namespace: bankapp-ns
spec:
  targetRef:
    apiVersion: "apps/v1"
    kind: Deployment
    name: mysql
  updatePolicy:
    updateMode: "Auto"
  resourcePolicy:
    containerPolicies:
      - containerName: "*"
        minAllowed:
          cpu: 100m
          memory: 128Mi
        maxAllowed:
          cpu: 1
          memory: 1Gi
```
# Benefits of Autoscaling in Kubernetes

## 1. Improved Application Performance

**Benefit:**  
Handles increased load automatically to keep your app fast and responsive.

**Example:**  
Imagine you run an e-commerce app. During a flash sale, thousands of users visit at once. Kubernetes Horizontal Pod Autoscaler (HPA) automatically scales from 2 to 10 pods to handle the traffic smoothly without slowing down the site.

## 2. Cost Efficiency

**Benefit:**  
Saves money by scaling down unused resources during low demand.

**Example:**  
Your blog app gets less traffic at night. Kubernetes scales down the number of pods from 5 to 1, freeing up resources and reducing cloud costs.

## 3. High Availability

**Benefit:**  
Keeps your services running even when traffic unexpectedly spikes.

**Example:**  
A news site gets featured on a trending platform. Kubernetes auto-scales to maintain availability without crashing, ensuring all readers can access it.

## 4. Smart Resource Optimization

**Benefit:**  
Right-sizes CPU and memory based on actual usage.

**Example:**  
Using Vertical Pod Autoscaler (VPA), Kubernetes notices your MySQL pod consistently uses more memory than requested. It automatically increases the memory limit to prevent crashes.

---

## Task 7: Security & Access Control

**Scenario:**  
Secure your Kubernetes cluster by implementing Role-Based Access Control (RBAC) and additional security measures.

### Part A: RBAC Implementation
**Steps:**
1. **Configure RBAC:**  
   - Create roles and role bindings using YAML files for specific user groups (e.g., Admin, Developer, Tester).

![image](https://github.com/user-attachments/assets/fb0cf503-2bcf-4a78-9063-beb2a4e981fe)

2. **Create Test Accounts:**  
   - Simulate real-world usage by creating user accounts for each role and verifying access.
## admin can only delete pod 

![image](https://github.com/user-attachments/assets/fa3b4cd3-caa7-4bb2-b472-caf89df49f21)

3. **Optional Enhancement:**  
   - Simulate an unauthorized action (e.g., a Developer attempting to delete a critical resource) and document how RBAC prevents it.
   - 
![image](https://github.com/user-attachments/assets/89a87cda-f5cd-4104-90e5-571369de55ab)

4. **Document in `solution.md`:**  
   - Include screenshots or logs of your RBAC configuration.
   - Describe the roles, permissions, and potential risks mitigated by proper RBAC implementation.

## RBAC (Role-Based Access Control) is a security method in Kubernetes used to control who can do what in the cluster. It works by creating roles that define what actions are allowed, and then assigning those roles to users or groups using bindings.

## How it Works (With Example)

An Admin can have full access to manage everything in a namespace (create, delete, update pods, deployments, etc.).

A Developer might have permission to create and update deployments or pods, but not delete secrets or change security settings.

A Tester might only be allowed to view logs or see the status of the app, but not change anything.

This way, each team member gets only the access they need to do their job—nothing more, nothing less.

## Benefits of RBAC

- Improved security by limiting access based on roles
- Easier auditing and compliance tracking
- Prevents accidental or unauthorized changes

> [!NOTE] 
> 
> **Interview Questions:**
>  - How do RBAC policies help secure a multi-team Kubernetes environment?
>  - Can you provide an example of how improper RBAC could compromise a cluster?

### Part B: Additional Security Controls
**Steps:**
1. **Set Up Taints & Tolerations:**  
   - Apply taints to nodes and specify tolerations in your Pod specifications.

### When i apply taint to worker-node-1 all then all the pods only ran on other worker node
![image](https://github.com/user-attachments/assets/dfcf0633-9a6d-4fb3-81ba-c6d0a8e2efc4)


2. **Define a Pod Disruption Budget (PDB):**  
   - Write a YAML file for a PDB to ensure a minimum number of Pods remain available during maintenance.
```
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: bankapp-pdb
  namespace: bankapp-ns
spec:
  minAvailable: 2
  selector:
    matchLabels:
      app: bankapp
```
3. **Document in `solution.md`:**  
   - Include the YAML files and explain how taints, tolerations, and PDBs contribute to cluster stability and security.
## Kubernetes: Taints, Tolerations & Pod Disruption Budgets (PDBs)

### 1. Taints
**What they do:** Prevent pods from being scheduled on certain nodes.

**Purpose:** Mark a node as special or restricted — such as nodes reserved for critical workloads or those requiring high memory or GPU.

### 2. Tolerations
**What they do:** Allow specific pods to run on tainted nodes.

**Purpose:** Provide exceptions for selected pods to access special or restricted nodes.

### 3. Pod Disruption Budgets (PDBs)
**What they do:** Ensure a minimum number of pods are always running during voluntary disruptions (e.g., node upgrades or drains).

**Purpose:** Maintain application availability and prevent total outages during cluster maintenance.

### How They Improve Cluster Stability & Security
Taints and tolerations work together to maintain cluster stability by controlling where pods can run—ensuring only critical or trusted workloads use special nodes, preventing overload. They also enhance security by isolating sensitive applications from general workloads. Pod Disruption Budgets (PDBs) add stability by ensuring key services stay available during maintenance or updates, reducing downtime risks.

---

## Task 8: Job Scheduling & Custom Resources

**Scenario:**  
Manage scheduled tasks and extend Kubernetes functionality by creating Jobs, CronJobs, and a Custom Resource Definition (CRD).

**Steps:**
1. **Create a Job and CronJob:**  
   - Write YAML files for a Job (a one-time task) and a CronJob (a scheduled task).
   **Onetime-job**

![image](https://github.com/user-attachments/assets/aaaa89a6-54b5-4ba2-8749-d7cac0b20869)

   **cron-job**
### generate a new job after 1 minute 

![image](https://github.com/user-attachments/assets/413b1d2d-ace7-483c-9358-174b160fd206)

   
2. **Create a Custom Resource Definition (CRD):**  
   - Write a YAML file for a CRD and use `kubectl` to create a custom resource.

![image](https://github.com/user-attachments/assets/6e8f3c6b-3e89-4703-81fc-434276666a4e)

4. **Document in `solution.md`:**  
   - Include the YAML files and explain the use cases for Jobs, CronJobs, and CRDs.
   - Reflect on how CRDs extend Kubernetes capabilities.

**job.yml**
```
apiVersion: batch/v1
kind: Job
metadata:
  name: hello-job
  namespace: bankapp-ns
spec:
  template:
    spec:
      containers:
      - name: hello
        image: busybox
        command: ["echo", "Hello this is one-time job"]
      restartPolicy: Never
```
**cron-job.yml**
```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello-cron
  namespace: bankapp-ns
spec:
  schedule: "*/1 * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox
            command: ["echo", "Hello this is cron-job CronJob"]
          restartPolicy: OnFailure
```
**crd.yml**
```
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  name: copytasks.copy.example.com
spec:
  group: copy.example.com
  versions:
    - name: v1
      served: true
      storage: true
      schema:
        openAPIV3Schema:
          type: object
          properties:
            spec:
              type: object
              properties:
                source:
                  type: string
                  description: "The source location from which files should be copied"
                destination:
                  type: string
                  description: "The destination location where files should be copied"
                filePattern:
                  type: string
                  description: "Pattern to match files for copying (e.g., *.txt)"
                schedule:
                  type: string
                  description: "Optional cron schedule for periodic copying task"
  scope: Namespaced
  names:
    plural: copytasks
    singular: copytask
    kind: CopyTask
    shortNames:
    - ct
```
### 1. Jobs
- **Use Case:** Running database migrations or backup tasks
- **Example:** A job to back up a database at a specific time

### 2. CronJobs
- **Use Case:** Periodic backups, scheduled report generation, or cleanup tasks
- **Example:** A CronJob to back up the database every night at midnight

### 3. Custom Resource Definitions (CRDs)
- **Use Case:** Defining custom workflows, monitoring systems, or managing business-specific resources
- **Example:** A custom OrderProcessing CRD to handle orders in an e-commerce system

### How CRDs Extend Kubernetes
CRDs allow you to define custom resources that extend Kubernetes' native capabilities, enabling the management of specialized workloads beyond the standard containers. By using CRDs, you can create custom resources like `OrderProcessing` that integrate directly into Kubernetes, making it more versatile for specific application needs

---

## Task 9: Bonus Task: Advanced Deployment with Helm, Service Mesh, or EKS

**Scenario:**  
For an added challenge, deploy a component of the SpringBoot BankApp application using Helm, implement a basic Service Mesh (e.g., Istio), or deploy your cluster on AWS EKS.

**Steps:**
1. **Helm Deployment:**  
   - Create a Helm chart for your application.
   - Deploy the application using Helm and perform an update.
  
![image](https://github.com/user-attachments/assets/c364c4d1-a789-4614-a184-0011a74c2487)

![image](https://github.com/user-attachments/assets/a2458345-5b13-424a-840f-613d39ec2240)


   - *OR*
2. **Service Mesh Implementation:**  
   - Deploy a basic Service Mesh (using Istio, Linkerd, or Consul) and demonstrate traffic management between services.
   - *OR*

![image](https://github.com/user-attachments/assets/22cdfe43-1424-4eef-85b9-633aaca4979f)

3. **Deploy on AWS EKS:**  
   - Set up an EKS cluster and deploy your application there.
4. **Document in `solution.md`:**  
   - Include your Helm chart files, Service Mesh configuration, or EKS deployment details.
   - Explain the advantages of using Helm, a Service Mesh, or EKS in a production environment.
   
## Helm – Kubernetes Package Manager
Helm helps you manage Kubernetes applications with versioned, reusable charts.

- Simplifies Deployments: One command can deploy complex apps with all their dependencies.
- Configuration Management: Easily override values for different environments (dev/staging/prod).
- Reusable Templates: Helm charts standardize deployments across teams.
- Rollback Support: Quickly revert to a previous stable version on failure.

---

## Service Mesh (e.g., Istio, Linkerd) – Advanced Traffic Control & Observability

- Security: Built-in mutual TLS encryption between services.
- Observability: Monitor service communication with metrics, tracing, and logging.
- Traffic Management: Fine-grained control like canary deployments, traffic shifting, retries, and timeouts.
- Resilience: Automatic failover, circuit breaking, and load balancing between services.

---

## Amazon EKS (Elastic Kubernetes Service) – Managed Kubernetes on AWS

- Fully Managed Control Plane: No need to handle Kubernetes upgrades, security patches, or scaling the control plane.
- Integrated Security: Works with IAM, VPC, and AWS Secrets Manager for secure access and networking.
- Auto Scaling & Load Balancing: Native support for Cluster Autoscaler and AWS Load Balancers.
- Production-Ready: High availability, SLA-backed, and integrated with AWS services (CloudWatch, RDS, S3, etc.).

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
