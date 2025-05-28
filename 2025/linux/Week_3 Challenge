

# How to Create a User Account on Linux with a Shell Script 

## Overview

Creating user accounts on a Linux system via the command line is a common task for system administrators. 
This guide walks you through a simple yet effective Bash script to create user accounts safely and interactively.

## Features

✨ Features
✅ Interactively creates a new user with a specified username and password.

🚫 Prevents duplication by checking if the username already exists.

🔐 Hides password input for security.

✅ Displays success or error messages for clear feedback.

The Script: user_management.sh
```
#!/bin/bash

create_user() {
  echo -n "Enter new username: "
  read username

  # Check if username is empty
  if [[ -z "$username" ]]; then
    echo "Error: Username cannot be empty!"
    exit 1
  fi

  # Check if user already exists
  if id "$username" &>/dev/null; then
    echo "Error: User '$username' already exists!"
    exit 1
  fi

  # Prompt for password
  echo -n "Enter password: "
  read -s password
  echo

  if [[ -z "$password" ]]; then
    echo "Error: Password cannot be empty!"
    exit 1
  fi

  # Create user and set password
  sudo useradd -m "$username"
  echo "$username:$password" | sudo chpasswd

  if [[ $? -eq 0 ]]; then
    echo "User '$username' created successfully!"
  else
    echo "Error: Failed to create user!"
    exit 1
  fi
}

# Main logic
case "$1" in
  -c|--create)
    create_user
    ;;
  *)
    echo "Usage: $0 -c | --create"
    exit 1
    ;;
esac
```

## Usage
Make the script executable and run it with the -c or --create flag:
```
bash
Copy
Edit
chmod +x user_management.sh
./user_management.sh -c
```
or
```
bash
Copy
Edit
./user_management.sh --create
```

🔄 Steps in Action
Script prompts for a username.

It checks if the username already exists.

If available, it prompts for a password (input is hidden).

The user is created, and a success message is displayed.

## Example

```
$ ./user_management.sh -c
Enter new username: testuser
Enter password: ******
User 'testuser' created successfully!
```

## Error Handling

- If the username already exists, the script will display:
  ```
  Error: User 'testuser' already exists!
  ```
- If any required input is missing, the script will exit without making changes.
- Missing username or password
```
javascript
Copy
Edit
Error: Username cannot be empty!
Error: Password cannot be empty!
```
##Notes
1)You must have sudo privileges to run this script successfully.

2)The password is not visible during input for added security.

3)The script can be expanded to support other operations like deleting or modifying users.

## Conclusion
This simple shell script is a practical tool for managing user accounts in Linux. It ensures basic input validation, prevents errors, and provides an intuitive command-line experience. 
Whether you're a system admin or a developer managing local users, this script is a handy addition to your toolkit.
