## Working with Users and Groups
- Create a group named "qa" with `groupadd`
- Modify a group named "dev" with `groupmod`
- Create the users "sam" and "steve" with `useradd`
- Modify the users "john" and "sally" with `usermod`

```bash
groupadd -g 1301 qa
groupmod -n devops dev
cat /etc/group

useradd -M -G qa,devops sam
id sam

useradd -u 1250 -g qa steve
id steve

usermod -d /home/associate -g qa john
usermod -u 1255 -G qa sally
cat /etc/passwd
```

## Working with Ownership and Permissions
- Change the owner and group of `/usr/local/share/staging` and all its contents to "**sally**" and "**qa**" using `chown`
- Change the group of `/usr/local/share/production`
and its contents to "**devops**" using `chgrp`
- Use octal mode permissions to update files and directories with `chmod`
- Use symbolic mode permissions to update files and directories with `chmod`

## Removing Users and Groups
- Remove the users "**benedict**" and "**arnold**" with `userdel`
- Remove the group "**test**" with `groupdel`
