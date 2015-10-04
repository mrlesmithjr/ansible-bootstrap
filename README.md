Role Name
=========

Initial host configurations (Bootstrap)...Creates user accounts, sets root password, locks down ssh and manages remote ssh pub keys

[![Build Status](https://travis-ci.org/mrlesmithjr/ansible-bootstrap.svg?branch=master)](https://travis-ci.org/mrlesmithjr/ansible-bootstrap)
Requirements
------------

None

Role Variables
--------------

````
---
# defaults file for ansible-bootstrap
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
deploy_ssh_pub_keys:  #defines remote users to add ssh pub keys for either the remote user or adding another users pub key to a remote user for passwordless ssh
  - remote_user: demo_user
    keys:
      - ssh_pub_keys/demo_user.pub
#      - ssh_pub_keys/demo_user_1.pub
#  - remote_user: demo_user2
#    keys:
#      - ssh_pub_keys/demo_user2.pub
enable_deploy_ssh_pub_keys: false  #defines if accounts in deploy_ssh_pub_keys should be managed
reboot: true  # reboot after changing hostname to match inventory_hostname - set to false if you do not want to reboot
root_password:  #define root password for hosts....define here or in group_vars/all
````

Dependencies
------------

None

Example Playbook
----------------

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
