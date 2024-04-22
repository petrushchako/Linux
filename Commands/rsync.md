# `rsync``

## Description:
`rsync` is a powerful command-line utility for efficiently transferring and synchronizing files and directories between local and remote systems. It is widely used for backup and mirroring purposes due to its ability to preserve file permissions, ownerships, timestamps, and more.

## Syntax:

`rsync [options] source destination`


## Options:
- `-a, --archive`: Archive mode, preserves symbolic links, permissions, timestamps, and more.
- `-v, --verbose`: Increase verbosity, providing more detailed output during synchronization.
- `-z, --compress`: Enables compression during data transfer, reducing network usage.
- `-r, --recursive`: Recursively synchronize directories and their contents.
- `-n, --dry-run`: Performs a trial run without making any changes, useful for testing.
- `-P`: Combines the `--partial` and `--progress` options, showing progress during transfer and resuming interrupted transfers.
- `-e, --rsh=COMMAND`: Specifies the remote shell to use for communication.
- `--delete`: Deletes files on the destination that are not present on the source, keeping them in sync.

