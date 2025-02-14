 ## 📌 Task :- User & Group Management

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
