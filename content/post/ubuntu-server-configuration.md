+++
author = "Justin Zimmerman"
date = "2015-10-15T08:55:24-04:00"
description = "A listing of important tasks to complete after spinning up your Ubuntu server."
keywords = ["Ubuntu", "Server"]
tags = ["Ubuntu"]
title = "Ubuntu Server Configuration"
topics = ["Ubuntu"]
type = "post"

+++

Below is a listing of important tasks to complete after spinning up your Ubuntu server.

##### SSH login as root

You should have added an ssh key to the instance during creation. SSH into the instance as root with

`ssh root@server_ip_address`

##### Update server to latest patches

```sh
sudo apt-get update
sudo apt-get upgrade
```

Optionally to uninstall old packages

`sudo apt-get autoremove`

##### Create a new user

`adduser user_name`

##### Assign root permission to new user

`gpasswd -a user_name sudo`

##### Login as new user

`su - user_name`

##### Add public key

```sh
mkdir .ssh
chmod 700 .ssh
nano .ssh/authorized_keys
```

Copy your public key into this file

`chmod 600 .ssh/authorized_keys`

##### SSH into the instance as the new user

`ssh user_name@server_ip_address`

##### Edit SSH configuration settings

```sh
sudo nano /etc/ssh/sshd_config
PermitRootLogin no
PermitEmptyPassword no
sudo service ssh restart
```

##### Setup the firewall

Permit ssh on port 22

`sudo ufw allow ssh`

To allow all traffic from a specified IP address

`sudo ufw allow from any_ip_address`

Allow traffic from a specific port

`sudo ufw allow 80/tcp`

Review configuration before enabling

`sudo ufw show added`

Enable the UFW configuration

`sudo ufw enable`

##### Configure NTP

```sh
sudo apt-get update
sudo apt-get install ntp
```

##### Setup swap file

Usually best practice to double amount of RAM for swap file

```sh
sudo fallocate -l xxxG /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
```

##### Install fail2ban

```sh
sudo apt-get update
sudo apt-get install fail2ban
```

##### Edit fail2ban config

```sh
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
```

Update the bantime, findtime, and maxretry settings
Restart the fail2ban service

`sudo service fail2ban restart`
