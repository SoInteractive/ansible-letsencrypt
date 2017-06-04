<a href="https://letsencrypt.org">
    <img src="https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg" alt="letsencrypt logo" title="letsencrypt" align="right" height="60" />
</a>

Ansible Role: Let’s Encrypt
===========================

[![Build Status](https://ci.devops.sosoftware.pl/buildStatus/icon?job=SoInteractive/letsencrypt/master)](https://ci.devops.sosoftware.pl/blue/organizations/jenkins/SoInteractive%2Fletsencrypt/activity) [![License: MIT](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT) [![Ansible Role](https://img.shields.io/ansible/role/18183.svg)](https://galaxy.ansible.com/SoInteractive/letsencrypt/) [![Twitter URL](https://img.shields.io/twitter/follow/sointeractive.svg?style=social&label=Follow%20%40SoInteractive)](https://twitter.com/sointeractive)

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
