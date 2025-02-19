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
