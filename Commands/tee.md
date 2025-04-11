# `tee`
The `tee` command reads from standard input and writes the output to both standard output (the terminal) and one or more files. It is commonly used in pipelines to log command output while still viewing it in real-time.


### Syntax
```bash
tee [OPTION]... [FILE]...
```

### Common Use Cases
- View output on the terminal and save it to a file.
- Log script or command execution output for later review.
- Debug shell pipelines without losing visibility of intermediate steps.



### Examples
- Write Output to a File
  ```bash
  ls -l | tee output.txt
  ```
  Prints the output of `ls -l` and saves it in `output.txt`.

- Append to an Existing File
  ```bash
  echo "New log entry" | tee -a log.txt
  ```
  Adds `"New log entry"` to the end of `log.txt` without overwriting it.

- Write to Multiple Files
  ```bash
  date | tee file1.txt file2.txt
  ```
  Writes the current date to both `file1.txt` and `file2.txt`.

- Use in Script Logging
  ```bash
  ./deploy.sh | tee deploy.log
  ```
  Logs script output to `deploy.log` and prints it live to the terminal.

<br>

### Options
| Option | Description |
|--------|-------------|
| `-a`, `--append` | Append to the given file(s), do not overwrite |
| `-i`, `--ignore-interrupts` | Ignore interrupt signals |
| `--help` | Display help and exit |
| `--version` | Show version information and exit |

### Notes
- `tee` is particularly useful in automated deployments, backups, or CI/CD pipelines where you want to monitor output in real-time and archive logs.
- It is a standard utility available in almost all Unix-like operating systems.
