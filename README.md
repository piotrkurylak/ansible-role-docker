## Role Name: Docker

Ansible role which allows you to install Docker & Docker Compose on Debian/Ubuntu and CentOS/RedHat systems.

## Requirements

None.

## Role Variables

Docker apt repository variables. You can set up nightly or test release if you want. 
````yaml
docker_apt_repo_url: "https://download.docker.com/linux/{{ ansible_distribution | lower }}"
docker_apt_arch: amd64
docker_apt_release_channel: stable
docker_apt_keyring_path: signed-by=/usr/share/keyrings/docker-archive-keyring.gpg
docker_apt_repository: "deb [arch={{ docker_apt_arch }} {{ docker_apt_keyring_path }}] {{ docker_repo_url }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"
````

Docker yum repository variables.
````yaml
docker_yum_gpg_key: "https://download.docker.com/linux/centos/gpg"
docker_yum_repo_url: "https://download.docker.com/linux/centos/docker-ce.repo"
docker_yum_repo_path: "/etc/yum.repos.d/docker-ce.repo"
````

Docker Compose variables. Change if you need specific version, for now current stable version is 1.29.2
````yaml
docker_compose_version: "1.29.2"
docker_compose_repo_url: "https://github.com/docker/compose/releases/download/{{ docker_compose_version }}/docker-compose-{{ ansible_system }}-{{ ansible_architecture }}"
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
