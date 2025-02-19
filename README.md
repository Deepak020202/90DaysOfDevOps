# Week 4: Git and GitHub Challenge - Basic

## Challenge Tasks 

### Task 1: Fork and Clone the Repository
1. **Fork the Repository:**  
   - Visit [this repository](https://github.com/LondheShubham153/90DaysOfDevOps) and fork it to your own GitHub account. If not done yet.
  
2. **Clone Your Fork Locally:**  
   - Clone the forked repository using HTTPS:
     ```bash
     git clone <your-fork-url>
     ```
   - Change directory into the cloned repository:
     ```bash
     cd 2025/git/01_Git_and_Github_Basics
     ```

---

### Task 2: Initialize a Local Repository and Create a File
1. **Set Up Your Challenge Directory:**  
   - Inside the cloned repository, create a new directory for this challenge:
     ```bash
     mkdir week-4-challenge
     cd week-4-challenge
     ```

2. **Initialize a Git Repository:**  
   - Initialize the directory as a new Git repository:
     ```bash
     git init
     ```

3. **Create a File:**  
   - Create a file named `info.txt` and add some initial content (for example, your name and a brief introduction).

4. **Stage and Commit Your File:**  
   - Stage the file:
     ```bash
     git add info.txt
     ```
   - Commit the file with a descriptive message:
     ```bash
     git commit -m "Initial commit: Add info.txt with introductory content"
     ```

---

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

### Task 4: Explore Your Commit History
1. **View the Git Log:**  
   - Check your commit history using:
     ```bash
     git log
     ```
   - Take note of the commit hash and details as you will reference these in your documentation.

---

### Task 5: Advanced Branching and Switching
1. **Create a New Branch:**  
   - Create a branch called `feature-update`:
     ```bash
     git branch feature-update
     ```
  
2. **Switch to the New Branch:**  
   - Switch using `git switch`:
     ```bash
     git switch feature-update
     ```
   - Alternatively, you can use:
     ```bash
     git checkout feature-update
     ```

3. **Modify the File and Commit Changes:**  
   - Edit `info.txt` (for example, add more details or improvements).
   - Stage and commit your changes:
     ```bash
     git add info.txt
     git commit -m "Feature update: Enhance info.txt with additional details"
     git push origin feature-update
     ```
   - Merge this branch to `main` via a Pull Request on GitHub.
   
4. **(Advanced) Optional Extra Challenge:**  
   - If you feel confident, create another branch (e.g., `experimental`) from your main branch, make a conflicting change to `info.txt`, then switch back to `feature-update` and merge `experimental` to simulate a merge conflict. Resolve the conflict manually, then commit the resolution.  
   > *Note: This extra step is optional and intended for those looking for an additional challenge.*

---

### Task 6: Explain Branching Strategies
1. **Document Your Process:**  
   - Create (or update) a file named `solution.md` in your repository.
   - List all the Git commands you used in Tasks 1–4.
   - **Explain:** Write a brief explanation on **why branching strategies are important** in collaborative development. Consider addressing:
     - Isolating features and bug fixes
     - Facilitating parallel development
     - Reducing merge conflicts
     - Enabling effective code reviews

---

### Bonus Task: Explore SSH Authentication
1. **Generate an SSH Key (if not already set up):**
   - Create an SSH key pair:
     ```bash
     ssh-keygen
     ```
   - Follow the prompts and then locate your public key (typically found at `~/.ssh/id_ed25519.pub`).

2. **Add Your SSH Public Key to GitHub:**  
   - Copy the contents of your public key and add it to your GitHub account under **SSH and GPG keys**.  
     (See [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) for help.)

3. **Switch Your Remote URL to SSH:**  
   - Change the remote URL from HTTPS to SSH:
     ```bash
     git remote set-url origin git@github.com:<your-username>/90DaysOfDevOps.git
     ```

4. **Push Your Branch Using SSH:**  
   - Test the SSH connection by pushing your branch:
     ```bash
     git push origin feature-update
     ```

---



# Git & GitHub Advanced Challenge 

This challenge covers advanced Git concepts essential for real-world DevOps workflows. By the end of this challenge, you will:  

- Understand how to work with Pull Requests effectively.  
- Learn to undo changes using Reset & Revert.  
- Use Stashing to manage uncommitted work.  
- Apply Cherry-picking for selective commits.  
- Keep a clean commit history using Rebasing.  
- Learn industry-standard Branching Strategies.  

## **Topics Covered**  
1. Pull Requests – Collaborating in teams.  
2. Reset & Revert – Undo changes safely.  
3. Stashing – Saving work temporarily.  
4. Cherry-picking – Selecting specific commits.  
5. Rebasing – Maintaining a clean history.  
6. Branching Strategies – Industry best practices.  

## **Challenge Tasks**  

### **Task 7: Working with Pull Requests (PRs)**  
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

### **Task 8: Undoing Changes – Reset & Revert**  
**Scenario:** You accidentally committed incorrect changes and need to undo them.  

1. Create and modify a file.  
   ```bash
   echo "Wrong code" >> wrong.txt
   git add .
   git commit -m "Committed by mistake"
   ```  
2. Soft Reset (keeps changes staged).  
   ```bash
   git reset --soft HEAD~1
   ```  
3. Mixed Reset (unstages changes but keeps files).  
   ```bash
   git reset --mixed HEAD~1
   ```  
4. Hard Reset (removes all changes).  
   ```bash
   git reset --hard HEAD~1
   ```  
5. Revert a commit safely.  
   ```bash
   git revert HEAD
   ```  

**Document in `solution.md`**  
- Differences between `reset` and `revert`.  
- When to use each method.  

---

### **Task 9: Stashing - Save Work Without Committing**  
**Scenario:** You need to switch branches but don’t want to commit incomplete work.  

1. Modify a file without committing.  
   ```bash
   echo "Temporary Change" >> temp.txt
   git add temp.txt
   ```  
2. Stash the changes.  
   ```bash
   git stash
   ```  
3. Switch to another branch and apply the stash.  
   ```bash
   git checkout main
   git stash pop
   ```  

**Document in `solution.md`**  
- When to use `git stash`.  
- Difference between `git stash pop` and `git stash apply`.  

---

### **Task 4: Cherry-Picking - Selectively Apply Commits**  
**Scenario:** A bug fix exists in another branch, and you only want to apply that specific commit.  

1. Find the commit to cherry-pick.  
   ```bash
   git log --oneline
   ```  
2. Apply a specific commit to the current branch.  
   ```bash
   git cherry-pick <commit-hash>
   ```  
3. Resolve conflicts if any.  
   ```bash
   git cherry-pick --continue
   ```  

**Document in `solution.md`**  
- How cherry-picking is used in bug fixes.  
- Risks of cherry-picking.  

---

### **Task 10: Rebasing - Keeping a Clean Commit History**  
**Scenario:** Your branch is behind the main branch and needs to be updated without extra merge commits.  

1. Fetch the latest changes.  
   ```bash
   git fetch origin main
   ```  
2. Rebase the feature branch onto main.  
   ```bash
   git rebase origin/main
   ```  
3. Resolve conflicts and continue.  
   ```bash
   git rebase --continue
   ```  

**Document in `solution.md`**  
- Difference between `merge` and `rebase`.  
- Best practices for rebasing.  

---

### **Task 6: Branching Strategies Used in Companies**  
**Scenario:** Understand real-world branching strategies used in DevOps workflows.  

1. Research and explain Git workflows:  
   - Git Flow (Feature, Release, Hotfix branches).  
   - GitHub Flow (Main + Feature branches).  
   - Trunk-Based Development (Continuous Integration).  

2. Simulate a Git workflow using branches.  
   ```bash
   git branch feature-1
   git branch hotfix-1
   git checkout feature-1
   ```  

**Document in `solution.md`**  
- Which strategy is best for DevOps and CI/CD.  
- Pros and cons of different workflows.  

---
