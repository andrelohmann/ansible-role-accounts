accounts
=========

[![Build Status](https://travis-ci.org/andrelohmann/ansible-role-accounts.svg?branch=master)](https://travis-ci.org/andrelohmann/ansible-role-accounts)

Deploy users and public keys to your machines.

Role Variables
--------------

Create a list with all users that need to be created on the system. You can set every parameter for the user that is available from http://docs.ansible.com/ansible/user_module.html. Also you can set every parameter (exept "user") for the key that is available from http://docs.ansible.com/ansible/authorized_key_module.html. The optional array "accounts_sshd_configs" allows to set sshd_config parameters.

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

If you need additional users on host base, you can set an additional list **accounts_host_users**.

    accounts_host_users:
    - name: __USERNAME__
      uid: __UID__
      state: present
      keys:
      - key: ssh-rsa AAA...
        state: present

Example Playbook
----------------

    - hosts: accounts
      roles:
         - { role: andrelohmann.accounts }

License
-------

MIT

Author Information
------------------

https://github.com/andrelohmann
