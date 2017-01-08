accounts
=========

[![Build Status](https://travis-ci.org/andrelohmann/ansible-role-accounts.svg?branch=master)](https://travis-ci.org/andrelohmann/ansible-role-accounts)

Deploy users and public keys to your machines.

Role Variables
--------------

Create an array with all users that need to be created on the system. You can set every parameter for the user that is available from http://docs.ansible.com/ansible/user_module.html. Also you can set every parameter (exept "user") for the key that is available from http://docs.ansible.com/ansible/authorized_key_module.html. The optional array "accounts_sshd_configs" allows to set sshd_config parameters.

    accounts_users:
    - name: __USERNAME__
      uid: __UID__
      state: present
      keys:
      - key: ssh-rsa AAA...
        state: present

    accounts_sshd_configs:
    - key: PermitRootLogin
      value: 'no'
    - key: AuthenticationMethods
      value: 'publickey'

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: accounts
      roles:
         - { role: andrelohmann.ansible-role-accounts }

License
-------

MIT

Author Information
------------------

https://github.com/andrelohmann
