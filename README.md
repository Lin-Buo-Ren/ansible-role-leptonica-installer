Leptonica Installer
=========

This Ansible role builds and install Leptonica to the specified system.

Requirements
------------

### Managed Node

Currently only Ubuntu is supported, tested on 18.04.

Patches on supporting other OS distributions are welcomed.

Role Variables
--------------

### Software Installation Prefix (`installation_prefix`)

Determine the installation prefix of Leptonica, or `auto-detected` for the playbook to determine a sane location automatically:

| user  | installation prefix            |
| ----- | ------------------------------ |
| root  | /opt/leptonica-_version_       |
| other | ~/.local/opt/leptonica-version |

### Additional command-line arguments to pass to the build configuration program(configure) (`custom_configure_args`)

Each argument should be manually quoted when required, example: `'"CFLAGS=-v" "CXX=/some/c++ compiler"'`

Example Playbook
----------------

```yaml
- name: Install Leptonica
  hosts: localhost
  roles:
    - leptonica_installer
```

License
-------

Creative Commons BY-SA 4.0+

Author Information
------------------

林博仁(Buo-ren, Lin)  
<Buo.Ren.Lin@gmail.com>

