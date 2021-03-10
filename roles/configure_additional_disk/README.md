Role Name
=========

Role Name: ctxcommunity.common.configure_additional_disk

This role is used to initialize, format, and assign a drive letter to additional
disks that are assigned to the machine.

This role only needs to against a newly provisioned machine with a multi-disks configuration.

Requirements
------------

This role assumes the additional disk(s) is/are uninitialized.

If more that one disk needs to be initialize, formatted, and assigned a driver letter then
the best place to define the variables for role is from the playbook.yml

Role Variables
--------------

The defaults/main.yml contains the following variables and default values:

  disk_drive_letter: G
  disk_drive_label: Data
  disk_number: 1

The disk_drive_letter variable controls the drive letter that will be assigned to the
volume. Make sure the drive letter to be used is not already assigned to the machine.

The disk_drive_label variable is the volume name be assigned to the volume. Any Windows OS
limitations on the volume name (i.e. 32 characters max) applies here.

The disk_number variable is the Windows Disk ID that will be configured.

While the defaults/main.yml file can be modified directly, future updates will
overwrite the defaults/main.yml file.  In addition, many of the roles use the same
variables and could benefit from the variable being set at a high precedence.
The variable smb_location is one such example.

To override the default variable values the best place(s) to accomplish this is
to set the new values in one of the following locations:
  host_vars/{hostname.mycompany.com}.yml
  group_vars/{group}.yml
  group_vars/all.yml
  playbook.yml (Best place to define variables if multiple disks need to be configured)

If more that one disk needs to be initialize, formatted, and assigned a driver letter then
the best place to define the variables for role is from the playbook.yml. The role only
configures one disk at a time. To configure multiple disks, update the variables, as
needed, and run the role again with the updated values.

Dependencies
------------

No dependencies.

Example Playbook
----------------

    - hosts: servers
      roles:
         - ctxcommunity.common.configure_additional_disk

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
