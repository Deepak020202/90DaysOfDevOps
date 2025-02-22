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


