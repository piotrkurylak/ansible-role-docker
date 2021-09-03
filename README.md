## Role Name: Docker
----------------

Ansible role which allows you to install Docker on Debian systems.

## Requirements
----------------

None.

## Role Variables
----------------

Docker repository URL depending on distro. 
````yaml
docker_repo_url: "https://download.docker.com/linux/{{ ansible_distribution | lower }}"
````

Docker repository variables. You can set up nightly or test release if you want.
````yaml
docker_apt_arch: amd64
docker_apt_release_channel: stable
docker_apt_repository: "deb [arch={{ docker_apt_arch }}] {{ docker_repo_url }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"
````

You can add users which be added to docker group. (Run docker commands without sudo)
````yaml
docker_users: []
````

## Dependencies
----------------

None.

## Example Playbook
----------------

````yaml
    - hosts: all
      become: yes
      roles:
         - docker
````

## License
----------------

MIT / BSD

## Author Information
----------------

Role created by Piotr Kurylak.
