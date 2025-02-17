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

