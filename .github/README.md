# ans_role_add_user

Ansible role to add a user to a system

[![Release](https://img.shields.io/github/release/digimokan/ans_role_add_user.svg?label=release)](https://github.com/digimokan/ans_role_add_user/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Add a user to a system.
* Optionally set user password (via prompt), if password has never been set.
* Optionally add user to groups.

## Supported Operating Systems

* Any Linux distribution.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_add_user
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Add admin user to system"
         include_role:
           name: ans_role_add_user
         vars:
           user_name: "admin"
           user_groups:
             - "wheel"
   ```

## Role Options

See the role `defaults` file for overridable vars:

  * [defaults/main.yml](../defaults/main.yml)

Define these _optional_ vars for the role:

  * `user_groups`: a _list_ of existing groups to add user to (_NOTE: user will
    be in primary group `user_name` by default_).

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_add_user/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

