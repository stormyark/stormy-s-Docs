---
title: How to secure your server
draft: false
tags:
  - server
author: stormy
---
### Updates

Updating packages and dependencies:
```shell
sudo apt update && apt upgrade
```

Enable automatic updates for existing packages:
```shell
sudo apt dist-upgrade
```

Enable automatic updates:
```shell
sudo apt install unattended-upgrades
```

```shell
dpkg-reconfigure --priority=low unattended-upgrades
```

---
### User

Create a new user:
```shell
adduser {your-name}
```

> Give it a secure password! Only login via this user not using root! This will be your password to access the server via ssh, so hackers will try to bruteforce.

Add user to sudo group:
```shell
addmod -aG sudo {your-name}
```

---
### SSH

<aside>
💡 While not a comprehensive security measure, changing the default SSH port (which is 22) to a non-standard port can reduce the number of automated attacks. Many automated scripts and bots target default ports. By using a non-standard port, you can avoid many of these attacks.

</aside>

Change ssh port:
```shell
sudo nano /etc/ssh/sshd_config
```

> `# Port 22 → Port 535` | use anything between 0-1023 (Well Known Ports range)

Only use IPv4:

> `AddressFamily any → AddressFamily inet`

Dont let Root login:

> `PermitRootLogin yes → PerminRootLogin no`

Disable password login:

> `# PasswordAuthentication yes → PasswordAuthentication no`

Only apply this when you generated an SSH key!

```shell
sudo systemctl restart sshd
```

---
### Generate SSH key

Generate SSH key pair on the server:

```shell
ssh-keygen -t ecdsa -q -N '' -f {file-name}
```

It will create the files `server-admin` (the private key) and `server-admin.pub` (the public key). The option `-N ''` tells to the command **`ssh-keygen`** to generate a key pair without password.

We want to append the public key to `~/.ssh/authorized_keys`, but first let’s make sure that the directory exists and has propper permissions:

```shell
mkdir -p ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
cat {file-name}.pub >> ~/.ssh/authorized_keys
#rm {file-name}.pub
```

### Login with private key

We want to transfer the private key to our local machine (laptop). We can just copy/paste its content or we can use **`scp`** like this:

```shell
scp -P 22 root@10.11.12.13:~/{file-name} .
chmod 600 {file-name}
```

Now let’s try to login using this private key:

```shell
ssh -i {file-name} root@10.11.12.13
```

To make things easier, let’s create a configuration file on `~/.ssh` **(on the local machine)**:

```shell
touch ~/.ssh/config
chmod 600 ~/.ssh/config

cat >> ~/.ssh/config <<EOF
Host {your-server}
    HostName {ip}
    Port 22
    User root
    IdentityFile ~/.ssh/{file-name}.key
    IdentitiesOnly yes
EOF

mv server-admin ~/.ssh/{file-name}.key
chmod 600 ~/.ssh/{file-name}.key
```

---
### Firewall

Install Firewall ufw (Uncomplicated Firewall):

```shell
sudo apt install ufw
```

Allow ssh port:

```shell
sudo ufw allow 22
```

Enable ufw:

```shell
sudo ufw enable
```

---
### Fail2ban

<aside>
💡 Fail2ban is an open-source intrusion prevention software framework designed to protect computer servers from brute-force attacks. It works by monitoring log files and banning IP addresses that show malicious signs, such as multiple failed login attempts, seeking for exploits, etc.
</aside>

Install Fail2ban:

```shell
sudo apt install -y fail2ban
```

Check status:

```shell
fail2ban-client status
```

```shell
fail2ban-client status sshd
```

---
### Source

[https://docs.lugbz.org/server-setup.html](https://docs.lugbz.org/server-setup.html)