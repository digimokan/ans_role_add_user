# ans_role_config_user

Ansible role to add a user to the system and configure user account.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_user.svg?label=release)](https://github.com/digimokan/ans_role_config_user/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Add a user to the system.
* If defined, set user password.
* Check that user _has_ set a password at some point.
* Set user's primary group.
* Set additional groups that user is a member of (note: groups must exist).
* Optionally, on user creation, create a home dir for user.

## Supported Operating Systems

* Ubuntu
* Arch Linux
* FreeBSD

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_user
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
       - name: "Add and configure user 'admin'"
         ansible.builtin.include_role:
           name: ans_role_config_user
         vars:
           cfg_user_name: "admin"
           cfg_user_primary_group: "admin"
           cfg_user_groups:
             - "wheel"
           cfg_user_create_home_dir_in_existing_filesystem: false
           cfg_user_path_to_home_dir: "/home/admin"
           cfg_user_comment: "admin"
   ```

## Role Options

Dependencies:

  * [defaults/main/dependencies.yml](../defaults/dependencies.yml)

Settings:

  * [defaults/main/settings.yml](../defaults/settings.yml)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_user/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

