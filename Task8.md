## Task 8: Orchestrate with Docker Compose

1. **Create a docker-compose.yml File:**  
   - Write a `docker-compose.yml` file that defines at least two services (e.g., your sample app and a database).
   - Include definitions for services, networks, and volumes.
2. **Deploy Your Application:**  
   - Bring up your application using:
     ```bash
     docker-compose up -d
     ```
   - Test the setup, then shut it down using:
     ```bash
     docker-compose down
     ```
3. **Document the Process:**  
   - Explain each service and configuration in your `solution.md`.

---
## Solution :-

# 📄 Docker Compose File: Simplifying Multi-Container Applications

## 🔹 What is a Docker Compose File?
A **Docker Compose file** (`docker-compose.yml`) is a YAML configuration file used to **define and manage multiple containers** in a single application. Instead of running `docker run` multiple times, you can manage everything with a single command:

```sh
docker-compose up -d
```

## 📌 Key Features of a Docker Compose File
✔ Defines **services**, **networks**, and **volumes** 🛠️  
✔ Automates **multi-container deployment** 🚀  
✔ Uses YAML format (`.yml` or `.yaml`) 📄  
✔ Supports **scaling** and **dependency management** 🔗  
✔ Allows easy configuration via **environment variables** 🌍  

## 🔹 Basic Structure of a `docker-compose.yml` File
```yaml
version: "3.8"   # Specifies Docker Compose version

services:
  web:          # Service name (Container 1)
    image: nginx:latest  # Pulls Nginx image from Docker Hub
    ports:
      - "8080:80"   # Maps port 8080 on the host to port 80 in the container

  database:     # Service name (Container 2)
    image: mysql:5.7   # Pulls MySQL image
    environment:
      MYSQL_ROOT_PASSWORD: example   # Sets the MySQL root password
    volumes:
      - db_data:/var/lib/mysql   # Persists database data

volumes:
  db_data:   # Defines a named volume for persistent storage
```

## 📌 Key Sections in `docker-compose.yml`
| Section  | Description |
|----------|------------------------------------------------------------|
| **version**  | Specifies the Docker Compose format version. Example: `"3.8"` |
| **services** | Defines containers that make up the application. |
| **networks** | Enables inter-container communication (optional). |
| **volumes**  | Stores persistent data outside of containers. |

---
Would you like to add more details or examples? 🚀


---
## Poc :-

![image](https://github.com/user-attachments/assets/9291b4e5-4dcf-4257-a7ca-d46785ae2949)

![image](https://github.com/user-attachments/assets/1ddac6b0-ec61-4700-92b1-12e5965cbb20)

![image](https://github.com/user-attachments/assets/1a0841ea-64f0-4e58-9bca-cca93641f482)

![image](https://github.com/user-attachments/assets/6969810d-1662-4774-9625-73161b93738e)
