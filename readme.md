ansible-role-docker
=========

Installs docker-ce on Debian 9 and 10 hosts. Also includes a tasks file for Raspbian,
however I've only tested this role with Raspbian Stretch.

Requirements
------------

I run the latest ansible, hence I recommend using:

ansible > 2.8

Role Variables
--------------

```
docker_remote_ip: "{{ ansible_default_ipv4.address }}"

Unused var at the moment, but there commented out tasks that would
set up remote access to the docker daemon in the Debian tasks,
but since I don't docker over http/s these are commented out.

docker_remote_port: 2375

See above, unused at this time.

username: qwe

The username for the user that gets added to the docker group.
This value is the username I use on my own devices.

```

Dependencies
------------

None.

Example Playbook
----------------


```
---
- name: Install docker-ce
  hosts: all
  roles:
    - role: richardskumat.ansible-role-docker

```


License
-------

GPLv3

Author Information
------------------

Richard Skumat