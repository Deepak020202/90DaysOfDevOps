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
## Solution

### - Git Flow (Feature, Release, Hotfix branches) :-

Gitflow can be used for projects that have a scheduled release cycle and for the DevOps best practice of continuous delivery. This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow. Instead, it assigns very specific roles to different branches and defines how and when they should interact. In addition to feature branches, it uses individual branches for preparing, maintaining, and recording releases. Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.

![image](https://github.com/user-attachments/assets/a5a9832b-c8ba-4e39-b3c1-39b9a8cd4381)

### - GitHub Flow (Main + Feature branches) :-

Git Flow is particularly useful when your development cycle resolves around releases.If you work using Scrum and expect to do a single release at the end of the sprint then you will want to use Git Flow. Also if you rely on QA to do manual testing of your code before it goes to production, then this could be another reason why you might want to use Git Flow.

![image](https://github.com/user-attachments/assets/6ba62537-e0ea-484e-b2e6-0d5882ab80bb)

###    - Trunk-Based Development (Continuous Integration) : -

all team members work on a single shared branch known as the trunk. There could be short-lived branches, but the emphasis is on frequent commits and maintaining shippable code at all times.

![image](https://github.com/user-attachments/assets/355d21a0-8dba-42bb-a718-c9c2b0026187)

