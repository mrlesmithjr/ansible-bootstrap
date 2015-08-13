Role Name
=========

Initial host configurations (Bootstrap)
Creates user accounts, sets root password, locks down ssh

[![Build Status](https://travis-ci.org/mrlesmithjr/ansible-bootstrap.svg?branch=master)](https://travis-ci.org/mrlesmithjr/ansible-bootstrap)
Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

````
create_local_users: true  #defines creating local user accounts on hosts
# To generate passwords use (replace P@55w0rd with new password).... echo "P@55w0rd" | mkpasswd -s -m sha-512
create_users:  #defines user accounts to setup on hosts....define here or in group_vars/all
  - user: demo_user  #define username
    authorized_keys: ''
    comment: 'Demo user'  #define a comment to associate with the account
    generate_keys: false  #generate ssh keys...true|false
    home: ''  #define a different home directory... ''=/home/username
    pass: demo_password  #define password for account
    setup: false  #true=creates account|false=removes account if exists...true|false
    shell: ''  #define a different shell for the user
    sudo: false  #define if user should have sudo access...true|false
    system_account: false  #define if account is a system account...true|falseinstall_fail2ban: false
reboot: true  # reboot after changing hostname to match inventory_hostname - set to false if you do not want to reboot
root_password:  #define root password for hosts....define here or in group_vars/all
````

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: mrlesmithjr.bootstrap }

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
