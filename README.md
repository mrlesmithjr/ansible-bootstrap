Role Name
=========

Initial host configurations (Bootstrap)...Security, SSH, etc.

[![Build Status](https://travis-ci.org/mrlesmithjr/ansible-bootstrap.svg?branch=master)](https://travis-ci.org/mrlesmithjr/ansible-bootstrap)
Requirements
------------

None

Role Variables
--------------

````
---
reboot: true  # reboot after changing hostname to match inventory_hostname - set to false if you do not want to reboot
root_password: []  #define root password for hosts....define here or in group_vars/all
````

Dependencies
------------

None

Example Playbook
----------------

Example Playbook
----------------
#### Galaxy
-----------
    - hosts: servers
      roles:
         - mrlesmithjr.bootstrap
         - mrlesmithjr.users
#### GitHub
-----------
    - hosts: servers
      roles:
        - ansible-bootstrap
        - ansible-users

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
