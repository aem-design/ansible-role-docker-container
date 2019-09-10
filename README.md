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
| docker_container_privileged 	|          	| false                            	|       	|
| docker_registry_images_pull 	|          	| false                            	|       	|
| docker_container_restart    	|          	| false                            	|       	|
| docker_container_state      	|          	| started                          	|       	|
| docker_host                 	|          	| localhost                        	|       	|
| docker_volume_driver        	|          	| local                            	|       	|

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: aem_design.docker_container
      debug_hide: false
      vars:
        docker_container_name: "author"
        docker_image: "aemdesign/aem"
        docker_image_tag: "6.5.0"
        docker_published_ports: [
          "0.0.0.0:8080:8080/tcp",
          "0.0.0.0:58242:58242/tcp",
          "0.0.0.0:57345:57345/tcp"
        ]
        docker_volumes: [
          "author-repository:/aem/crx-quickstart/repository:z",
          "author-logs:/aem/crx-quickstart/logs:z",
          "author-backup:/aem/backup:z"
        ]
        docker_env:
          TZ: "Australia/Melbourne"
          AEM_JVM_OPTS: -server -Xms1024m -Xmx1024m -XX:MaxDirectMemorySize=256M -XX:+CMSClassUnloadingEnabled
            -Djava.awt.headless=true -Dorg.apache.felix.http.host=0.0.0.0
          AEM_START_OPTS: "start -c /aem/crx-quickstart -i launchpad -p 8080 -a 0.0.0.0 -Dsling.properties=conf/sling.properties"
          AEM_RUNMODE: "-Dsling.run.modes=author,crx3,crx3tar,nosamplecontent"
```

## License

Apache 2.0

## Author Information

This role was created by [Max Barrass](https://aem.design/).