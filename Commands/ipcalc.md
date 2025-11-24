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



### Example 1: Simple /24 Subnet

Command:

```bash
ipcalc 192.168.10.5/24
```

Output:

```
Address:   192.168.10.5
Netmask:   255.255.255.0 = 24
Wildcard:  0.0.0.255
Network:   192.168.10.0/24
Broadcast: 192.168.10.255
HostMin:   192.168.10.1
HostMax:   192.168.10.254
Hosts/Net: 254  Class C
```


## Example 2: Using Netmask Instead of CIDR

Command:

```bash
ipcalc 10.10.10.10 255.255.0.0
```

Output:

```
Address:   10.10.10.10
Netmask:   255.255.0.0 = 16
Wildcard:  0.0.255.255
Network:   10.10.0.0/16
Broadcast: 10.10.255.255
HostMin:   10.10.0.1
HostMax:   10.10.255.254
Hosts/Net: 65534  Class A
```



## CIDR Calculations Provided by `ipcalc`
`ipcalc` can convert or compute:

### Netmask to Prefix
```bash
ipcalc 255.255.255.128
```

Outputs:

```
Netmask: 255.255.255.128 = 25
```

### Prefix to Netmask

```bash
ipcalc /20
```

Outputs:

```
Netmask: 255.255.240.0
```

### Multiple Formats
```bash
ipcalc 192.168.0.1/28
```



## Displaying Binary Output
Use the `-b` flag:

```bash
ipcalc -b 192.168.1.5/30
```

Output includes binary forms:

```
Address:   192.168.1.5        11000000.10101000.00000001.00000101
Netmask:   255.255.255.252 = 30
Wildcard:  0.0.0.3
Network:   192.168.1.4/30
Broadcast: 192.168.1.7
```




## Using `ipcalc` in Scripts
Example Bash snippet:

```bash
network=$(ipcalc -n 192.168.32.61/26 | awk -F' ' '/Network/ {print $2}')
broadcast=$(ipcalc -b 192.168.32.61/26 | awk -F' ' '/Broadcast/ {print $2}')

echo "Network: $network"
echo "Broadcast: $broadcast"
```


## Why `ipcalc` Is Useful for DevOps/SRE
* Determining subnets in infrastructure automation
* Validating IP ranges during provisioning
* Converting CIDR → netmask in Terraform/Ansible scripts
* Debugging network segmentation issues
* Creating firewall/ACL rules
* Educating yourself on subnet boundaries
