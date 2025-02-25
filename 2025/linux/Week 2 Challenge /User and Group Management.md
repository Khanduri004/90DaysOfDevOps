# Linux System Administration & Automation
# User & Group Management

**Task 1 :**

Create a user devops_user and add them to a group devops_team. 
To create the user in linux the command used is **sudo useradd -M devops_user**
The users present in the system can be seen in the **/etc/passwd file**

<img width="963" alt="image" src="https://github.com/user-attachments/assets/bb16648e-aa1c-410f-b64f-b8083acb9e61" />

To create a group the command used in linux is sudo groupadd devops_team
The list of the groups are present in /etc/group
Now we need to add the devops_user to the group devops_team
In order to do this we have a command : **sudo gpasswd -a devops_user devops_team**

Set a password and grant sudo access.
In order to set the password and grant the user devops_user sudo access we need to add the user to the sudo group.
This can be done using the command: **sudo usermod -aG sudo devops_user**

Restrict SSH login for certain users in /etc/ssh/sshd_config.
To deny the ssh login to the user we need to append DenyUsers <theusername> to the file /etc/ssh/sshd_config .

