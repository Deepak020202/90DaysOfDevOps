## Task 4: 
### Optimize Your Docker Image with Multi-Stage Builds

1. **Implement a Multi-Stage Docker Build:**  
   - Modify your existing `Dockerfile` to include multi-stage builds.  
   - Aim to produce a lightweight, **distroless** (or minimal) final image.
2. **Compare Image Sizes:**  
   - Build your image before and after the multi-stage build modification and compare their sizes using:
     ```bash
     docker images
     ```
3. **Document the Differences:**  
   - Explain in `solution.md` the benefits of multi-stage builds and the impact on image size.

---
## Solution :-

# 📌 Multi-Stage Builds in Docker

Multi-stage builds allow you to use **multiple `FROM` statements** in a single `Dockerfile`. Each stage can have its own base image and tools, helping to **reduce the final image size** and keep only necessary files in production.

## 🚀 Benefits of Multi-Stage Builds

1. **Reduces Image Size** 🏋️‍♂️  
   - Only the required files are copied to the final image, making it **lightweight**.  
   - No need to keep unnecessary build tools, compilers, or dependencies in production.

2. **Improves Security** 🔒  
   - Since extra tools and dependencies are removed, the attack surface is **minimized**.  
   - Keeps the final image **clean and production-ready**.

3. **Optimizes Build Performance** ⚡  
   - Build stages are **cached**, leading to **faster rebuilds**.  
   - Rebuilding only the necessary layers **saves time**.

4. **Better Organization** 🏗  
   - Separates **build environment** (e.g., compilers) from **runtime environment**.  
   - Improves maintainability and debugging.

---
## POC :- 

![image](https://github.com/user-attachments/assets/d71f37ff-b363-497f-9d16-d648329faa9c)

![image](https://github.com/user-attachments/assets/0f21a940-8150-4018-a91c-7737190c239c)

![image](https://github.com/user-attachments/assets/afdfeecc-f8cf-4a84-a92b-6223dd4c1a2c)

![image](https://github.com/user-attachments/assets/bc54e691-38cc-42e6-8325-520ccb7c2942)

![image](https://github.com/user-attachments/assets/d381a5fb-a6d6-46dc-b108-90d799de1d7e)

![image](https://github.com/user-attachments/assets/dad6fe20-1e7a-46c0-88c5-0e34ff398a1d)

