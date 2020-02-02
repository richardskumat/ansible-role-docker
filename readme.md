ansible-role-docker
=========

Installs Docker-ce on Debian 9, 10 and CentOS 7 hosts. Also includes a tasks file for Raspbian,
however I've only tested this role with Raspbian Stretch and Buster.

Requirements
------------

This was tested with:

ansible > 2.9

Role Variables
--------------

```
docker_service_state: 'started'
docker_service_enabled: 'yes'
```

What the state of the docker service should be.

These values define the state of the docker service
handler task in handlers/main.yml.

```
docker_centos_repo_baseurl: 'https://download.docker.com/linux/centos/docker-ce.repo'
```

Repo url to download the repo file from.

```
configure_docker_users: 'false'
```

Configure this role whether to add/remove users
from the docker group. By default, this role
doesn't touch users/group memberships.

When set to true, the role runs docker-users.yml
from tasks.

```
docker_group_name: 'docker'
```

The group name of the group that has write
access to the docker socket.

Default value is docker.

See the [docker post-installation docs](https://docs.docker.com/install/linux/linux-postinstall/) for
more details

```
add_docker_users: []
```

The list of users to add to the docker group.

Default value is blank.

Example values:

```yaml
add_docker_users: [
    - john
    - wick
]
```

```
remove_docker_users: []
```

The list of users to be removed from the docker group.

This value is used a command task(gpasswd -d user group),
so it's not perfect by any means.

Default value is blank.

Example values:

```yaml
remove_docker_users: [
    - john
    - wick
]
```

```yaml
remove_docker_packages: 'false'
```

Whether to run the uninstallation task to remove packages
installed by docker.

Accepted values:

'true' or 'false'

Default value:

'false'

Dependencies
------------

The following packages are required on Debian
based distributions:

lsb-release

This role will attempt to install lsb-release as
a dependency.

Example Playbook
----------------


```yaml
---
- name: Install docker-ce
  hosts: all
  become: 'true'
  roles:
    - role: richardskumat.ansible_role_docker

```


License
-------

GPLv3

Author Information
------------------

Richard Skumat