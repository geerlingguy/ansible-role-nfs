# Ansible Role: NFS

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-nfs.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-nfs)

Installs NFS utilities on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    nfs_exports: []

A list of exports which will be placed in the `/etc/exports` file. See Ubuntu's simple [Network File System (NFS)](https://help.ubuntu.com/14.04/serverguide/network-file-system.html) guide for more info and examples. (Simple example: `nfs_exports: { name: "/home/public" }`).

A complete overview of export options follows below. Only `path` is required, the rest is optional.

| Option                 | Default | Comment |
| :---                   | :---    | :---    |
| `name`                 | -       | The name/comment |
| `subnet`               | *       | The subnet you want to export to |
| `writable`             | `false` | The share cannot be written |
| `insecure`             | `false` | Requests don't have to originate from a port less than IPPORT_RESERVED (1024) |
| `async`                | `false` | Replies to requests before the data is written to disk. This improves performance, but results in lost data if the server goes down |
| `no_subtree_check`     | `false` | Deactivates that every file request is checked to make sure that the requested file is in an exported subdirectory |
| `no_root_squash`       | `false` | Don't convert incoming requests from user root to the anonymous uid and gid |
| `all_squash`           | `false` | Convert incoming requests, from ALL users, to the anonymous uid and gid |
| `anonuid`              | -       | Set anonymous user id to a specific id |
| `anongid`              | -       | Set anonymous group id to a specific id |

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
