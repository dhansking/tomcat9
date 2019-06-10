Ansible Role: Wildfly
=====================

This role install Tomcat9 (default: v.9.0.21 ) on Centos7 and Ubuntu.

Access from:
- http://ip:8080       

Credentials Manager:
- User: admin
- Pass: password

Versions: 
- v.9.0.21
- v.9.0.20
  
Requirements
------------

This Ansible playbook is meant to be run on a FRESH never used server, virtual machine or container.

Role Variables
--------------

**defaults/main.yml:***
```
tomcat_tomcat_version: '9.0.21'
tomcat_tomcat_admin_password: 'password'
tomcat_tomcat_manager_localhost_only: False
tomcat_tomcat_install: '/opt'
```

**vars/Debian.yml:***
```
tomcat_packages:
  - openjdk-8-jdk
  - unzip
```

**vars/RedHat.yml:***
```
tomcat_packages:
  - java-1.8.0-openjdk
  - unzip
```

Role Templates
==============

```
context.xml.j2
tomcat-users.xml.j2
tomcat_service.j2
```

Dependencies
------------

None.

Example Playbook
----------------

**Example with prompt:**
```
- hosts: "{{ vm }}"
  gather_facts: True

  vars_prompt:
    - name: "vm"
      prompt: "VM"
      private: no

  roles:
    - { role: squintans.tomcat }
```

Playbook Call
=============
```
ansible-playbook -i inventory.yml play.yml
```

License
-------

BSD

Author Information
------------------
This role was created in 2019 by Serafín Quintáns - [squintans](http://www.linkedin.com/in/serafin-quintans/)

