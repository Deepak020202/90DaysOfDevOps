## 📌 Task :- Log File Analysis with AWK, Grep & Sed
Log File Analysis with AWK, Grep & Sed
Logs are crucial in DevOps! You’ll analyze logs using the Linux_2k.log file from LogHub (GitHub Repo).

Task: Download the log file from the repository. Extract insights using commands: Use grep to find all occurrences of the word "error". Use awk to extract timestamps and log levels. Use sed to replace all IP addresses with [REDACTED] for security. Bonus: Find the most frequent log entry using awk or sort | uniq -c | sort -nr | head -10.

---
## Solution :-

### Step1: - Use grep to find all occurrences of the word "error".

In the log file error word are not exist 

![image](https://github.com/user-attachments/assets/6263555b-7bc7-4469-8960-cef9421a6054)

### Step2 :- Use awk to extract timestamps and log levels.

![image](https://github.com/user-attachments/assets/7a0e0845-f08c-4e4f-9755-6314790bfb45)

### Step3 :- Use sed to replace all IP addresses with [REDACTED] for security.

```
sed -E 's/[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/[REDACTED]/g' Linux_2k.log
```

![image](https://github.com/user-attachments/assets/fedb4a63-8d79-4b56-8292-af92d094aecd)

### Step 4 (Bonus) :- Find the most frequent log entry using awk or sort | uniq -c | sort -nr | head -10.

![image](https://github.com/user-attachments/assets/947c393d-d05c-4203-96ca-4509a37017c3)

---
