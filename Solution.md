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

## Part 5: Help and Usage Information

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
