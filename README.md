Nginx role as a docker container
=========

A general-purpose role to install nginx on a linux server as a docker image with default security configurations.

This role allows the users to import their own configurations files.

Requirements
------------

- [Docker](https://docs.docker.com/engine/install/) - Docker must be installed on the target server.
- [Ansible](https://docs.ansible.com/) - Ansible must be installed to execute the playbook.

Role Variables
--------------


| variable | purpose |
|----- | ---- |
| `nginx_container_name` | Name of the nginx container |
| `nginx_port` | Port exposed by the container |
| `nginx_container_volume` | List of the volumes mounted in the container |
| `nginx_docker_network` | Boolean to setup or not a dedicated docker network |
| `nginx_docker_network_name` | Name of the new docker network (optional)
| `nginx_default_conf_path` | Default path of the `nginx.conf` file |
| `nginx_custom_confs_path` | Path to custom nginx configuration files |

Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

In `inventory/hosts_vars/host`: 

```
nginx_custom_confs_path: "../files/nginx"
nginx_docker_network: true 
nginx_docker_network_name: nginx_shared
```

Playbook example : 
```
- name: Setup nginx proxy
  hosts: my_host 
  become: yes
  roles:
    - role: nginx
      tags: nginx
```

License
-------

BSD


