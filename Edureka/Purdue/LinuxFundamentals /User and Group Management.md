### System files
* **/etc/shadow**
/etc/shadow is a file that contains encrypted passwords, related information for the system's accounts and optional aging
information. Since /etc/shadow file is only readable by the root user, malicious users cannot crack their fellow users' passwords.
Syntax: [username]:[enc_pwd]:[last_pwd_change]:[pwd_validity]:[warn_date]:[acc_validity]:[acc_disablity]
* **/etc/sudoers
Find out more
* **/etc/passwd** 
Contains the following information
Syntax: [username]:[password]:[UID]:[GID]:[GECOS]:[home_dir]:[shell_path]
* **/etc/skel**
Directory contains files and directories that are automatically copied over to a new user's home directory
A home directory serves as the repository for a user's personal files, directories and programs,
including personal configuration files. Home directory has many important folders like /etc directory
and its subdirectories and configuration files for the system.


### User management
* **Creating User**
Create a user with home directory 
```# sudo useradd -m ‹username>```
Create a user with a predefined home directory
```# sudo useradd -m -d /home/ubuntu/user ‹username>```
Create a user with an expiry date
```# sudo useradd -m - e <yyyy-mm-dd> ‹username>```
Note:
You can also use **adduser** command to add new users. The difference is that **useradd** is a native binary compiled with the system. But **adduser** is a Perl script, which uses useradd binary in the backend.
* **Delete User**
```# sudo userdel <userName>```
You can use 'userdel' command to delete users from the Linux system By default, the home directory of the user is not deleted.
You can delete the home directory of the user and the mail spool using **-r** flag with the userdel command
* **Modify user**
The command **usermod** is used to modify or change any attribute of an already created user account via the command line. 
It is a simple command with lots of options that can be used to make changes to an existing user.
Note: You can use option **-e** with **usermod** to set expiry date on a user account with the date format YYYY-MM-DD.
**chage** command is used to view and change password related information. 
Example:
In this example, the **chage** command is used to check the current account expiry status:
```
    sudo chage -l sam
    sudo usermod -e 2020-12-12 sam
    sudo chage -l sam
```

### User groups
Linux is a multiuser operating system, and groups are nothing but the collection of users. 
The concept of groups makes it easy for administrators to manage users with the same security and access privileges. 
|   |
|---|
|Every user has a primary user group and zero or more supplementary groups.|
|User groups is a simple mechanism in Linux systems to organize a collection of users|
|Each user group is associated with a unique ID called the GID|
|There are two types of groups - a primary group and a supplementary group|
|Each user is a member of a primary group and of zero or 'more than zero' supplementary groups|
|Users may be added to an existing group to utilize the privileged access it grants|
|Every user by default gets his/her own group unless restricted manually|

By default, all the information listing groups are stored in a file called **/etc/group**. 
The hashed passwords that you can see in the **/etc/group** file are stored in **/etc/gshadow** file.

|Command|Syntax|
|---|---|
|**cat /etc/group**|Syntax: [group_name]:[group_password]:[GID]:[users]|
|**cat /etc/gshadow**|Syntax: [group_name]:[group_password]:[group_admins]:[users]|

Note: 
If no password is set, it is indicated by **!** or **!!**. It implies only members can access the group.
**!!** indicates that no password has ever been set on the group


#### **Create Group**
You can use 'groupadd' command to create a new group. It creates a new group account using the values specified on the command line plus the default values from the system.

|Command|Options|Description|
|---|---|---|
|groupadd {option} {groupName}|||
| |-f|Causes the command to simply exit, if the specified group already exists|
| |-g|The number value of the group's ID. This value must be unique, unless the **-o** option is used|
| |-p|Specifies to use given password for the new group|
| |-k|Overrides the default value of **/etc/login.defs** file|
Example:
```
sudo groupadd developers
groups //will display groups
tail -5 /etc/group
```

#### **Modify and Delete Groups**
* **groupmod** 
You can use this command to modify the definition of a user group by modifying the appropriate entry in the group database.
* **groupdel** 
You can use this command for deleting all entries that refer to group, thereby, modifying the system account files by the
named group must exist. This only removes the group, not the files associated with that group. They can be accessed by their owners

Example 1:
```
edureka@edureka:~$ tail -5 /etc/group
. . .
developers: x:1003:
edureka@edureka:~$ sudo groupmod - n front_end_developers developers
edureka@edureka:~$ sudo groupmod -g 345 front end developers
edureka@edureka:~$ tail -5 /etc/group
. . .
front_end developers: x:345:
```

Example 2:
```
edureka@edureka:~$ tail -5 /etc/group
front_end_developers:x:345:
testers:x:1005:
edureka@edureka:~$ sudo groupdel testers
edureka@edureka:~$ tail -5 /etc/group
front_end _developers:x:345:
```

#### Adding Existing User To Different Groups
```
edureka@edureka:~$ sudo tail -4 /etc/passwd
mylinux:x:1001:1001:Abel,301,2345628393,4447828282,nil:/home/mylinux:/bin/bash
kate:x:1002:345::/home/sam:/bin/bash
an: x: 1003:1005: Sam Winchester, 456,4579943426,7893567742, nil: /home/sam:/bin/bash
dean: x: 1004:1007: Dean Winchester, 5325897667,345434333,nil,nil: /home/dean: /bin/bash
edureka@edureka:~$ sudo usermod -d /home/mylinux - g sam - G front_end_developers, management -s /bin/bash sam
```
```
edureka@edureka:~$ sudo tail -2 /etc/passwd
sam: x: 1003:1005: Sam Winchester, 456,4579943426,7893567742, nil: /home/mylinux:/bin/bash
dean: x: 1004:1007: Dean Winchester, 5325897667,345434333,nil,nil:/home/dean: /bin/bash
edureka@edureka:~$ tail -7 /etc/group
front end developers:: 345: sam
back_end_developers: x:1003:
operations_team:x:1004:
it_support:x:1006:
sam:x:1005:
dean: x:1007:
management:: 1008: sam
```
