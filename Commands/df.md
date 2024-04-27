# `df`

## Description:
`df` is a command-line utility used to display information about disk space usage on Unix-like operating systems. It provides information about file system disk space usage, including total size, used space, available space, and usage percentages.

## Syntax:
`df [options] [filesystem...]`


## Options:
- `-h`, `--human-readable`: Print sizes in human-readable format (e.g., 1K, 234M, 2G).
- `-T`, `--print-type`: Print file system types.
- `-t <type>`, `--type=<type>`: Limit the display to file systems of a specific type.
- `-x <type>`, `--exclude-type=<type>`: Exclude file systems of a specific type from the display.
- `-a`, `--all`: Include all file systems, including those with 0 blocks.
- `--total`: Display a total line at the end of the output.
- `-i`, `--inodes`: Display inode information instead of block usage.
- `-l`, `--local`: Limit the display to local file systems.

## Output Fields:
- `Filesystem`: Name of the file system.
- `1K-blocks`: Total size of the file system in 1K blocks.
- `Used`: Used space in the file system.
- `Available`: Available space in the file system.
- `Use%`: Percentage of used space.
- `Mounted on`: Mount point of the file system.
