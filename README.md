# ansible-role-boundary-client

[![molecule](https://github.com/diodonfrost/ansible-role-boundary/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-boundary/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.boundary-660198.svg)](https://galaxy.ansible.com/diodonfrost/boundary)

This role provide a compliance for install Hashicorp Boundary cli and desktop on your target host.

## Requirements

This role was developed using Ansible 2.5 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.boundary_client` to install the role on your system.
*   Ansible >= 2.8
*   Python >= 2.7

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
---
# defaults file for diodonfrost.boundary

# Install boundary cli
# Default: true
install_cli: true

# Define boundary cli version to install
# Possible values: https://releases.hashicorp.com/boundary/index.json
# Default: latest
boundary_cli_version: latest

# Define where to download boundary cli package url
# Default: use local system path defined in Ansible vars/*.yml
boundary_cli_pkg_url: "{{ default_boundary_cli_pkg_url }}"

# Define where to install boundary cli binary
# Default: use local system path defined in Ansible vars/*.yml
boundary_cli_bin_directory: "{{ default_boundary_cli_bin_directory }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy boundary role in a localhost and installing the latest version of boundary.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.boundary
```

This role can also install a specific version of boundary.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: ansible-role-boundary
      vars:
        boundary_cli_version: 0.13.1
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://www.virtualbox.org/) (if you test windows system)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create ubuntu 22.04 instance
molecule create

# Apply role on ubuntu 22.04 instance
molecule converge

# Launch tests on ubuntu 22.04 instance
molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd

# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2023 by diodonfrost.
