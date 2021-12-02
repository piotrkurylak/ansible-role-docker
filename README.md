## Role Name: Docker

Ansible role which allows you to install Docker & Docker Compose on Debian systems.

## Requirements

None.

## Role Variables

Docker repository URL depending on distro. 
````yaml
docker_repo_url: "https://download.docker.com/linux/{{ ansible_distribution | lower }}"
````

Docker repository variables. You can set up nightly or test release if you want.
````yaml
docker_apt_arch: amd64
docker_apt_release_channel: stable
docker_apt_keyring_path: signed-by=/usr/share/keyrings/docker-archive-keyring.gpg
docker_apt_repository: "deb [arch={{ docker_apt_arch }} {{ docker_apt_keyring_path }}] {{ docker_repo_url }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"
docker_compose_repo_url: "https://github.com/docker/compose/releases/download/{{ docker_compose_version }}/docker-compose-{{ ansible_system }}-{{ ansible_architecture }}"
````

Docker Compose version. You can change as you need, for now current stable version is 1.29.2
````yaml
docker_compose_version: "1.29.2"
````

Docker Compose destination path.
````yaml
docker_compose_dest_path: "/usr/local/bin/docker-compose"
````


You can add users which be added to docker group. (Run docker commands without sudo)
````yaml
docker_users: []
````

## Dependencies

None.

## Example Playbook

````yaml
    - hosts: all
      become: yes
      roles:
         - ansible-role-docker
````

## License

MIT / BSD

## Author Information

Role created by Piotr Kurylak.
