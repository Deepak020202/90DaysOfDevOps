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
