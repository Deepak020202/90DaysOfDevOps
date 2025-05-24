## Task 1: Account Creation

1. Implement an option `-c` or `--create` that allows the script to create a new user account. The script should prompt the user to enter the new username and password.

2. Ensure that the script checks whether the username is available before creating the account. If the username already exists, display an appropriate message and exit gracefully.

3. After creating the account, display a success message with the newly created username.

### Solution

## Code :-

```
#!/bin/bash

account_create() {

        echo "Enter username :-"
        read username

        if id "$username" &>/dev/null; then
                echo "==========="$username" already exist====="
                exit 1
        fi
sudo useradd -m "$username"

echo "Enter password :"
read password

echo "$password"

echo "============== USER CREATED ==============="

}

if [[ "$1" == "--create" ]]; then
        account_create
else
        echo "You enter a wrong input :"
fi
```


![image](https://github.com/user-attachments/assets/1985bd97-a4f0-49fe-9e85-878019b33efb)

---

## Task 2: Account Deletion

1. Implement an option `-d` or `--delete` that allows the script to delete an existing user account. The script should prompt the user to enter the username of the account to be deleted.

2. Ensure that the script checks whether the username exists before attempting to delete the account. If the username does not exist, display an appropriate message and exit gracefully.

3. After successfully deleting the account, display a confirmation message with the deleted username.

### Solution :-

### Code :- 

```
#!/bin/bash

delete_account() {
echo "Enter the username want to delete :"

read username

if ! id "$username" &>/dev/null; then
        echo "$username does not exist"
        exit 1
fi

sudo userdel -r $username

echo "============= USER DELETED ================================"
}

if [[ "$1" == "-delete"  ]]; then
        delete_account
fi

```
---
## Part 3: Password Reset

1. Implement an option `-r` or `--reset` that allows the script to reset the password of an existing user account. The script should prompt the user to enter the username and the new password.

2. Ensure that the script checks whether the username exists before attempting to reset the password. If the username does not exist, display an appropriate message and exit gracefully.

3. After resetting the password, display a success message with the username and the updated password.

## Solution :-

### Program :-

```
#!/bin/bash

reset_pass() {

        read -p "Enter username :-" username

        if id "$username" &>/dev/null; then


        read -p "Enter the new password :" password

         echo "$username:$password" | sudo chpasswd

          echo "successfully password reset!!!"

  else
      echo "user does not exist "
      exit 1
        fi

}

if [[ $1 == "--reset" ]]; then
        reset_pass
else
        echo "$0 --reset"
        exit 1
fi
```

### Output :- 

![image](https://github.com/user-attachments/assets/81a831da-3b9b-44cb-a482-f1a674364ef8)

---
## Part 4: List User Accounts

1. Implement an option `-l` or `--list` that allows the script to list all user accounts on the system. The script should display the usernames and their corresponding user IDs (UID).

## Solution :-

### Program 

```
#!/bin/bash

echo "---------------------------------------PRINTING USER & ID--------------------------------"

if [[ $1 == "--list" ]] then
        cut -d: -f 1,3 /etc/passwd
else
exit 1
fi
```

### Output :-

![image](https://github.com/user-attachments/assets/d1d61458-6d7b-4d0f-ad7c-de637c4326b3)

---

## Task 5: Help and Usage Information

1. Implement an option `-h` or `--help` that displays usage information and the available command-line options for the script.

## Solution :-

## Code 
```
#!/bin/bash

list_user() {
  echo "---------- PRINTING USER & ID ----------"
  cut -d: -f1,3 /etc/passwd
}

user_create() {
  read -p "Enter username: " username

  if id "$username" &>/dev/null; then
    echo "Error: Username '$username' already exists."
    return 1
  fi

  sudo useradd "$username"

  read -s -p "Enter password: " password
  echo
  echo "$username:$password" | sudo chpasswd

  echo "================= SUCCESSFULLY CREATED ================="
}

reset_pass() {
  read -p "Enter username: " username

  if id "$username" &>/dev/null; then
    read -s -p "Enter the new password: " password
    echo
    echo "$username:$password" | sudo chpasswd
    echo "Successfully reset password for '$username'!"
  else
    echo "Error: User '$username' does not exist."
    return 1
  fi
}

delete_account() {
  read -p "Enter the username to delete: " username

  if ! id "$username" &>/dev/null; then
    echo "Error: Username '$username' does not exist."
    return 1
  fi

  sudo userdel -r "$username"

  echo "============= USER '$username' DELETED ================"
}

case "$1" in
  --list)
    list_user
    ;;
  --create)
    user_create
    ;;
  --reset)
    reset_pass
    ;;
  --delete)
    delete_account
    ;;
  *)
    echo "Invalid option: $1"
    echo "Usage: $0 [OPTION]"
    echo "Options:"
    echo "  --list          List all users and their IDs."
    echo "  --create        Create a new user account."
    echo "  --reset         Reset a user's password."
    echo "  --delete        Delete an existing user account."
    return 1
    ;;
esac

```
---

## Bonus Task 

## Automated Backup & Recovery using Cron


This is another challenge for Day 2 of the Bash Scripting Challenge! In this challenge, you will create a bash script that performs a backup of a specified directory and implements a rotation mechanism to manage backups.

## Challenge Description

Your task is to create a bash script that takes a directory path as a command-line argument and performs a backup of the directory. The script should create timestamped backup folders and copy all the files from the specified directory into the backup folder.

Additionally, the script should implement a rotation mechanism to keep only the last 3 backups. This means that if there are more than 3 backup folders, the oldest backup folders should be removed to ensure only the most recent backups are retained.

> The script will create a timestamped backup folder inside the specified directory and copy all the files into it. It will also check for existing backup folders and remove the oldest backups to keep only the last 3 backups.

## Solution : - 

```
#!/bin/bash
<< info

Task 6 : - Automated Backup & Recovery using Cron
info
       # argument check
    if [ -z "$1" ]; then
    echo "Usage: $0 <directory_path>"
        exit 1
        fi

        #path set

        SOURCE_DIR="$1"
        BACKUP_DIR="${SOURCE_DIR}/backups"
        TIMESTAMP=$(date +"%S-%M-%H___%d-%m-%Y")
        BACKUP_PATH="${BACKUP_DIR}/backup_${TIMESTAMP}"

        mkdir -p "$BACKUP_DIR"

        # Backup create
        echo "Creating backup at: $BACKUP_PATH"
        rsync -av --exclude="backups" "$SOURCE_DIR/" "$BACKUP_PATH"


        # Keep only 3 backup
        BACKUP_COUNT=$(ls -dt ${BACKUP_DIR}/backup_* | wc -l)
        if [ "$BACKUP_COUNT" -gt 3 ]; then
            echo "Removing old backups..."
                ls -dt ${BACKUP_DIR}/backup_* | tail -n +4 | xargs rm -rf
                fi

```

![image](https://github.com/user-attachments/assets/c961d657-2fc7-4ec7-9751-9dbcce929d6f)

![image](https://github.com/user-attachments/assets/e9eca99f-5563-4976-8d48-07609b3276e4)
