# `ftp`

## FTP (File Transfer Protocol) - Legacy & Unencrypted ⚠️

**FTP** is an older protocol that transmits all data, including credentials and files, in **plain text** (unencrypted). Use SFTP instead unless specifically required.

### Establishing the Connection

To connect, you use the `ftp` command.

```bash
ftp remote_host_ip_or_domain
# Example: ftp 192.168.1.5
```

The system will prompt you for the `username` and then the `password`. Once connected, the prompt changes to `ftp>`.

### Core FTP Commands

| Command | Description | Example |
| :--- | :--- | :--- |
| `ls` or `dir` | Lists files and directories on the **remote** server. | `ftp> ls` |
| `pwd` | Prints the **W**orking **D**irectory on the **remote** server. | `ftp> pwd` |
| `cd` | Change directory on the **remote** server. | `ftp> cd public_files` |
| `lcd` | Change directory on the **local** machine. | `ftp> lcd ~/downloads` |
| `get` | **Downloads** a single file from the remote server. | `ftp> get remote_file.pdf` |
| `mget` | Downloads **M**ultiple files (supports wildcards). | `ftp> mget *.jpg` |
| `put` | **Uploads** a single file to the remote server. | `ftp> put local_file.html` |
| `mput` | Uploads **M**ultiple files (supports wildcards). | `ftp> mput *.bak` |
| `binary` | Sets transfer mode to **binary** (required for non-text files like ZIPs, EXEs). | `ftp> binary` |
| `ascii` | Sets transfer mode to **ASCII** (for text-only files). | `ftp> ascii` |
| `quit` or `bye` | Closes the connection and exits the FTP prompt. | `ftp> quit` |

