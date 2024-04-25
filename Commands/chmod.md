# `chmod`

## Description:
`chmod` is a command-line utility used to change the permissions of files and directories in Unix-like operating systems. It allows users to specify who can read, write, or execute a file or directory by modifying the file mode bits.

## Syntax:
`chmod [options] mode file...`


## Options:
- `-R, --recursive`: Recursively change permissions for directories and their contents.
- `-v, --verbose`: Display verbose output, showing the result of each permission change.
- `-c, --changes`: Like verbose mode, but only display output for files whose permissions were actually changed.
- `-f, --silent, --quiet`: Suppress error messages.
- `--reference=<file>`: Set the permissions of each file to be the same as the specified reference file.
- `-x, --execute`: Set execute permission.
- `-w, --write`: Set write permission.
- `-r, --read`: Set read permission.
- `u, g, o, a`: Specify permissions for the user (owner), group, others, or all (user, group, and others) respectively.
- `+, -, =`: Add, remove, or set permissions explicitly.
- `r, w, x`: Represent read, write, and execute permissions respectively.

## Mode:
The mode parameter consists of three parts:
- The first character specifies the target of the permissions modification (e.g., "u" for user).
- The following characters indicate the operation (+, -, or =) and the permissions to be modified (r, w, or x).
- Multiple operations and permissions can be combined, separated by commas (e.g., "u+x,g-w,o=r").
