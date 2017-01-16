NodeJS
======

[![Build Status](https://travis-ci.org/jebovic/ansible-nodejs.svg?branch=master)](https://travis-ci.org/jebovic/ansible-nodejs) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.nodejs-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/nodejs)

Install and configure NodeJS

This role is a part of my [OPS project](https://github.com/jebovic/ops), follow this link to see it in action. OPS provides a lot of stuff, like a vagrant file for development VMs, playbooks for roles orchestration, inventory files, examples for roles configuration, ansible configuration file, and many more.

Compatibility
-------------

Tested and approved on :

* Debian jessie (8+)
* Ubuntu Trusty (14.04 LTS)
* Ubuntu Xenial (16.04 LTS)

Role Variables
--------------

```yaml
# nodejs install configuration
nodejs_apt_key_url: "https://deb.nodesource.com/gpgkey/nodesource.gpg.key"
nodejs_apt_repositories:
  - "deb https://deb.nodesource.com/node_{{ nodejs_major_version }} {{ ansible_distribution_release | lower }} main"
  - "deb-src https://deb.nodesource.com/node_{{ nodejs_major_version }} {{ ansible_distribution_release | lower }} main"
nodejs_packages:
  - nodejs
nodejs_major_version: 6.x # choose between 4.x and 6.x

# npm basic configuration
nodejs_npm_config_path: /usr/local/lib/npm
nodejs_npm_config_unsafe_perm: "false"
nodejs_npm_user: root
nodejs_npm_usergroup: root
nodejs_npm_packages:
  - name: npm
    version: latest
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - { role: jebovic.nodejs }
```

Example : config
----------------

```yaml
# Customize NodeJS version and user
nodejs_major_version: 4.x
nodejs_npm_user: me
nodejs_npm_usergroup: me
```

Tags
----

* nodejs_config : only update config
* nodejs_npm_addons : only install additional npm packages

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
