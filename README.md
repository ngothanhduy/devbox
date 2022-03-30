# SANDBOX

This is a script to set up a linux sandbox to learn DevOps things on your Windows machine.

---

## Prerequisite

[Vagrant](https://www.vagrantup.com/)

[Virtual box](https://www.virtualbox.org/wiki/Downloads)

[Git](https://git-scm.com/)

---

## 💻 Setup

Generate ssh-key on your Windows machine:

`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

Copy ssh public key to your Git tool on the web browser. You will need to check how to add this key to it on their guidance (Github, Bitbucket,...)

`cat ~/.ssh/id_rsa.pub`

Up your sandbox and waiting:

`vagrant up`

SSH into your sandbox and do some config:

`vagrant ssh`
`git config --global user.name "your_name"`
`git config --global user.email "your_email@example.com"`

---

## Start coding and drink ☕