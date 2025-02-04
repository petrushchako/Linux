# `free`

## Overview
This document describes various commands used to check free memory on a Linux system. Understanding memory usage is essential for performance monitoring and troubleshooting.

## Commands to Check Free Memory

### 1. `free` Command
The `free` command displays the total, used, and available memory in the system.

#### Syntax:
```bash
free [OPTIONS]
```

#### Common Options:
- `-h` → Display output in human-readable format (KB, MB, GB)
- `-m` → Show memory usage in megabytes
- `-g` → Show memory usage in gigabytes
- `-t` → Display a total line summarizing RAM and swap usage
- `-s <seconds>` → Continuously refresh memory usage every specified number of seconds

#### Example Usage:
```bash
free -h
```
Output example:
```
total        used        free      shared  buff/cache   available
8.0Gi       3.2Gi       1.8Gi      0.5Gi       3.0Gi       4.0Gi
```

### 2. `vmstat` Command
The `vmstat` command provides detailed memory, CPU, and process statistics.

#### Syntax:
```bash
vmstat [OPTIONS] [DELAY] [COUNT]
```

#### Example Usage:
```bash
vmstat -s
```
Displays system memory statistics in a summary format.

### 3. `top` and `htop` Commands
These commands show real-time memory usage along with CPU and process details.

#### `top` Command:
```bash
top
```
Press `Shift + M` to sort by memory usage.

#### `htop` Command (if installed):
```bash
htop
```
A user-friendly, color-coded alternative to `top`.

### 4. `cat /proc/meminfo`
The `/proc/meminfo` file contains detailed system memory information.

#### Example Usage:
```bash
cat /proc/meminfo | head -10
```
Displays the first 10 lines of memory details.

## Conclusion
These commands help monitor free memory and system performance. The `free -h` command is the simplest way to check available memory, while `top` and `htop` provide real-time monitoring.

