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
