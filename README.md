# Ansible Install Linux

This repository contains a list of packages for Fedora, Debian, and Ubuntu distributions. It only contains a long list of packages for some GNU/Linux distributions.

## List

- [Ubuntu Packages](ubuntu-software.md)

## Ubuntu 20.04

## Packages Extra no Included

- [zoom](https://zoom.us/download#client_4meeting)
- [slack](https://slack.com/intl/en-bo/downloads/linux)
- [brave](https://brave.com/download/)
- [aws](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#cliv2-linux-install)
- [awless](https://github.com/wallix/awless/releases)
- [helm](https://helm.sh/docs/intro/install/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
- [terraform](https://www.terraform.io/downloads.html)
- [packer](https://learn.hashicorp.com/tutorials/packer/get-started-install-cli)
- [assume-role](https://github.com/remind101/assume-role)

## List of Repositories

### Ubuntu

- Ubuntu Official
- MariaDB
- VirtualBox
- Docker CE
- Typora
- VSCode
- NodeJS
- Yarn
- Terraform
- Postgresql
- Kubectl

## Pre-Requisites

First we must manually execute the following commands on the computer where the installation will take place:

```bash
$ sudo apt update
$ sudo apt install -y openssh-server
$ sudo systemctl enable --now sshd.service
```

Then we must copy a public SSH key on the computer where the installations will be executed:

```bash
$ ssh-copy-id -o PubkeyAuthentication=no -i ~/.ssh/demo-ssh.pub user_name@ip_address_or_localhost
```

This ansible poroject is for automatic install on post-installation for Ubuntu Operating System.

## Config Files and replace values

The project have three playbooks:

- ubuntu-base-repos.yml
- ubuntu-desktop.yml
- ubuntu-security.yml

## Versions

- XFCE: 4.14.3
- Ubuntu: 20.04 Focal
- Ansible: 2.9

## Commands

First we are located on the route:

```bash
$ cd ansible-ubuntu
```

Execution order:

1. **ubuntu-base.yml**:

```bash
$ ansible-playbook ubuntu-base-repos.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

2. **ubuntu-desktop.yml**:

```bash
$ ansible-playbook ubuntu-desktop.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

3. **ubuntu-security.yml**:

```bash
$ ansible-playbook ubuntu-security.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```
