Leptonica Installer
=========

This Ansible role builds and install the latest Leptonica software to the specified system.

This software is not affiliated nor endorsed by the Leptonica.

Requirements
------------

### Managed Node

Currently only Ubuntu is supported, tested on 18.04.

Patches on supporting other OS distributions are welcomed.

Role Variables
--------------

| Variable name | Description  | Default value |
| :-: | :-: | :-: |
| `leptonica_install_scope` | Determine the install scope of the software, only effective when `leptonica_installation_prefix` isn't set to `auto-detected`.  Supported value: `global`, `local`  | `local` |
| `leptonica_installation_prefix` | The installation prefix for the software, or `auto-detected` for auto detection (`/opt/leptonica-_installed_version_` (when `leptonica_install_scope` is `global`), `~/.local/opt/leptonica-_installed_version_` (when `leptonica_install_scope` is `local`)) | `auto-detected` |
| `leptonica_custom_configure_args` | Additional command-line arguments to pass to the build configuration program(configure), each argument should be manually quoted when required, example: `'"CFLAGS=-v" "CXX=/some/c++ compiler"'` | (empty) |
| `leptonica_skip_package_installation` | Skip system update and package installation, this allows installation without superuser privileges.  Supported values: `False`, `True` | `False` |

Example Playbook
----------------

```yaml
- name: Install Leptonica to /opt/leptonica, with `CC=gcc6` as additional build configuration
  hosts: localhost
  roles:
    - role: leptonica_installer
      vars:
        - installation_prefix: /opt/leptonica
        - custom_configure_args: '"CC=gcc6"'

```

License
-------

Creative Commons BY-SA 4.0+

Author Information
------------------

林博仁(Buo-ren, Lin)  
<Buo.Ren.Lin@gmail.com>

