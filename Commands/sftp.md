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


<br>


## Docker excercise
This exercise shows how to configure an isolated **SFTP** server instance locally using Docker, allowing you to practice the secure `sftp` and `scp` commands. We will use a dedicated SSH server image for maximum compatibility with the SFTP protocol.

### **1. Configure & Run the Server (SSH/SFTP)**

Use the `panubo/sshd` image and map the standard SSH port **22** to port **2222** on your local machine to avoid conflicts with your host's primary SSH daemon.

**Required Command:**

```bash
mkdir -p ~/sftp_test_data
docker run -d \
  --name sftp-exercise-server \
  -p 2222:22 \
  -e SSH_USERS="alex:alex123:1000" \
  -v ~/sftp_test_data:/home/devuser/upload \
  panubo/sshd
```

| Credentials | Port | Host Address |
| :--- | :--- | :--- |
| **Username** | `alex` | `127.0.0.1` |
| **Password** | `alex123` | |
| **Local Port** | `2222` | |

### **2. Practice the Secure Transfer Commands**
Use the hostname `127.0.0.1` and the specific local port (`-P 2222`) to test your secure file transfer commands.

#### **A. Using the Interactive SFTP Client**

```bash
sftp -P 2222 alex@127.0.0.1
```

Once connected, practice commands like `put`, `get`, `ls`, and `bye`.

```sftp
sftp> ls upload
sftp> put local_file.txt upload/
sftp> get upload/remote_file.zip
sftp> bye
```

#### **B. Using the Non-Interactive SCP Client**
For quick, one-off transfers (no interactive prompt).

**Upload (Local to Remote):**
```bash
scp -P 2222 local_file.txt alex@127.0.0.1:upload/
```

**Download (Remote to Local):**
```bash
scp -P 2222 alex@127.0.0.1:upload/remote_file.zip .
```

### **3. Cleanup (Stop & Remove)**
```bash
docker stop sftp-exercise-server
docker rm sftp-exercise-server
```