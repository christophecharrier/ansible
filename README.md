# Ansible Playbook for SIS-Deployment Team


Documentation Ansible:
http://docs.ansible.com/ansible/playbooks_best_practices.html


To launch your playbook:

Used a playbook file to launch: 
    
    ansible-playbook -i Inventory_File playbook.yml
    
Options to launch a playbook:

| command        | Description                                      |
|:---------------|:-------------------------------------------------|
| -f              | specify number of parallel processes to use |
| -l              | further limit selected hosts to an additional pattern|
| --list-hosts    | outputs a list of matching hosts; does not execute anything else|
| --list-tags     | list all available tags|
| --list-tasks    | list all tasks that would be executed|
| --syntax-check  | perform a syntax check on the playbook, but do not execute it|
| -t              | only run plays and tasks tagged with these values|
| -v              | verbose mode (-vvv for more, -vvvv to enable connection debugging)|


Ansible playbook works with multiple roles:

- Apache
- Artifactory
- Buildslave
- Cortex
- Docker
- System
- Testslave

In each roles, there are several tasks with specifics tags.

You can launch an action (task) on a specific role by calling a Tag or several tags


### *APACHE*

#### TAGS:

* certificat: request to generate XX.key & XX.csr files



### *ARTIFACTORY* 

#### TAGS:

* arti-conf: Deploy default config file on ARTIFACTORY
* arti-restart: Artifactory restart
* arti-http: Deploy default config http on ARTIFACTORY
* repo-install-artifactory: Download & install repo bintray artifactory
* arti-tomcat: Install manager for tomcat and deploy configuration files



### *BUILDSLAVE*

#### TAGS:

* slave_fleet_id: Get slave's Fleet ID
* slave-shutdown-meta: shutdown buildslave with meta capability
* slave-shutdown-micro: shutdown buildslave with micro capability
* slave-stop-wui-meta:
* slave-stop-wui-micro:
* slave-gracefull-only:
* slave-stop-fleet-meta:
* slave-stop-fleet-micro:
* slave-start-fleet-meta:
* slave-start-fleet-micro:
* slave-start-check-meta:
* slave-start-check-micro:
* slave-start-meta:
* slave-start-micro:
* slave-workdir-clean:
* slave-workdir-clean-autolint:



### *CORTEX*

#### TAGS:

* archi: Deploy cortex architecture (Admin Users, create Data Directory, deploy git repositories)
* setup_hostname: Setup Hostname
* setup_root_cortex: Setup root user
* config_ssh: Setup ssh config



### *DOCKER*

#### TAGS:

* docker-rm-ct: Removing all containers
* docker-clean-img: Removing abandoned images
* cmd-docker: This task can be used to execute a command in a container, using either nsenter or docker exec. This task need to know the "Method" : "nsenter" or "exec".
* docker_install: Install docker for Ubuntu 14.04
* docker-rm-img: Removing all images



### *SYSTEM*

#### TAGS:

* btrfs_clean: Clean BTRFS (Balance)
* install_acl: Install ACL capability on ubuntu1404
* install_ansible: Install ANSIBLE tool and file configuration
* install_postfix: Install POSTFIX and configuration file
* krb5: Remove old file krb5.conf and add a new configuration
* nsenter: Install nsenter and add nse function on .bashrc
* reboot: restart server
* update: Update/Upgrade for Debian/Ubuntu/Red-Hat/Fedora/CentOs Distribution



### *TESTSLAVE*

#### TAGS:

* nfs_t: Add nfs mount point on testslave machines, modify fstab, mount a new filesystem and test.
