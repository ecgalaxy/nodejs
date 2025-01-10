ECGALAXY nodejs
===============

Ansible role that installs [Node.js](https://nodejs.org/) globally.

Requirements
------------

- On Ubuntu, the `gpg-agent` command, which can be provided by `ecgalaxy.common_packages`.

Role Variables
--------------

- `nodejs_version`: Sets the Node.js version to install ("18.x", "20.x", etc),
using the distribution package manager.

The default version is 22.x.

Optionally, in order to install a specific version from a downloadable archive, set the below variables:

- `nodejs_download_url`: The Node.js archive to download (see https://nodejs.org/dist/)
- `nodejs_checksum`: The archive checksum
- `nodejs_install_path`: The path where Node.js will be installed

Those variables must be manually set for RHEL 8 and Node.js > 20.x.

About Node.js 18.x, 20.x, 22.x and 23.x on Amazon Linux 2
---------------------------------------------------------

Official Node.js 18.x, 20.x, 22.x and 23.x pre-built binaries cannot be used on Amazon Linux 2,
due to binary incompatibilities (missing glibc symbol versions).

AWS recommends to build those Node.js versions from source, when using Amazon Linux 2 (AL2).

Pre-built Node.js 18x, 20.x, 22.x and 23.x binaries for Amazon Linux 2 can be found at
https://code.europa.eu/ecgalaxy/amazonlinux2-nodejs/-/packages

They are downloaded by this Ansible role (when executed on AL2),
and saved into the `/opt/nodejs/<nodejs_version>` folder.

Symlinks to the Node.js executables are then created in `/usr/local/bin`.

You may want to update your `$PATH` as well, pointing to the `/opt/nodejs/<nodejs_version>/bin` folder.

Usage with `nvm` has been tested successfully; the command `nvm use system` will correctly point to the "global"
Node.js version (saved into `/opt/nodejs/<nodejs_version>`).

You can also execute this role to globally install 18.x, 20.x, 22.x and 23.x then overwrite the contents of
`~/.nvm/versions/node/v<nodejs_version>` for each, which will allow switching from one version to another
with `nvm use`.

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

To globally install the default Node.js version:

    bash <(curl -s https://code.europa.eu/-/snippets/1/raw/main/ansible-role.sh) ecgalaxy.nodejs

To globally install Node.js 23.x:

    bash <(curl -s https://code.europa.eu/-/snippets/1/raw/main/ansible-role.sh) ecgalaxy.nodejs --extra-vars '{"nodejs_version":"23.x"}'

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
