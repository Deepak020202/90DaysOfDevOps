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

## Output :-

![image](https://github.com/user-attachments/assets/1985bd97-a4f0-49fe-9e85-878019b33efb)
