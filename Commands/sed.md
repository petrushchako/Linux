# `sed`

## Description:
`sed` (stream editor) is a command-line utility for filtering and transforming text. It reads text from standard input or files, processes it line by line, and applies specified editing operations based on provided commands or scripts.

## Syntax:

```bash
sed [options] [script] [file...]
```

## Options:
- `-e <script>`, `--expression=<script>`: Add the script to the commands to be executed.
- `-f <file>`, `--file=<file>`: Read the script from a file instead of specifying it inline.
- `-i[SUFFIX]`, `--in-place[=SUFFIX]`: Edit files in place (make backup if SUFFIX supplied).
- `-n`, `--quiet`, `--silent`: Suppress automatic printing of pattern space.
- `-r`, `--regexp-extended`: Use extended regular expressions in the script.
- `-E`, `--posix`: Use POSIX compliant regular expressions (same as `-r`).
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

## Examples:

1. **Replace all occurrences of "old" with "new" in a file:**

    ```bash
    sed 's/old/new/g' file.txt
    ```

2. **Delete lines containing a specific pattern:**

    ```bash
    sed '/pattern/d' file.txt
    ```

3. **Print only lines that contain the word "error":**

    ```bash
    sed -n '/error/p' logfile.txt
    ```

4. **Replace only the first occurrence of "foo" with "bar" in each line:**

    ```bash
    sed 's/foo/bar/' file.txt
    ```

5. **Insert a line before a match:**

    ```bash
    sed '/pattern/i\This line goes before the match' file.txt
    ```

6. **Append a line after a match:**

    ```bash
    sed '/pattern/a\This line goes after the match' file.txt
    ```

7. **Edit file in place, replacing "apple" with "orange":**

    ```bash
    sed -i 's/apple/orange/g' fruits.txt
    ```

8. **Using multiple `-e` expressions:**

    ```bash
    sed -e 's/foo/bar/g' -e '/pattern/d' file.txt
    ```

9. **Write matched lines to another file:**

    ```bash
    sed -n '/pattern/w matches.txt' file.txt
    ```

10. **Quit after first match (improves performance on large files):**

    ```bash
    sed '/pattern/q' file.txt
    ```

## Usage:
1. Specify editing operations using `sed` commands or scripts.
2. Provide input text from standard input or files.
3. Run the `sed` command, and review the output for the applied transformations.
4. Optionally, use options to modify the behavior of the `sed` command.

## Notes:
- `sed` is a powerful tool for text manipulation, commonly used in scripting and automation tasks.
- Understanding regular expressions is essential for effective use of `sed`.
- Be cautious when using `sed` with large files or complex scripts, as it may impact performance.
