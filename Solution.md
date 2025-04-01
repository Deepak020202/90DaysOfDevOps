 ## 📌 Task 1:- User & Group Management

Learn about Linux users, groups, and permissions (/etc/passwd, /etc/group).
Task:
Create a user devops_user and add them to a group devops_team.
Set a password and grant sudo access.
Restrict SSH login for certain users in /etc/ssh/sshd_config.

---
## Solution :-

### Step1. Adding devops_user and add them to a group devops_team.
```
sudo useradd devops_user
sudo groupadd devops_team
sudo usermod -aG devops_team devops_user
cat /etc/group 
```
![image](https://github.com/user-attachments/assets/a8464f01-b9ab-4fc7-ac84-588a49ce7f2e)

---
### Step2. Set a password for devops_user and grant sudo access.
```
passwd devops_user
sudo usermod -aG sudo devops_user
cat /etc/passwd
```

![image](https://github.com/user-attachments/assets/9b30b420-f5da-4d80-b39b-af4a38d6bedd)

---
### Step3. Restrict SSH login for certain users in /etc/ssh/sshd_config

locate the ssh_config file and make changes in AllowUser or DenyUser and add username after that SSH login will be not allowed for that user 

---

## 📌 Task 2:-  File & Directory Permissions
  Create /devops_workspace and a file project_notes.txt. Set permissions: Owner can edit, group can read, others have no access. Use ls -l to verify permissions.

---

## Solution 

![image](https://github.com/user-attachments/assets/2e055528-cf3a-4306-98d7-7b2336c3d1a5)

---

## 📌 Task 3:- Log File Analysis with AWK, Grep & Sed
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
## 📌 Task 4:- Volume Management & Disk Usage
 Create a directory /mnt/devops_data. Mount a new volume (or loop device for local practice). Verify using df -h and mount | grep devops_data.

---

## Solution :-

### Step1 :- create a volume on AWS

![image](https://github.com/user-attachments/assets/98c12cef-526c-49af-a3b2-4668a30d475a)

### Step2 :- Mount this volume on EC2 instance

![image](https://github.com/user-attachments/assets/bba9c374-8850-4fb7-b2e1-c3d462bf4d08)

### Step 3 :- Verify using df -h

![image](https://github.com/user-attachments/assets/8e15b2d2-6c1c-49b4-b728-27db8fa682d7)

---
## 📌 Task 5:- Process Management & Monitoring
 Start a background process (ping google.com > ping_test.log &). Use ps, top, and htop to monitor it. Kill the process and verify it's gone.

---

## Solution :-

### ping google.com

![image](https://github.com/user-attachments/assets/d1c95295-46d4-4e9e-83b5-7aa13257edf5)

### Use ps & Kill the process and verify it's gone.

![image](https://github.com/user-attachments/assets/220f6fce-c2e7-41c7-be5b-7e532a4de555)

### htop to monitor it

![image](https://github.com/user-attachments/assets/4269f975-c02c-495f-84f4-4b9cff2619c4)

---
## 📌 Tasks 6:- Automate Backups with Shell Scripting
 Write a shell script to back up /devops_workspace as backup_$(date +%F).tar.gz. Save it in /backups and schedule it using cron. Make the script display a success message in green text using echo -e.Automate Backups with Shell Scripting

---
## Solution :-

![image](https://github.com/user-attachments/assets/f1294485-f338-4feb-9ea6-bb75bd91e545)

![image](https://github.com/user-attachments/assets/87ca7c76-245d-40e5-b281-f2047dd765c7)

![image](https://github.com/user-attachments/assets/85049505-8ed5-4860-82e4-f49c31bae0dc)
