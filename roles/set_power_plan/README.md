Role Name
=========

Role Name: ctxcommunity.common.set_power_plan

This role sets the machines OS power settings.

Requirements
------------

See Role Variables

Role Variables
--------------


Possible Values are:
  high performance  (default) : This sets the OS Power Plan to High Performance
  balanced                    : This sets the OS Power Plan to Balanced
  power saver                 : This sets the OS Power Plan to Power Saver

While the defaults/main.yml file can be modified directly, future updates will
overwrite the defaults/main.yml file.  In addition, many of the roles use the same
variables and could benefit from the variable being set at a high precedence.
The variable smb_location is one such example.

To override the default variable values the best place(s) to accomplish this is
to set the new values in one or more of the following locations:
  host_vars/{hostname.mycompany.com}.yml
  group_vars/{group}.yml
  group_vars/all.yml
  playbook.yml (Best option if you need to import multiple certificates)

Dependencies
------------

No dependencies.


Example Playbook
----------------

    - hosts: servers
      roles:
         - ctxcommunity.common.set_power_plan

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
