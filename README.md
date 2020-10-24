# Ansible playbook for initial system configuration of an Ubuntu 20.04 server.


## Description

The following Ansible playbook, will perform an initial system configuration of an Ubuntu 20.04 server.


## Tasks

* System update
* Check if reboot is required
* Create a sudo user
* Add sudo user SSH public key
* Set no password in sudoers file
* Set hostname
* Set Full Qualified Domain Name (FQDN)
* Set timezone
* Install tcpdump, glances and net-tools
* SSH hardening
* Add aliases to .bashrc file

## Ansible version

2.9


## Tested on

Ubuntu 20.04 server (should work on Ubuntu 18.04 as well).


## Prerequisites

a) A remote server with Ubuntu 20.04 already installed<br />
b) An SSH key pair on your laptop or Ansible remote server, with the public key already installed in the remote server<br />
d) Ansible already installed on your laptop or Ansible remote server


## Getting started

a) On your laptop or Ansible remote server, create a working directory


b) In your working directory open a console window


c) Clone github repository

```
git clone https://github.com/jobetinfosec/ansible-ubuntu2004-bootstrap.git
```


d) Switch to playbook directory

```
cd ansible-ubuntu2004-bootstrap
```


e) Open the hosts file

```
nano hosts
```

f) Replace <TEMPORARY_ITEMS> with your own data:

| Item | Instructions | Further info |
| :---: | :---: | :---: |
| `<SERVER_IP>` | replace it with your remote server's IP address |  |
| `<SUDO_USER_NAME>` | replace it with sudo user's name |  |
| `<SUDO_USER_PASSWORD>` | replace it with sudo user's password |  |
| `<SSH_PRIVATE_KEY_NAME>` | replace it with your SSH private key name | For example: ~/.ssh/key_name |


then save and close the file


g) Open the roles/bootstrap/defaults/main.yml file

```
nano roles/bootstrap/defaults/main.yml
```

h) Replace <TEMPORARY_ITEMS> with your own data:

| Item | Instructions | Further info |
| :---: | :---: | :---: |
| `<USER_NAME>` | replace it with sudo user's name | |
| `<SSH_PUBLIC_KEY>` | replace it with sudo user's public key | |
| `<CUSTOM_SSH_PORT>` | replace it with your custom SSH port number | |
| `<HOST_NAME>` | replace it with host name | For example: server |
| `<SERVER_IP>` | replace it with remote server IP address | |
| `<DOMAIN_NAME>` | replace it with server's domain name | For example: domain.com |
| `<TIMEZONE>` | replace it with your current timezone | |


then save and close the file


i) Check if you are able to ping remote server

```
ansible -m ping all
```

You should receive a SUCCESS message


j) Check if any error shows up

```
ansible-playbook bootstrap.yml --check
```


k) Launch installation

```
ansible-playbook bootstrap.yml
```


## Licence

MIT licence

## Author Information

Created by Roberto Jobet (sysadmin@wpsecurity.press).

Don't hesitate to open an Issue if you find any bug or have suggestions.
