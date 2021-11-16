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

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - ecgalaxy.nodejs

License
-------

EUPL-1.2

Author Information
------------------

ECGALAXY team.

note: This role is inspired to https://github.com/geerlingguy/ansible-role-nodejs.
