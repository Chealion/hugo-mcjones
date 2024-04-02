
---
title: "Misc Ansible Snippets"
date: 2024-02-01 21:26:22
lastmod: 2024-02-01 21:32:09
categories: ['ansible', 'snippet']
draft: false
---


# Misc Ansible Snippets

## Ad Hoc Commands
```
ansible -m ping all
ansible -m command -a whoami all
ansible -m command -a "uname -r" all
```
## Serial
Serial can be used to trigger numbers of hosts as part of a playbook:

Doing 3 at a time:
```
- hosts: all
serial: 3
```

Staggered across 10 nodes:
```
- hosts: all
serial:
  - 1
  - 3
  - 6
```
Related: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_strategies.html
## Forks
In `ansible.cfg`:
```
[defaults]
forks=40
```
Max number of connections when running
Related: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_strategies.html


<!-- #public #ansible #snippet -->

<!-- {BearID:B08360EC-2226-45B4-88D8-4463B7BBEA01} -->
