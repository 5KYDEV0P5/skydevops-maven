SDMAVEN
=========

Install and configures Apache maven.

Requirements
------------

```common``` role is the dependency, which will setup the directory structure and install pre-requisites

Role Variables
--------------

```
---
# vars file for maven
maven_version: 3.5.3
maven_install_dir: /apps
maven_src_tar: apache-maven-3.5.3-bin.zip
maven_home: /apps/apache-maven-3.5.3
maven_shared_home: /usr/shared/maven
maven_repo_dir: /data/maven/repo
maven_profile_sh: /etc/profile.d/maven.sh
```

Dependencies
------------

skydevops ```common``` Ansible Role is needed

Example Playbook
----------------

Use the following playbook:

```
- hosts: test_servers
  become: yes
  gather_facts: yes
  roles:
    - role: common
    - role: sdjava
      tags: java
    - role: maven
      tags: maven
```

License
-------

Licensed under the Apache License V2.0. See the [LICENSE file](LICENSE) for details.

Author Information
------------------

Author: Shashi yebbare
