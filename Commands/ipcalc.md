# `ipcalc`

### Overview
`ipcalc` is a command-line utility used to perform IPv4 network calculations.
It takes an **IP address** and an optional **CIDR prefix** and outputs information such as:

- Network address
- Netmask (decimal & binary)
- Wildcard mask
- Broadcast address
- Host range
- Number of usable hosts

<br>

`ipcalc` is extremely useful for DevOps, networking, penetration testing, and scripting tasks where subnet calculations must be automated.

## Installation
### Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install ipcalc

# RedHat/CentOS
#sudo yum install ipcalc
```


### macOS (Homebrew)

```bash
brew install ipcalc
```



## Basic Usage
### Syntax

```
ipcalc <IP/CIDR>
```

or:

```
ipcalc <IP> <NETMASK>
```

Examples:

```bash
ipcalc 192.168.10.5/24
ipcalc 10.0.0.1 255.255.255.0
```

