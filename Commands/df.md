# `df`

## Description:
The `df` (**disk free**) command in Linux is used to display information about the available and used disk space on file systems. It provides details such as the total size, used space, available space, and mount points of file systems.
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

## Example:
1. To display disk space usage for all file systems in human-readable format:

    `df -h`
2. To display disk space usage for a specific file system type:

    `df -t ext4`


## Usage:
1. Run the `df` command without any options to display disk space usage for all mounted file systems.
2. Use options to filter and customize the output according to specific requirements.
3. Review the output to gather information about disk space usage, including total size, used space, available space, and usage percentages.
4. Combine `df` with other commands or shell scripting for monitoring disk space usage and managing storage resources.

## Notes:
- The output of `df` may vary depending on the operating system and version.
- Some options may not be available on all systems or may behave differently across different Unix-like systems.
- File systems that are not mounted are not displayed by default. Use the `-a` option to include them in the output.
