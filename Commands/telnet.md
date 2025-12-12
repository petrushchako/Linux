# `telnet`

The `telnet` command is an application-layer protocol that facilitates communication with a remote host, primarily used today for testing TCP connectivity and interacting with unencrypted network services.

> **SECURITY WARNING:** Telnet transmits all data, including credentials, in **plain text (unencrypted)**. It should **never** be used for secure remote access (use **SSH** instead).

## 1. Basic Syntax and Function
The primary use of `telnet` in modern DevOps and networking is to test if a specific port on a remote server is open and actively listening.

### **Syntax**
```bash
telnet [hostname or IP address] [port]
```

| Component | Description | Default |
| :--- | :--- | :--- |
| `hostname` or `IP address` | The address of the remote machine to connect to. | *(None)* |
| `port` | The port number the service is listening on. | `23` (Standard Telnet Port) |

### **Common Use Cases**
| Protocol | Port | Command Example | Use |
| :--- | :--- | :--- | :--- |
| **HTTP** | `80` | `telnet example.com 80` | Manually send an HTTP `GET` request to debug web servers. |
| **SMTP** | `25` | `telnet mailserver.com 25` | Manually send email commands (`HELO`, `MAIL FROM`, `RCPT TO`) to test mail flow. |
| **Database** | e.g., `3306` | `telnet 192.168.1.50 3306` | Check if the firewall is open and the database service is running. |
| **Remote CLI** | `23` | `telnet router.local` | Access legacy network devices that only support Telnet. |

### **Connection Status**
  * **Successful:** You will see a message like `Connected to <host>. Escape character is '^]'.` You can now type commands directly to the listening service.
  * **Connection Refused:** The host is reachable, but nothing is listening on that specific port, or a host-level firewall is blocking it.
  * **Connection Timed Out:** The connection was blocked by a network firewall or the host is offline/unreachable.
