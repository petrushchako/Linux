# SFTP user configuration

- Configure user
```sh
adduser tenant1

mkdir -p /var/sftp/tenant1/uploads
chown root:root /var/sftp/tenant1
chmod 755 /var/sftp/tenant1
chown tenant1:tenant1 /var/sftp/tenant4/uploads

echo '
Match User tenant1
	ForceCommand internal-sftp
	PasswordAuthentication yes
	PubkeyAuthentication yes
	AuthenticationMethods publickey,password
	ChrootDirectory /var/sftp/tenant1
	PermitTunnel no
	AllowAgentForwarding no
	AllowTcpForwarding no
	X11Forwarding no' >> /etc/ssh/sshd_config

systemctl restart sshd

-u tenant4 ssh-keygen -t rsa -b 4096 -f /home/tenant1/.ssh/tenant1_key -N ""

mkdir -p /home/tenant1/.ssh
touch /home/tenant1/.ssh/authorized_keys

cat /home/tenant4/.ssh/tenant1_key.pub | tee -a /home/tenant1/.ssh/authorized_keys

chmod 700 /home/tenant1/.ssh
chmod 600 /home/tenant1/.ssh/authorized_keys
chown -R tenant1:tenant1 /home/tenant1/.ssh
```

- Delete user
```sh
deluser --remove-home tenant1
rm -rf /var/sftp/tenant1
vim /etc/ssh/sshd_config
systemctl restart sshd
```

- Test user
```
chmod 600 tenant1_key
sftp -i tenant1_key -P <PORT_NUM> tenant1@<IP_ADDR>
```
