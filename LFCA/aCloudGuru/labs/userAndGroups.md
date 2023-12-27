## Working with Users and Groups
- Create a group named "qa" with `groupadd`
- Modify a group named "dev" with `groupmod`
- Create the users "sam" and "steve" with `useradd`
- Modify the users "john" and "sally" with `usermod`

## Working with Ownership and Permissions
- Change the owner and group of `/usr/local/share/staging` and all its contents to "**sally**" and "**qa**" using `chown`
- Change the group of `/usr/local/share/production`
and its contents to "**devops**" using `chgrp`
- Use octal mode permissions to update files and directories with `chmod`
- Use symbolic mode permissions to update files and directories with `chmod`