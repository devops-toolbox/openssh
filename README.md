Role Name
=========

openssh: Openssh

[![Build Status](https://travis-ci.org/cmihai-ansible/openssh.svg?branch=master)](https://travis-ci.org/cmihai-ansible/openssh)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.openssh](https://galaxy.ansible.com/devopstoolbox.openssh)

```bash
ansible-galaxy install devopstoolbox.openssh
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
openssh_packages_state: present
openssh_remove_packages: true
openssh_enable_service: true
openssh_enable_selinux: true
openssh_copy_templates: true
openssh_firewall_configure: true
openssh_firewall_rules:
  - service: ssh
  - port: 3389
openssh_users:
  - user: devops
    group: docker
openssh_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install openssh on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: openssh is configured
      import_role:
        name: devopstoolbox.openssh
      vars:
        openssh_packages_state: present
        openssh_remove_packages: true
        openssh_enable_service: true
        openssh_enable_selinux: true
        openssh_copy_templates: true
        openssh_firewall_configure: true
        openssh_firewall_rules:
          - service: ssh
          - port: 3389
        openssh_users:
          - user: devops
            group: docker
        openssh_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: openssh
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
