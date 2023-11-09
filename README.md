ECGALAXY nodejs
===============

Ansible role that installs Node.js.

Requirements
------------

- On Ubuntu, the `gpg-agent` command, which can be provided by `ecgalaxy.common_packages`.

Role Variables
--------------

- `nodejs_version`: Sets the Node.js version to install ("16.x", "18.x", "20.x", etc).

The default version is 20.x.

Version numbers from Nodesource: https://github.com/nodesource/distributions.

Node.js 18 and 20 on Amazon Linux 2 are supported, using pre-built binaries from:
https://code.europa.eu/ecgalaxy/amazonlinux2-nodejs

Dependencies
------------

- optional: ecgalaxy.bootstrap
- optional: ecgalaxy.common_packages

Example Playbook
----------------

    - hosts: all
      roles:
        - ecgalaxy.bootstrap
        - ecgalaxy.common_packages
        - ecgalaxy.nodejs

One-liner
---------

    bash <(curl -s https://code.europa.eu/-/snippets/1/raw/main/ansible-role.sh) ecgalaxy.nodejs

See [ansible-role](https://code.europa.eu/-/snippets/1) for instructions.

Please verify the script integrity first.

License
-------

Copyright the European Union 2022.

Licensed under the EUPL-1.2 or later.

Author Information
------------------

ECGALAXY team.

NOTE: This role is based on [original work by Jeff Geerling](https://github.com/geerlingguy/ansible-role-nodejs).
