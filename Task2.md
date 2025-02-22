## Task 2 :-
### Create a Dockerfile for a Sample Project

1. **Select or Create a Sample Application:**  
   - Choose a simple application (for example, a basic Node.js, Python, or Java app that prints “Hello, Docker!” or serves a simple web page).

2. **Write a Dockerfile:**  
   - Create a `Dockerfile` that defines how to build an image for your application.
   - Include comments in your Dockerfile explaining each instruction.
   - Build your image using:
     ```bash
     docker build -t <your-username>/sample-app:latest .

3. **Verify Your Build:**  
   - Run your container locally to ensure it works as expected:
     ```bash
     docker run -d -p 8080:80 <your-username>/sample-app:latest
     ```
   - Verify the container is running with:
     ```bash
     docker ps
     ```
   - Check logs using:
     ```bash
     docker logs <container_id>
     ```
    ---
   ## Solution :-
