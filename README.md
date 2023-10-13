# Ansible Sample Collection

Use this with:

- <https://github.com/egandro/ansible-tutorial>

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

## initial collection setup

```bash
ansible-galaxy collection init egandro.ansible_tutorial_collection
```

- open `galaxy.yml` add change according to your needs

## new role

```bash
ansible-galaxy init --init-path roles roleXXX
```

## use the collection

- create a `./collections/requirements.yml` file in your project

```yml
#  ansible-galaxy install -r ./collections/requirements.yml --force
---
collections:
  - name: https://github.com/egandro/ansible-tutorial-collection.git
    type: git
    version: main
```

Sample Playbook

```yml
# ansible-playbook hello-world.yml
---
- name: sample book
  hosts: localhost
  gather_facts: false
  connection: local

  roles:
    # full namespace of the role
    - role: egandro.ansible_tutorial_collection.hello_world
      vars:
        my_var: foo
```
