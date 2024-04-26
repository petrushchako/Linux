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

## Example:
1. To terminate a process with a specific PID:   
    `kill 1234`
2. To send a different signal to a process:
    `kill -s SIGTERM 1234`



## Usage:
1. Specify the PID or PIDs of the processes to be signaled.
2. Optionally, specify the signal to send using the `-s` option.
3. Run the `kill` command, and the specified signal will be sent to the target processes.

## Notes:
- The default signal sent by `kill` is `SIGTERM`, which allows processes to perform cleanup operations before terminating.
- Use caution when sending signals, especially `SIGKILL`, as it does not allow processes to perform cleanup and may lead to data loss or corruption.
- Only processes owned by the current user or those running with the same effective user ID can be signaled.




