# `sftp`

## SFTP (Secure File Transfer Protocol) - Recommended

**SFTP** is the secure method, using the **SSH** protocol to encrypt both commands and data. It is the preferred method for transferring files.

### Establishing the Connection

To connect, you use the `sftp` command, which is usually pre-installed.

```bash
sftp username@remote_host_ip_or_domain
# Example: sftp john@192.168.1.10
# Example: sftp jane@sftp.example.com
```

You will be prompted for the user's password. Once connected, the prompt changes to `sftp>`.

### Core SFTP Commands

| Command | Description | Example |
| :--- | :--- | :--- |
| `pwd` | Prints the **W**orking **D**irectory on the **remote** server. | `sftp> pwd` |
| `lpwd` | Prints the **W**orking **D**irectory on the **local** machine. | `sftp> lpwd` |
| `ls` | Lists files and directories on the **remote** server. | `sftp> ls` |
| `lls` | Lists files and directories on the **local** machine. | `sftp> lls` |
| `cd` | Change directory on the **remote** server. | `sftp> cd /var/www/html` |
| `lcd` | Change directory on the **local** machine. | `sftp> lcd ~/Desktop/reports` |
| `get` | **Downloads** a file from the remote server to the local machine. | `sftp> get remote_file.txt` |
| `put` | **Uploads** a file from the local machine to the remote server. | `sftp> put local_file.zip` |
| `mget` | Downloads **M**ultiple files (supports wildcards). | `sftp> mget *.log` |
| `mput` | Uploads **M**ultiple files (supports wildcards). | `sftp> mput *.config` |
| `exit` or `bye` | Closes the connection and exits the SFTP prompt. | `sftp> bye` |
