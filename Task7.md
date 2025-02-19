## **Task 7: Working with Pull Requests (PRs)**  
**Scenario:** You are working on a new feature and need to merge your changes into the main branch using a Pull Request.  

1. Fork a repository and clone it locally.  
   ```bash
   git clone <your-forked-repo-url>
   cd <repo-name>
   ```  
2. Create a feature branch and make changes.  
   ```bash
   git checkout -b feature-branch
   echo "New Feature" >> feature.txt
   git add .
   git commit -m "Added a new feature"
   ```  
3. Push the changes and create a Pull Request.  
   ```bash
   git push origin feature-branch
   ```  
4. Open a PR on GitHub, request a review, and merge it once approved.  

**Document in `solution.md`**  
- Steps to create a PR.  
- Best practices for writing PR descriptions.  
- Handling review comments.  

---
## Solution :-
