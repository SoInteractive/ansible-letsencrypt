Letsencrypt automation
======================

Role should automatically download and install letsencrypt certificate.
Additionally it will set certificate autorenewal.

Requirements
------------

globally resolvable domain name

Examples
--------

Use it in a playbook as follows:
```yaml
- hosts: all
  become: true
  roles:
    - SoInteractive.letsencrypt
```

Have a look at the [defaults/main.yml](defaults/main.yml) for role variables
that can be overridden.
