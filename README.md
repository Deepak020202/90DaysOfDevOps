# Week 2: Linux System Administration & Automation
---
## Welcome to Week 2 of the 90 Days of DevOps - 2025 Edition!
#### This week, we dive into Linux system administration and automation, covering essential topics such as user management, file permissions, log analysis, process control, volume mounts, and shell scripting.

#### 🚀 Project: DevOps Linux Server Monitoring & Automation
Imagine you're managing a Linux-based production server and need to ensure that users, logs, and processes are well-managed. You will perform real-world tasks such as log analysis, volume management, and automation to enhance your DevOps skills.
---
## 📌 Tasks

### 1️⃣ User & Group Management

Learn about Linux users, groups, and permissions (/etc/passwd, /etc/group).
Task:
Create a user devops_user and add them to a group devops_team.
Set a password and grant sudo access.
Restrict SSH login for certain users in /etc/ssh/sshd_config.

---
### 2️⃣ File & Directory Permissions

Task:
Create /devops_workspace and a file project_notes.txt.
Set permissions:
Owner can edit, group can read, others have no access.
Use ls -l to verify permissions.

---
### 3️⃣ Log File Analysis with AWK, Grep & Sed**

Logs are crucial in DevOps! You’ll analyze logs using the Linux_2k.log file from LogHub (GitHub Repo).

Task:
Download the log file from the repository.
Extract insights using commands:
Use grep to find all occurrences of the word "error".
Use awk to extract timestamps and log levels.
Use sed to replace all IP addresses with [REDACTED] for security.
Bonus: Find the most frequent log entry using awk or sort | uniq -c | sort -nr | head -10.

---
### 4️⃣ Volume Management & Disk Usage**

Task:
Create a directory /mnt/devops_data.
Mount a new volume (or loop device for local practice).
Verify using df -h and mount | grep devops_data.

---
### 5️⃣ Process Management & Monitoring**

Task:
Start a background process (ping google.com > ping_test.log &).
Use ps, top, and htop to monitor it.
Kill the process and verify it's gone.

---

### 6️⃣ Automate Backups with Shell Scripting**

Task:
Write a shell script to back up /devops_workspace as backup_$(date +%F).tar.gz.
Save it in /backups and schedule it using cron.
Make the script display a success message in green text using echo -e.

---
