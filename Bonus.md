## Task 6:- Automated Backup & Recovery using Cron


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



