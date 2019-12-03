# Ansible Role: NFS

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-nfs.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-nfs)

Installs NFS utilities on RedHat/CentOS or Debian/Ubuntu.

A list of exports which will be placed in the `/etc/exports` file. See Ubuntu's simple [Network File System (NFS)](https://help.ubuntu.com/14.04/serverguide/network-file-system.html) guide for more info and examples.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    nfs_exports: []
    nfs_exports_detailed: []

### Simple behaviour

Simple example: 
```
nfs_exports: 
  - name: "Public"
    path: "/home/public"
    options: "*(rw,sync,no_root_squash)"
```

### Detailed behaviour

With this alternative syntax a more detailed control can be achived. Both behaviours (simple and detailed) can be used at the same time.

Detailed example:
```
nfs_exports_detailed: 
  - name: "Private"
    path: "/home/private"
    options: 
      "*":
        - rw
        - sync
        - no_root_squash
      "10.0.0.1":
        - ro
      "10.0.0.2":
        - rw
        - root_squash
        - all_squash
    state: "directory"
    acls: 
      mode: 0755
      owner: nobody
      group: nobody 
  - name: "removed"
    path: "/var/nfs/removed"
    options:
    state: "absent"
    acls:
```

## Dependencies

None.

## Example Playbook

    - hosts: db-servers
      roles:
        - { role: geerlingguy.nfs }

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
