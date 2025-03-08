## Task 3 :- 
###Explore Docker Terminologies and Components
1. **Document Key Terminologies:**  
   - In your `solution.md`, list and briefly describe key Docker terms such as image, container, Dockerfile, volume, and network.
   - Explain the main Docker components (Docker Engine, Docker Hub, etc.) and how they interact.

---
## Solution :-
## What is Docker?
Docker is a platform that allows developers to package applications into containers. Containers are lightweight, portable, and ensure that the application runs the same way regardless of the environment.

---

## Key Docker Terms

### 1. **Image**
An image is a lightweight, standalone package that contains everything needed to run a piece of software, including the code, runtime, dependencies, and system tools.
- Example: The official Python image can be pulled using:
  ```sh
  docker pull python:3.9
  ```

### 2. **Container**
A container is a running instance of an image. It is isolated and runs the application as defined in the image.
- Example: Running a Python container interactively:
  ```sh
  docker run -it python:3.9
  ```

### 3. **Dockerfile**
A Dockerfile is a script containing a set of instructions for building a Docker image.
- Example Dockerfile:
  ```Dockerfile
  FROM python:3.9
  WORKDIR /app
  COPY . .
  RUN pip install -r requirements.txt
  CMD ["python", "app.py"]
  ```

### 4. **Volume**
A volume is used to persist data outside the container’s filesystem so that data is not lost when a container stops.
- Example: Create and use a volume:
  ```sh
  docker volume create mydata
  docker run -v mydata:/app/data python:3.9
  ```

### 5. **Network**
Docker networks allow containers to communicate with each other.
- Example: Creating a network and running containers in it:
  ```sh
  docker network create mynetwork
  docker run --network=mynetwork mycontainer
  ```

---

## Main Docker Components

### 1. **Docker Engine**
The core of Docker, responsible for building, running, and managing containers.

### 2. **Docker Hub**
A cloud-based repository for storing and sharing Docker images.
- Example: Pulling an image from Docker Hub:
  ```sh
  docker pull nginx
  ```

### 3. **Docker CLI**
The command-line interface for interacting with Docker.

### 4. **Docker Compose**
A tool for defining and managing multi-container applications.
- Example `docker-compose.yml` file:
  ```yaml
  version: '3'
  services:
    web:
      image: nginx
      ports:
        - "80:80"
  ```

---
