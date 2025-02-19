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
