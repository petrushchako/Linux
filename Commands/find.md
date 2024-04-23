# `find`

## Description:
`find` is a command-line utility used for searching files and directories based on various criteria such as name, size, permissions, and more. It recursively descends the directory hierarchy starting from a specified path and matches files based on the specified criteria.

## Syntax:
`find [path...] [expression]`


## Options:
- `-name <pattern>`: Search for files and directories with a specified name pattern.
- `-type <type>`: Search for files of a specified type (f for regular files, d for directories, l for symbolic links, etc.).
- `-size <size>`: Search for files with a specified size (e.g., +10M for files larger than 10 megabytes).
- `-user <username>`: Search for files owned by a specific user.
- `-group <groupname>`: Search for files belonging to a specific group.
- `-perm <mode>`: Search for files with specific permissions.
- `-mtime <days>`: Search for files modified within a specified number of days.
- `-exec <command> {} +`: Execute a command on each matched file.
- `-print`: Print the pathname of matched files (default action).

## Expression:
- `-and`: Logical AND operator.
- `-or`: Logical OR operator.
- `-not`: Logical NOT operator.
