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
   # Solution :-

 ### choosing a simple flask app and write docker file changes in app.py and then build docker image after that run docker image and container working 

 ### POC are here :-

   
 ![Dockerfile](https://github.com/user-attachments/assets/1c88ceb0-2f6c-41b3-a41e-2e317b37430f)
   
![image](https://github.com/user-attachments/assets/1972b258-dc49-4b7c-bea8-879056b5bf80) 

![image](https://github.com/user-attachments/assets/0229dc55-24e8-4842-9b6b-b9923563f684)

![image](https://github.com/user-attachments/assets/a369e8e0-449d-4141-afda-ed75ab065977)

![image](https://github.com/user-attachments/assets/4868aab3-6e98-4faa-a445-98ff86af3fb0)
