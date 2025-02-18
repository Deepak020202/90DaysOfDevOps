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
