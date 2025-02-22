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


