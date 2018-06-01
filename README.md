Ansible Role: MAVEN
=========

Install and configures Apache maven on RedHat/CentOS and Debian/Ubuntu 

Requirements
------------
Requires ```EPEL``` repository for ```RedHat/CentOS``` machines, you can install the repository using the ```common``` Ansible role.


Role Variables
--------------
To install different version of Apache Maven, change the following variable
```
maven_version: 3.5.3
```

Choose the directory in which Maven will be installed, ```default: /apps``` if undefined. The default directory structure and required packages will be created and installed using the ```common``` Ansible Playbook
```
maven_install_dir: /apps
```

The archive file has to be pre-downloaded and placed in one of the following folders 
```
- /home/$USER/ansible_roles/files
- /home/$USER/ansible_roles/
- /home/$USER/ansible_roles/maven/files
- /home/$USER/ansible_roles/maven/tasks/files
```
The following variable will define the maven archive
```
maven_src_tar: apache-maven-3.5.3-bin.zip
```

Maven Home Environmental variable ```[M2_HOME]``` will be set using the variable, the path depends on the ```maven_install_dir```
```
maven_home: /apps/apache-maven-3.5.3
```

The variable will set the symlink for the installed Maven
```
maven_shared_home: /usr/shared/maven
```

The data directory to store all maven app data
```
maven_repo_dir: /data/maven/repo
```

The following will setup the profile
```
maven_profile_sh: /etc/profile.d/maven.sh
```

Dependencies
------------

skydevops ```common``` Ansible Role is needed, which creates the required directories and also install the required packages.

Example Playbook
----------------

Use the following playbook:

```
- hosts: all
  become: yes
  gather_facts: yes
  roles:
    - role: common

- hosts: test_servers
  become: yes
  gather_facts: yes
  roles:
    - role: sdjava
    - role: maven
```

License
-------

Licensed under the Apache License V2.0. See the [LICENSE file](LICENSE) for details.

Author Information
------------------

This role was created in 2018 by [Shashi Yebbare](https://www.skydevops.co.in/), author of [SkyDevops](https://www.skydevops.co.in/).
