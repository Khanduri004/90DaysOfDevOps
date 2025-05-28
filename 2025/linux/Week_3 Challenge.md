

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

## How to Delete a User Account on Linux with a Shell Script
Managing user accounts is a key responsibility for Linux administrators. In this post, we’ll explore a simple Bash script that allows you to safely delete user accounts from the terminal — complete with validation and helpful feedback.

## Overview
This script provides a safe and user-friendly way to delete existing user accounts on a Linux system. It prompts for a username, checks if the user exists, and deletes the account while cleaning up associated files.

✨ ## Features
- Checks if the user exists before attempting deletion

- Deletes the user and their home directory

- Displays success and error messages clearly

- Requires and supports use with sudo privileges

## The Script: user_management.sh
Here’s the deletion logic you can include in your user_management.sh script:
``
bash

#!/bin/bash

delete_user() {
  echo -n "Enter username to delete: "
  read username

  # Check if username is empty
  if [[ -z "$username" ]]; then
    echo "Error: Username cannot be empty!"
    exit 1
  fi

  # Check if user exists
  if ! id "$username" &>/dev/null; then
    echo "Error: User '$username' does not exist!"
    exit 1
  fi

  # Delete the user and their home directory
  sudo userdel -r "$username"

  if [[ $? -eq 0 ]]; then
    echo "User '$username' deleted successfully!"
  else
    echo "Error: Failed to delete user '$username'!"
    exit 1
  fi
}

# Main logic
case "$1" in
  -d|--delete)
    delete_user
    ;;
  *)
    echo "Usage: $0 -d | --delete"
    exit 1
    ;;
esac
## Usage
To delete a user account, run the script with either the -d or --delete flag:
```
bash

chmod +x user_management.sh
./user_management.sh -d
```
or
```
bash

./user_management.sh --delete
```
## Steps in Action
1)You’ll be prompted to enter the username of the account to delete.

2)The script will check if the username exists.

3)If found, the user account and home directory will be deleted.

4)A confirmation message will be shown.

## Example Output
```
bash

$ ./user_management.sh -d
Enter username to delete: testuser
User 'testuser' deleted successfully!
```
##  Error Handling
Non-existent username:
```
bash

Error: User 'testuser' does not exist!
```
Missing username input:
```
bash

Error: Username cannot be empty!
```
Insufficient privileges (if not run with sudo):
```
bash
Error: Failed to delete user 'testuser'!
```
## Notes 
This script deletes the user’s home directory and associated files with -r. 
Remove -r if you want to retain home directories.

Always use with sudo or as the root user to ensure permission to delete accounts.

For system-critical accounts, proceed with extra caution — always double-check the username!

## Conclusion
This simple script makes user account management easier and safer for Linux administrators. It validates input, prevents accidental errors, and gives clear feedback throughout the process.


## How to Reset a User Password on Linux with a Shell Script
Resetting user passwords is a routine but critical task in system administration. In this guide, you’ll learn how to use a simple Bash script to securely reset the password of any existing user on a Linux system — complete with validation and user-friendly prompts.

## Overview
This script allows you to reset the password of an existing user account using the command-line interface. It checks whether the user exists before proceeding and provides secure password input and helpful messages throughout the process.

## Features
- Verifies the existence of the specified user

- Prompts for a new password securely (input is hidden)

-  Resets the password and confirms success

- Requires sudo privileges for secure system operations

## The Script: user_management.sh
Here’s the password reset logic you can integrate into your user_management.sh script:
``
#!/bin/bash

reset_password() {
  echo -n "Enter username: "
  read username

  # Check if username is empty
  if [[ -z "$username" ]]; then
    echo "Error: Username cannot be empty!"
    exit 1
  fi

  # Check if user exists
  if ! id "$username" &>/dev/null; then
    echo "Error: User '$username' does not exist!"
    exit 1
  fi

  # Prompt for new password
  echo -n "Enter new password: "
  read -s password
  echo

  if [[ -z "$password" ]]; then
    echo "Error: Password cannot be empty!"
    exit 1
  fi

  # Reset user password
  echo "$username:$password" | sudo chpasswd

  if [[ $? -eq 0 ]]; then
    echo "Password for user '$username' has been reset successfully!"
  else
    echo "Error: Failed to reset password for user '$username'!"
    exit 1
  fi
}

# Main logic
case "$1" in
  -r|--reset)
    reset_password
    ;;
  *)
    echo "Usage: $0 -r | --reset"
    exit 1
    ;;
esac
```

## Usage
Make the script executable and run it with the -r or --reset flag:
```
chmod +x user_management.sh
./user_management.sh -r
```
or
```
./user_management.sh --reset
```
## Steps in Action :
1)The script prompts for the username whose password needs to be reset.

2)It checks whether the username exists.

3)If found, it asks for a new password (input is hidden).

4)The password is updated, and a success message is shown.

##  Example Output :
```
$ ./user_management.sh -r
Enter username: testuser
Enter new password:
Password for user 'testuser' has been reset successfully!
```
## Error Handling
If the user doesn’t exist:
```
Error: User 'testuser' does not exist!
```
If no input is provided:
```
Error: Username cannot be empty!
Error: Password cannot be empty!
````
If run without sudo:
```
Error: Failed to reset password for user 'testuser'!
```
## Notes
1)You must have sudo privileges to reset passwords.

2)The password input is hidden for security using read -s.

3)You can expand the script to include additional password policies (e.g., minimum length or complexity).

## Conclusion
This Bash script simplifies the process of resetting a user password while incorporating essential validations and secure user interactions. It’s a handy addition to any Linux administrator's toolkit.

## **List User Accounts Script**

## Overview

This script provides a simple way to list all user accounts on a Linux system along with their corresponding User IDs (UIDs). It ensures a clear and structured output for easy reference.

## Features

- Lists all system users.
- Displays usernames along with their corresponding UIDs.

## Usage

### Running the Script

To list all user accounts, use the following command:

```
./user_management.sh -l
```
```
./user_management.sh --list
```

### Output

The script will display usernames along with their UIDs in a structured format.

## Example

```
$ ./user_management.sh -l
User Accounts:
root UID: 0
user1 UID: 1001
user2 UID: 1002
...
```
## Notes

- The script extracts user information from the `/etc/passwd` file.
- It filters out system service accounts to focus on actual users (if needed).

## Conclusion

This script provides an easy way to view all user accounts on a system, making it useful for system administrators and user management tasks.

## Help and Usage Information for a User Management Script
Providing clear, accessible usage information is crucial for any command-line tool. In this article, we’ll walk through how the Help and Usage Information feature works in a custom Linux User Management Script, helping users quickly understand all available commands and options.

## Overview
This script segment is designed to offer a quick and user-friendly guide directly from the terminal. When invoked, it prints detailed usage instructions and a list of supported command-line flags, making it easier for users—especially beginners—to use the script correctly.

## Features
- Displays usage instructions directly in the terminal

- Lists all supported options and their descriptions

- Serves as a quick reference for script navigation

- Automatically shown if no arguments are provided

## The Script Segment
Here’s the --help functionality that can be included in your user_management.sh script:
```
bash

print_help() {
  echo "User Account Management Script"
  echo "Usage: ./user_management.sh [OPTION]"
  echo
  echo "Options:"
  echo "  -c, --create     Create a new user account"
  echo "  -d, --delete     Delete an existing user account"
  echo "  -r, --reset      Reset password for a user account"
  echo "  -l, --list       List all system user accounts with UID"
  echo "  -h, --help       Display this help message"
}
```
And here's how you incorporate it into your main script logic:
```
bash

case "$1" in
  -c|--create)
    create_user
    ;;
  -d|--delete)
    delete_user
    ;;
  -r|--reset)
    reset_password
    ;;
  -l|--list)
    list_users
    ;;
  -h|--help|*)
    print_help
    ;;
esac
```

## Usage
To access the help menu, run the script with the -h or --help flag:
```
bash

./user_management.sh -h
or
```
bash
```
./user_management.sh --help
```
If you run the script without any arguments, it will also display the help menu by default.

## Terminal Output Example
``
bash
$ ./user_management.sh -h
````
User Account Management Script
Usage: ./user_management.sh [OPTION]

Options:
  -c, --create     Create a new user account
  -d, --delete     Delete an existing user account
  -r, --reset      Reset password for a user account
  -l, --list       List all system user accounts with UID
  -h, --help       Display this help message

## Notes
- Sudo required: While the help menu can be viewed by any user, actual account operations (create/delete/reset) require sudo privileges.
- Ease of use: New users can learn how to interact with the script without reading external documentation. 
- Extensible: Whenever you add new features to your script, update the help section accordingly.

## Conclusion
The --help functionality is essential for making your script user-friendly and self-documenting. Whether you’re distributing your script internally or sharing it with a wider audience, providing a clear usage guide ensures everyone can use it with confidence.
