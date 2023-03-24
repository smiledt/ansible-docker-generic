# Docker-Generic

A role to spin up a new docker container. The goal is for this role to be generic enough that a container can easily be specified using variables. This is only being published for integration into my AWX instance. 

## Requirements

Docker needs to be installed and configured on the server. 

## Required Variables

Required variables are listed here, along with default example values. Any of these defaults can be overwritten by using the vars role directory. 

    docker_name: Hello World

This is the name of the container. 

    docker_image: hello-world

The image of the container.

## Optional Variables

The following variables are optional, but some containers will require them. Random example values displayed.

    docker_ports:
      - 80:80
      - 443:443

These are the exported ports of the container.

    docker_volumes:
    - "/opt/app:/config"
    - "/opt/Application Support/Logs:/applogs"
    - "/opt/test:/test"

These are any volumes mounted in the container. The relevant directories will be created if they do not already exist. 

    docker_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

This is a dictionary of extra environment variables for the container. 

    docker_additional_options:
      restart_policy: unless-stopped

Any additional options for the container.

## Dependencies

None.

## Example Playbook
    - name: Deploy the Plex Container.
      hosts: plex
      become: true
      roles:
      - role: docker-generic

### License

MIT

### Author Information

Derek Smiley - Network Analyst, avid homelabber, and aspiring Systems Administrator.

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/