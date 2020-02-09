Role Name
=========

ati: Ati

[![Build Status](https://travis-ci.org/cmihai-ansible/ati.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ati)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.ati](https://galaxy.ansible.com/devopstoolbox.ati)

```bash
ansible-galaxy install devopstoolbox.ati
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ati_packages_state: present
ati_remove_packages: true
ati_enable_service: true
ati_enable_selinux: true
ati_copy_templates: true
ati_firewall_configure: true
ati_firewall_rules:
  - service: ssh
  - port: 3389
ati_users:
  - user: devops
    group: docker
ati_selinux_booleans:
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
- name: Install ati on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ati is configured
      import_role:
        name: devopstoolbox.ati
      vars:
        ati_packages_state: present
        ati_remove_packages: true
        ati_enable_service: true
        ati_enable_selinux: true
        ati_copy_templates: true
        ati_firewall_configure: true
        ati_firewall_rules:
          - service: ssh
          - port: 3389
        ati_users:
          - user: devops
            group: docker
        ati_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ati
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
