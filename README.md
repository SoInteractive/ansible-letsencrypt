![Logo](https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg)

Ansible role for Let’s Encrypt
==============================

[![Build Status](https://ci.devops.sosoftware.pl/buildStatus/icon?job=SoInteractive/letsencrypt/master)](https://ci.devops.sosoftware.pl/job/SoInteractive/letsencrypt/master)

Role automatically downloads certbot, installs dependencies and creates TLS certificate.
Additionally it sets certificate autorenewal in crontab.

Requirements
------------

- globally resolvable domain name
- open communication on port 80 and 443

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
