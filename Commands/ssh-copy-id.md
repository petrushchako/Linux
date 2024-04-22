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
