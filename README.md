# Ansible Role: NFS

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-nfs.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-nfs)

Installs NFS utilities on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    nfs_exports: []

A list of exports which will be placed in the `/etc/exports` file. See Ubuntu's simple [Network File System (NFS)](https://help.ubuntu.com/14.04/serverguide/network-file-system.html) guide for more info and examples. (Simple example: `nfs_exports: { "/home/public    *(rw,sync,no_root_squash)" }`).

## Dependencies

None.

## Example Playbook

    - hosts: db-servers
      roles:
        - { role: geerlingguy.nfs }

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
