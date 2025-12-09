# `ftp`

## FTP (File Transfer Protocol) - Legacy & Unencrypted

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


<hr>

## Docker excercise

### **1. Configure & Run the Server (vsftpd)**
Use the `fauria/vsftpd` image, which is pre-configured for easy use. The command maps the control port (21) and a range for **Passive Mode** data transfer (21100-21110) to your host machine's loopback address (`127.0.0.1`).

**Create Docker container**
```bash
mkdir -p ~/ftp_test_data
docker run -d \
  --name ftp-exercise-server \
  -p 21:21 -p 21100-21110:21100-21110 \
  -e FTP_USER=alex \
  -e FTP_PASS=alex123 \
  -e PASV_ADDRESS=127.0.0.1 \
  -e PASV_MIN_PORT=21100 \
  -e PASV_MAX_PORT=21110 \
  -v ~/ftp_test_data:/home/vsftpd \
  fauria/vsftpd
```

| Credentials | Port | Host Address |
| :--- | :--- | :--- |
| **Username** | `alex` | `127.0.0.1` |
| **Password** | `alex123` | |

### **2. Practice the Transfer Commands**
Use the hostname `127.0.0.1` and the credentials above to test your file transfer commands.

| Command | Action |
| :--- | :--- |
| `sftp alex@127.0.0.1` | **Connect** securely (Recommended). |
| `ftp 127.0.0.1` | **Connect** using unencrypted FTP (If available). |
| `put local_file.txt` | **Upload** a file from your local machine. |
| `get remote_file.zip` | **Download** a file from the server. |
| `bye` or `exit` | **Disconnect** and close the prompt. |

### **3. Cleanup (Stop & Remove)**
```bash
docker stop ftp-exercise-server
docker rm ftp-exercise-server
```