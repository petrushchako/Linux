# `sed`

## Description:
`sed` (stream editor) is a command-line utility for filtering and transforming text. It reads text from standard input or files, processes it line by line, and applies specified editing operations based on provided commands or scripts.

## Syntax:

`sed [options] [script] [file...]`

## Options:
- `-e <script>`, `--expression=<script>`: Add the script to the commands to be executed.
- `-f <file>`, `--file=<file>`: Read the script from a file instead of specifying it inline.
- `-i[SUFFIX]`, `--in-place[=SUFFIX]`: Edit files in place (make backup if SUFFIX supplied).
- `-n`, `--quiet`, `--silent`: Suppress automatic printing of pattern space.
- `-r`, `--regexp-extended`: Use extended regular expressions in the script.
- `-E`, `--posix`: Use POSIX compliant regular expressions (same as -r).
- `-s`, `--separate`: Consider files as separate rather than a single continuous stream.
- `-u`, `--unbuffered`: Buffer both input and output, flushing the output after each line.
- `-z`, `--null-data`: Separate lines by NUL characters, treating input as a whole text.
- `--version`: Display version information and exit.
- `--help`: Display usage information and exit.

## Commands:
- `s`: Substitute command, replaces occurrences of a pattern with a replacement.
- `p`: Print command, prints the current pattern space.
- `d`: Delete command, deletes the current pattern space and starts the next cycle.
- `g`: Global command, applies the command to all matches in the pattern space.
- `w`: Write command, writes the pattern space to a file.
- `q`: Quit command, immediately exits the script with the specified status.