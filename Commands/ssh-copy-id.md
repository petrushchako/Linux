# SSH-COPY-ID COMMAND

## Description:
`ssh-copy-id` is a command-line utility that simplifies the process of securely copying a user's public SSH key to a remote server's authorized_keys file. This enables passwordless authentication for SSH connections, improving security and convenience.

## Syntax:

`ssh-copy-id [options] [user@]hostname`


## Options:
- `-i <identity_file>`: Specifies the identity file (private key) to use.
- `-p <port>`: Specifies the port to connect to on the remote host.
- `-f`: Force mode, overwrites any existing keys in the remote host's authorized_keys file.
- `-h`: Display usage information and exit.

## Example:
To copy the public SSH key of the current user to a remote server:


`ssh-copy-id user@remote_host`


## Usage:
1. Ensure that you have generated an SSH key pair using `ssh-keygen`.
2. Run `ssh-copy-id` followed by the username and hostname of the remote server.
3. Enter the password for the remote user when prompted.
4. The public key will be added to the `~/.ssh/authorized_keys` file on the remote server, allowing passwordless SSH access.

## Notes:
- `ssh-copy-id` relies on SSH for secure copying of keys. Ensure SSH access is enabled on both local and remote machines.
- If you specify a custom port using the `-p` option, ensure the SSH daemon on the remote server is listening on that port.
- Always verify the fingerprint of the remote server before accepting the connection to prevent man-in-the-middle attacks.
