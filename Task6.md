## Task 6 :- 
### Persist Data with Docker Volumes
1. **Create a Docker Volume:**  
   - Create a Docker volume:
     ```bash
     docker volume create my_volume
     ```
2. **Run a Container with the Volume:**  
   - Run a container using the volume to persist data:
     ```bash
     docker run -d -v my_volume:/app/data <your-username>/sample-app:v1.0
     ```
3. **Document the Process:**  
   - In `solution.md`, explain how Docker volumes help with data persistence and why they are useful.

   ---
   ## Solution :-

## 📌 Docker Volumes: Ensuring Data Persistence

When using Docker containers, any data stored inside a container disappears once the container is removed. Docker volumes solve this problem by allowing persistent storage that remains even after a container stops or is deleted.

## 📖 What is a Docker Volume?

A Docker Volume is a storage mechanism that is managed by Docker and can be attached to one or more containers. Unlike bind mounts, Docker volumes are stored in Docker’s managed space rather than a host system directory.

## ✅ Key Features of Docker Volumes:

Data Persistence: Data is not deleted when the container stops or is removed.
Container Independence: Volumes can be shared across multiple containers.
Better Performance: Optimized by Docker for speed and efficiency.
Simplifies Backup & Recovery: Since volumes are managed by Docker, they can be easily backed up or migrated.

---

POC :-

![image](https://github.com/user-attachments/assets/b01ea912-d8bb-4391-b8ec-cc9127a34ca9)

![image](https://github.com/user-attachments/assets/46f26ca0-ad6f-457e-8063-5f2464ada018)

![image](https://github.com/user-attachments/assets/41ec3067-462b-4d9e-8d1e-248bf317b335)

![image](https://github.com/user-attachments/assets/0936d1c2-0f25-46df-9bb8-1d52589981bf)

---
