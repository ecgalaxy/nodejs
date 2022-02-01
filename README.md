ECGALAXY nodejs
=======================

Ansible role that installs Node.js.

Requirements
------------

None.

Role Variables
--------------


- `nodejs_version` - Set the version of Node.js to install ("12.x", "13.x", "14.x", "15.x", etc.). Version numbers from Nodesource: https://github.com/nodesource/distributions.

Dependencies
------------

- ecgalaxy.common_packages

Example Playbook
----------------

    - hosts: all
      roles:
        - ecgalaxy.nodejs

License
-------

Copyright the European Union 2022.

Licensed under the EUPL-1.2 or later.

Author Information
------------------

ECGALAXY team.

NOTE: This role is based on [original work by Jeff Geerling](https://github.com/geerlingguy/ansible-role-nodejs).
