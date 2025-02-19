## Task 3: Configure Remote URL with PAT and Push/Pull

1. **Configure Remote URL with Your PAT:**  
   To avoid entering your Personal Access Token (PAT) every time you push or pull, update your remote URL to include your credentials.  

   **⚠️ Note:** Embedding your PAT in the URL is only for this exercise. It is not recommended for production use.  
   
   Replace `<your-username>`, `<your-PAT>`, and `<repository-name>` with your actual GitHub username, your PAT, and the repository name respectively:
   
   ```bash
   git remote add origin https://<your-username>:<your-PAT>@github.com/<your-username>/90DaysOfDevOps.git
   ```
   If a remote named `origin` already exists, update it with:
   ```bash
   git remote set-url origin https://<your-username>:<your-PAT>@github.com/<your-username>/90DaysOfDevOps.git
   ```
2. **Push Your Commit to Remote:**  
   - Push your current branch (typically `main`) and set the upstream:
     ```bash
     git push -u origin main
     ```
3. **(Optional) Pull Remote Changes:**  
   - Verify your configuration by pulling changes:
     ```bash
     git pull origin main
     ```

---

## Solution
