Letsencrypt automation
======================

Role should automatically download and install letsencrypt cerificate.
Additionally it will set cerificate autorenewal.

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
    - letsencrypt
```

Have a look at the [defaults/main.yml](defaults/main.yml) for role variables
that can be overridden.
