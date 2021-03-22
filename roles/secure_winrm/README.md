Role Name
=========

Role Name: ctxcommunity.common.secure_winrm

This role removes the unsecure port and Basic authentication for WinRM

Requirements
------------

WinRM over HTTPS needs to be preconfigured

Role Variables
--------------

Dependencies
------------

No dependencies.

Example Playbook
----------------

    - hosts: servers
      roles:
         - ctxcommunity.common.secure_winrm

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
