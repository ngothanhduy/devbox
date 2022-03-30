# DEVBOX

This is a script to set up a linux devbox to learn DevOps things on your machine.

---

## Prerequisite

[Vagrant](https://www.vagrantup.com/)

[Virtual box](https://www.virtualbox.org/wiki/Downloads)

[Git](https://git-scm.com/)

---

## 💻 Setup

Generate ssh-key on your host machine:

`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

Copy ssh public key to your account settings:

[Github](https://github.com/settings/keys)

[Bitbucket](https://bitbucket.org/account/settings/ssh-keys/)

`cat ~/.ssh/id_rsa.pub`

Up your devbox and waiting:

`vagrant up`

SSH into your devbox and do some config:

`vagrant ssh`

`git config --global user.name "your_name"`

`git config --global user.email "your_email@example.com"`

---

## Start coding and drink ☕
