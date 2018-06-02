ovv.borg
=========

[![Build Status](https://travis-ci.org/ovv/ansible-role-borg.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-borg)

Ansible role to install and configure [borg backup](https://borgbackup.readthedocs.io/en/stable/).

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/ovv/ansible-role-borg.git ovv.borg
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/ovv/ansible-role-borg.git ovv.borg
```

Role Variables
--------------

* `borg_users`: Lift of users.
    `name`: Username.
    `keys`: List of the user public ssh keys.
* `borg_home`: Path for the backup user home (defaul to `/home/backup`).

Example Playbook
----------------

```yml
---
- hosts: localhost
  vars:
    borg_home: /var/backup
    borg_users:
      - name: ovv
        keys:
          - "{{ lookup('file', 'home/ovv/.ssh/id_rsa.pub') }}"
  roles:
    - ansible-role-borg
```

License
-------

MIT
