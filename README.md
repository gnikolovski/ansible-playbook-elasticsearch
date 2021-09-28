# Ansible Playbook - Elasticsearch

Ansible playbook for deploying Elasticsearch on Ubuntu.

Tested only on Ubuntu 20.04.

Supported Elasticsearch versions are 6.x and 7.x.

Before running this playbook update variables located in the vars/elastic.yml file.

For more information, please check out the following article: https://gorannikolovski.com/blog/deploy-elasticsearch-basic-authentication-using-ansible

## Install roles locally:

```
ansible-galaxy install geerlingguy.htpasswd
ansible-galaxy install geerlingguy.security
ansible-galaxy install geerlingguy.firewall
ansible-galaxy install elastic.elasticsearch
ansible-galaxy install geerlingguy.nginx
```

## Run playbook

### First run:

```
ansible-playbook playbook.yml \
  --limit elastic-001 \
  --extra-vars "@vars/elastic.yml" \
  --extra-vars "ansible_user=root ansible_ssh_port=22 ansible_python_interpreter=/usr/bin/python3"
```

### All subsequent runs:

```
ansible-playbook playbook.yml \
  --limit elastic-001 \
  --extra-vars "@vars/elastic.yml" \
  --extra-vars "ansible_user=VALUE_OF_server_user ansible_ssh_port=VALUE_OF_security_ssh_port ansible_python_interpreter=/usr/bin/python3" \
  --ask-become-pass
```

## Author Information

This playbook was created in 2021 by [Goran Nikolovski](https://gorannikolovski.com/).
