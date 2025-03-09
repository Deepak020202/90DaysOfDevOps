### Task 7: Configure Docker Networking
1. **Create a Custom Docker Network:**  
   - Create a custom Docker network:
     ```bash
     docker network create my_network
     ```
2. **Run Containers on the Same Network:**  
   - Run two containers (e.g., your sample app and a simple database like MySQL) on the same network to demonstrate inter-container communication:
     ```bash
     docker run -d --name sample-app --network my_network <your-username>/sample-app:v1.0
     docker run -d --name my-db --network my_network -e MYSQL_ROOT_PASSWORD=root mysql:latest
     ```
3. **Document the Process:**  
   - In `solution.md`, describe how Docker networking enables container communication and its significance in multi-container applications.

---

## Solution :- 

# 📡 Docker Networking: Enabling Container Communication

## 📖 What is Docker Networking?
Docker networking allows **containers** to communicate with each other **securely** and **efficiently**. It enables **inter-container communication** and helps applications **scale** in a microservices environment.

### ✅ Key Benefits of Docker Networking:
- **Container-to-Container Communication** 🏗️  
- **Isolated & Secure Networks** 🔒  
- **Integration with Host & External Networks** 🌎  
- **Scalability for Microservices** 🚀  

---
## developing mongoDB server using mongoDB-express within one network 

### POC :- 

![image](https://github.com/user-attachments/assets/3f327bb7-0e6f-40d4-b4d9-b5b7628a87eb)

![image](https://github.com/user-attachments/assets/82dbb1f1-4ae3-4379-9f1d-dece14fb29ae)

![image](https://github.com/user-attachments/assets/3bdd5a8b-768a-45ef-b791-40bb34a741bc)

![image](https://github.com/user-attachments/assets/cf165b4c-89a5-4e92-a81e-d4f8155a8a24)

![image](https://github.com/user-attachments/assets/5b0c3c61-36fb-47f3-8283-72e6525da35a)
 
![image](https://github.com/user-attachments/assets/a445977f-ffa9-4335-b935-c1086d1b7ce4)
 
![image](https://github.com/user-attachments/assets/69b24b3a-909d-4c7d-a0d4-3bb161c9e336)
 
![image](https://github.com/user-attachments/assets/933dc981-e2fa-4421-a35b-791af99750f4)
 
![image](https://github.com/user-attachments/assets/1b97b1a7-d8ca-4e17-ad73-c12c7bc10ff5)
 
![image](https://github.com/user-attachments/assets/01c177b6-d748-45f1-8f21-6454dd477ad9)

![image](https://github.com/user-attachments/assets/6b439a32-05c1-4b6f-9a59-f770161da4e8)
 
![image](https://github.com/user-attachments/assets/d3410498-94b2-4f3c-8716-22aebe0b117d)
 


 
 
 
 

 
 


