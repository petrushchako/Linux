# `ps`

## Description:
`ps` is a command-line utility used to display information about processes running on a system. It provides a snapshot of the currently running processes, including their process IDs (PIDs), resource usage, and other attributes.

## Syntax:
`ps [options]`


## Options:
- `-A`, `--all`: Display information about all processes.
- `-u <user>`, `--user <user>`: Display processes owned by a specific user.
- `-p <pid>`, `--pid <pid>`: Display information for a specific PID or list of PIDs.
- `-e`, `--everyone`: Display information for all users.
- `-f`, `--full`: Display full-format listing.
- `-l`, `--long`: Display more detailed information.
- `-o <format>`, `--format <format>`: Specify output format.
- `-t <terminal>`, `--terminal <terminal>`: Display processes associated with a specific terminal.
- `-h`, `--help`: Display usage information and exit.
- `-v`, `--version`: Display version information and exit.

## Output Fields:
- `PID`: Process ID.
- `TTY`: Terminal associated with the process.
- `TIME`: CPU time used by the process.
- `CMD`: Command or command line used to launch the process.
