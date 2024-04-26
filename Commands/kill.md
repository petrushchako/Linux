# `kill`

## Description:
`kill` is a command-line utility used to send signals to processes in Unix-like operating systems. It allows users to terminate or manipulate processes by specifying their process IDs (PIDs) or job IDs.

## Syntax:

`kill [options] <PID>...`

## Options:
- `-s <signal>`, `--signal=<signal>`: Specify the signal to send. If not provided, the default signal is SIGTERM (15).
- `-l`, `--list`: List available signal names.
- `-L`, `--table`: Display a table of signal names and their corresponding numbers.
- `-h`, `--help`: Display usage information and exit.
- `-V`, `--version`: Display version information and exit.


## Signals:
- `SIGHUP (1)`: Hangup signal, typically sent to daemons to restart them.
- `SIGINT (2)`: Interrupt signal, often sent by pressing Ctrl+C, terminates the process.
- `SIGTERM (15)`: Termination signal, requests the process to terminate gracefully.
- `SIGKILL (9)`: Kill signal, forcibly terminates the process.
- `SIGSTOP (19)`: Stop signal, suspends the process.
- `SIGCONT (18)`: Continue signal, resumes the execution of a stopped process.


