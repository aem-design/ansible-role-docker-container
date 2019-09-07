# Ansible Role: Docker Container

[![Build Status](https://travis-ci.org/aem-design/ansible-role-docker-container.svg?branch=master)](https://travis-ci.org/aem-design/ansible-role-docker-container)

This role for working with containers. Wrapper for Ansible `docker_container` role.
> This role was developed as part of
> [AEM.Design](http://aem.design/)

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

| Name                        	| Required 	| Default                          	| Notes 	|
|-----------------------------	|----------	|----------------------------------	|-------	|
| docker_container_name       	| yes      	|                                  	|       	|
| docker_image                	| yes      	|                                  	|       	|
| docker_image_tag            	| yes      	|                                  	|       	|
|                             	|          	|                                  	|       	|
| docker_container_userid     	|          	| root                             	|       	|
| docker_command              	|          	|                                  	|       	|
| docker_restart_policy       	|          	| unless-stopped                   	|       	|
| docker_links                	|          	| []                               	|       	|
| docker_volumes              	|          	| []                               	|       	|
| docker_published_ports      	|          	| []                               	|       	|
| docker_env                  	|          	| []                               	|       	|
| docker_labels               	|          	| name={{ docker_container_name }} 	|       	|
| docker_container_privileged 	|          	| no                               	|       	|
| docker_registry_images_pull 	|          	| no                               	|       	|
| docker_container_restart    	|          	| no                               	|       	|
| docker_container_state      	|          	| started                          	|       	|
| docker_host                 	|          	| localhost                        	|       	|
| docker_volume_driver        	|          	| local                            	|       	|

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - { role: aem_design.docker_container,
      docker_container_name: "author"
      docker_image: "aemdesign/aem"
      docker_image_tag: "6.5.0"
    }
```

## License

Apache 2.0

## Author Information

This role was created by [Max Barrass](https://aem.design/).