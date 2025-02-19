## Task 5: Advanced Branching and Switching
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
## Solution :-
