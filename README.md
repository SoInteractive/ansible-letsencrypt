<a href="https://letsencrypt.org">
    <img src="https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg" alt="letsencrypt logo" title="letsencrypt" align="right" height="60" />
</a>

Ansible Role: Let’s Encrypt
===========================

[![Build Status](https://travis-ci.org/SoInteractive/ansible-letsencrypt.svg?branch=master)](https://travis-ci.org/SoInteractive/ansible-letsencrypt) [![License: MIT](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT) [![Ansible Role](https://img.shields.io/badge/ansible%20role-SoInteractive.letsencrypt-blue.svg)](https://galaxy.ansible.com/SoInteractive/letsencrypt/) [![GitHub tag](https://img.shields.io/github/tag/sointeractive/ansible-letsencrypt.svg)](https://github.com/SoInteractive/ansible-letsencrypt/tags) [![Twitter URL](https://img.shields.io/twitter/follow/sointeractive.svg?style=social&label=Follow%20%40SoInteractive)](https://twitter.com/sointeractive)

Role automatically downloads certbot, installs dependencies and creates TLS certificate.
Additionally it sets certificate autorenewal in crontab.

# :warning: IMPORTANT NOTICE

THIS PROJECT IS ABANDONED. WE DO NOT ACCEPT ANY NEW ISSUES AND/OR PULL REQUESTS.

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
