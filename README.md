# Task 1: Fork and Clone the Repository
1. **Fork the Repository:**  
   - Visit [this repository](https://github.com/LondheShubham153/90DaysOfDevOps) and fork it to your own GitHub account. If not done yet.


  
2. **Clone Your Fork Locally:**  
   - Clone the forked repository using HTTPS:
     ```bash
     git clone <your-fork-url>
     ```

![image](https://github.com/user-attachments/assets/78cb1886-dbdc-4b04-937e-74c2e187706c)


   - Change directory into the cloned repository:
     ```bash
     cd 2025/git/01_Git_and_Github_Basics
     ```
  ```
 git clone git clone https://github.com/Deepak020202/90DaysOfDevOps-Demo.gitCloning into '90DaysOfDevOps-Demo'... 
   cd 2025/git/01_Git_and_Github_Basic
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


![image](https://github.com/user-attachments/assets/a221c0ae-f0a7-4a47-92b0-bfaa2e71d145)

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

![image](https://github.com/user-attachments/assets/b012e603-4272-4bba-af7c-a8a784133cb9)

---
## Task 4: Explore Your Commit History
1. **View the Git Log:**  
   - Check your commit history using:
     ```bash
     git log
     ```
   - Take note of the commit hash and details as you will reference these in your documentation.


![image](https://github.com/user-attachments/assets/e0b94895-c174-4270-af7f-8c5af27ed38c)


---
## Task 5: Advanced Branching and Switching
1. **Create a New Branch:**  
   - Create a branch called `feature-update`:
     ```bash
     git branch feature-update
     ```

![image](https://github.com/user-attachments/assets/a0b73808-a74f-40c5-8178-fc8140db3b63)
  
2. **Switch to the New Branch:**  
   - Switch using `git switch`:
     ```bash
     git switch feature-update
     ```
   - Alternatively, you can use:
     ```bash
     git checkout feature-update
     ```

![image](https://github.com/user-attachments/assets/65c67180-a115-4e33-9763-e873d070e4f4)


3. **Modify the File and Commit Changes:**  
   - Edit `info.txt` (for example, add more details or improvements).
   - Stage and commit your changes:
     ```bash
     git add info.txt
     git commit -m "Feature update: Enhance info.txt with additional details"
     git push origin feature-update
     ```
   - Merge this branch to `main` via a Pull Request on GitHub.


![image](https://github.com/user-attachments/assets/053c5dbb-46c2-45bd-aa41-aebee071ef34)
   
4. **(Advanced) Optional Extra Challenge:**  
   - If you feel confident, create another branch (e.g., `experimental`) from your main branch, make a conflicting change to `info.txt`, then switch back to `feature-update` and merge `experimental` to simulate a merge conflict. Resolve the conflict manually, then commit the resolution.  
   > *Note: This extra step is optional and intended for those looking for an additional challenge.*


![image](https://github.com/user-attachments/assets/13143aa7-aa39-48c9-9940-71024b75a7f1)

---

## Task 6: Explain Branching Strategies
1. **Document Your Process:**  
   - Create (or update) a file named `solution.md` in your repository.
   - List all the Git commands you used in Tasks 1–4.
   - **Explain:** Write a brief explanation on **why branching strategies are important** in collaborative development. Consider addressing:
     - Isolating features and bug fixes
     - Facilitating parallel development
     - Reducing merge conflicts
     - Enabling effective code reviews

![image](https://github.com/user-attachments/assets/5fa582f8-d6b2-48e0-99dd-02562d0d7c2b)

---
## 🤷‍♂️Importance of Branching Strategies in Collaborative Development

Branching strategies are essential in collaborative development because they provide a structured approach to managing code changes. A well-defined branching strategy helps teams work efficiently, avoid conflicts, and maintain code quality. Below are the key reasons why branching strategies are important:

### 1. Isolating Features and Bug Fixes
Branching allows developers to work on new features or bug fixes independently without affecting the main codebase.

✅Why it matters?
prevents incomplete or experimental code from disrupting the stable version.
Allows multiple developers to work on different tasks simultaneously.
Makes it easier to track and roll back specific changes if needed.

Example:
A developer working on a new login feature creates a branch (feature-login).
A different developer working on fixing a critical bug creates a bugfix-auth-error branch.
Both can work in isolation without interfering with each other.

### 2. Facilitating Parallel Development
Branching enables multiple developers or teams to work on different parts of the project at the same time.

✅ Why it matters?
Accelerates development by allowing teams to work independently.
Reduces bottlenecks since developers don’t have to wait for one another to complete their work.
Supports different workflows like feature branching, GitFlow, and trunk-based development.

Example:
The frontend team is working on a feature-ui-redesign branch, while the backend team is implementing a feature-api-enhancements branch.
Both teams can develop and test their features separately before merging them into the main branch.

### 3. Reducing Merge Conflicts
Merge conflicts occur when multiple developers modify the same part of a file. A good branching strategy minimizes these conflicts by structuring how and when changes are merged.

✅ Why it matters?
Prevents long-lived branches that accumulate too many changes, making merging difficult.
Encourages frequent merges to integrate changes incrementally instead of all at once.
Reduces the time spent resolving conflicts and debugging issues caused by conflicting changes.

Example:
A team follows a feature branch strategy where developers regularly merge their branches into develop.
Instead of waiting until the last moment, they integrate changes frequently, reducing the likelihood of large conflicts.

### 4. Enabling Effective Code Reviews
Branching strategies support structured code review processes before changes are merged into the main branch.

✅ Why it matters?
Ensures that every change is reviewed for quality, security, and consistency.
Allows teammates to catch errors or suggest improvements before code reaches production.
Helps maintain a clean and organized codebase.

Example:
A developer pushes their feature-payment-gateway branch and opens a pull request (PR).
Other developers review the code, suggest changes, and approve the PR before merging it into main.
This process ensures high-quality code and reduces the risk of introducing bugs.

---
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


![image](https://github.com/user-attachments/assets/1599e7c2-d212-4e2a-bf78-10e390e5d24a)

![image](https://github.com/user-attachments/assets/6a0fa4ba-82f0-4fa3-b7ca-adbf3e01ea35)

---
## **Task 8: Undoing Changes – Reset & Revert**  
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
## Solution 

```bash
   git reset --soft HEAD~1
   ```
undo last commit and  take file to the stagging 

![image](https://github.com/user-attachments/assets/b816bcfe-2380-4841-a601-977d5fe50815)

Mixed Reset (unstages changes but keeps files).  
   ```bash
   git reset --mixed HEAD~1
   ```
![image](https://github.com/user-attachments/assets/eb6d14cb-5f89-4e87-9a62-e6efdd4a9a5f) 

4. Hard Reset (removes all changes).  
   ```bash
   git reset --hard HEAD~1
   ```
   ![image](https://github.com/user-attachments/assets/cd327e5a-9c04-49e3-a403-9e147e31fce2)
   

![image](https://github.com/user-attachments/assets/e68702d6-a20c-4922-a1cb-9dd3fac0de39)

![image](https://github.com/user-attachments/assets/9a5f9439-48f8-4b3b-bff1-7c4363cf8bc6)
---
## **Task 9: Stashing - Save Work Without Committing**  
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
## Solution :-

![image](https://github.com/user-attachments/assets/bf05456f-614a-4522-8913-e1831d75234c)

### git stash apply :-
Applies the latest stash to your working directory but keeps the stash.	

❌ Stash is not removed.

### git stash pop	
Applies the latest stash and removes it from the stash list.	

✅ Stash is removed.
---
## **Task 10: Cherry-Picking - Selectively Apply Commits**  
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
## Solution :-

### 1️⃣ How Cherry-Picking is Used in Bug Fixes

Cherry-picking is commonly used to apply bug fixes to different branches without merging unrelated changes. This is particularly useful in scenarios where a critical bug fix needs to be applied to a stable production branch while development continues separately.

## 2️⃣ Risks of Cherry-Picking

1.Duplicate Commits
2.Merge Conflicts
3.Loss of Context
4.Branch Divergence


![image](https://github.com/user-attachments/assets/cf776913-aa24-42bb-88fb-cd25629f0a8f)
---
## **Task 11: Rebasing - Keeping a Clean Commit History**  
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

## Solution :-


![image](https://github.com/user-attachments/assets/692f249b-9495-486f-8371-5966d2646f3a)


![image](https://github.com/user-attachments/assets/5efa8bd4-b71f-4dcb-b546-6b63c0689b9b)
---
## **Task 12: Branching Strategies Used in Companies**  
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

### - Git Flow (Feature, Release, Hotfix branches) :-

Gitflow can be used for projects that have a scheduled release cycle and for the DevOps best practice of continuous delivery. This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow. Instead, it assigns very specific roles to different branches and defines how and when they should interact. In addition to feature branches, it uses individual branches for preparing, maintaining, and recording releases. Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.

![image](https://github.com/user-attachments/assets/a5a9832b-c8ba-4e39-b3c1-39b9a8cd4381)

### - GitHub Flow (Main + Feature branches) :-

Git Flow is particularly useful when your development cycle resolves around releases.If you work using Scrum and expect to do a single release at the end of the sprint then you will want to use Git Flow. Also if you rely on QA to do manual testing of your code before it goes to production, then this could be another reason why you might want to use Git Flow.

![image](https://github.com/user-attachments/assets/6ba62537-e0ea-484e-b2e6-0d5882ab80bb)

###    - Trunk-Based Development (Continuous Integration) : -

all team members work on a single shared branch known as the trunk. There could be short-lived branches, but the emphasis is on frequent commits and maintaining shippable code at all times.

![image](https://github.com/user-attachments/assets/355d21a0-8dba-42bb-a718-c9c2b0026187)
---
## Bonus Task: Explore SSH Authentication
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

![image](https://github.com/user-attachments/assets/395c75a4-d83e-4b51-b8a4-3910533a1287)

![image](https://github.com/user-attachments/assets/086afc5b-5786-4757-a6b0-9e5285ae3f7f)

---
