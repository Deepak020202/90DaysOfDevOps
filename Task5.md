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
