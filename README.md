# Ansible Role: rstudio-package-manager

[![CI](https://github.com/Appsilon/ansible-rstudio-package-manager/workflows/CI/badge.svg)](https://github.com/Appsilon/ansible-rstudio-package-manager/actions/workflows/ci.yml)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-appsilon.rstudio_package_manager-blue.svg)](https://galaxy.ansible.com/appsilon/rstudio_package_manager/)

Set up (the latest version of) [RStudio Package Manager](https://www.rstudio.com/products/package-manager/) in Debian-like systems.

## Requirements

* `curl` (will be installed)
* `r-base` (will not be installed)

## Role Variables

* `rstudio_package_manager_version` [default: `2021.09.0-1`]: Version to install
* `rstudio_package_manager_install` [default: `[]`]: Additional packages to install (e.g. `r-base`)
* `rstudio_package_manager_www_port` [default: `4242`]: The port you want RStudio Package Manager to listen on
* `rstudio_package_manager_config`: A map of maps containing RStudio Package
   Manager configuration. Gets converted into Golang's configuration file (GCFG)
   and is writted on down to `rstudio-pm.gcfg`. See
   [./defaults/main.yml](./defaults/main.yml) for an example.
* `rstudio_package_manager_config_override` [default: `""`]: If you know what you're doing, you can override whole `rstudio-pm.gcfg` config.

* `rstudio_package_manager_license`: If specified, RStudio Package Manager will attempt to activate the supplied license key.

For the rest of the default variables, see
[./defaults/main.yml](./defaults/main.yml).

## Dependencies

None

## Example

```yaml
---
- hosts: all
  roles:
    - rstudio-package-manager
```

## License

MIT

## Author Information

Oleksandr Ponomarov. Inspired by (aka shamelessly stolen from) [ansible-rstudio-server](https://github.com/Oefenweb/ansible-rstudio-server).
