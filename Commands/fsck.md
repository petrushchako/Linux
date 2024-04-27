# `fsck`

## Description:
fsck is a command-line utility used to check and repair file systems on Unix-like operating systems. It performs a consistency check on the file system and attempts to fix any errors found.

## Syntax:
`fsck [options] [filesystem...]`

## Options:
- `-a`: Automatically repair file systems without prompting for confirmation.
- `-p`: Automatically repair file systems that are flagged as requiring repair.
- `-y`: Answer "yes" to all prompts, useful for automated/scripted repairs.
- `-t <type>`: Specify the file system type to check (e.g., ext4, ntfs).
- `-r`: Interactively repair file systems, prompting the user for confirmation before making changes.
- `-V`: Display version information and exit.
- `-N`: Dry-run mode, perform a trial run without making any changes.

