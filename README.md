# Ansible Sample Modules

Use this with:

- <https://github.com/egandro/ansible-tutorial>

Idea from:

- <https://blog.ruanbekker.com/blog/2022/04/19/publish-and-use-your-ansible-role-from-git/>

## Ansible / Python setup

```bash
sudo apt install python3 -y
sudo apt install python3-pip -y
sudo apt install python3-venv -y
sudo apt install python-is-python3 -y
sudo apt autoremove

sudo apt install sshpass -y # not really needed - only vanilla debian from iso needs this

mkdir -p .python-venv
python3 -m venv .python-venv
. .python-venv/bin/activate
python3 -m pip install --quiet --upgrade pip
pip install --quiet -r requirements.**txt**
```

from here on just use `. .python-venv/bin/activate`

## new role

```bash
ansible-galaxy init --init-path roles roleXXX
# add roleXXX in meta/main.yml
```

## use the roles

- create a `./collections/requirements.yml` file in your project

```yml
#  ansible-galaxy install -r ./collections/requirements.yml --force
---
roles:
  - name: my-common-roles
    src: https://github.com/egandro/common-ansible
    version: main
    scm: git
```
