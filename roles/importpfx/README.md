Role Name
=========

Role Name: ctxcommunity.common.importpfx

This role imports a certificate in a PFX format from an SMB share location

Requirements
------------

See Role Variables

Role Variables
--------------

become: yes is used therefor the following items need to be defined in a
vaulted password .yml file that is included with the playbook.yml

ansible_become_method: runas
ansible_become_user: { Account with Local Admin Privileges. Can be domain account like DOMAIN\\Automation }
ansible_become_pass: { Password for Administrative Account}

Also the following hash table needs to be placed in a vaulted password .yml file that is included with the
playbook.yml. The following hash table shows how two different certificate can be used and referenced.  Additional
certificates can be added by following the same pattern as show in the example.

certificates:
  wildcard2020:
    certificate_pfx_file: wildcard2020.pfx
    certificate_pfx_password: YourPFXImportPassword
    certificate_pfx_thumbprint: YourCertificateThumbprint
  wildcard2021:
    certificate_pfx_file: wildcard2021.pfx
    certificate_pfx_password: YourPFXImportPassword
    certificate_pfx_thumbprint: YourCertificateThumbprint

The defaults/main.yml contains the following variables and default values:

  smb_location: \\\\file1\\automation
  certificate_smb_location: "{{ smb_location }}\\Certificates"
  certificate_pfx_name: wildcard2020
  certificate_install_state: present

The smb_location variable needs to point to an SMB File Share that the become user
has a minimum of read access.

The certificate_smb_location aggregates the file share location with the folder the
PFX files are stored in.  Some organization my wish to place their certificates on a
different file server and share than what is used for the SMB based software repository (smb_location).
In this case specify the file share and folder location using the certificate_smb_location variable.

For Example:

certificate_smb_location: \\\\myServer\\myShare\\myCertificateFolder

The best place to place this variable override would be in the following locations
depending on the what the variable scope override is required.

  host_vars/{hostname.mycompany.com}.yml
  group_vars/{group}.yml
  group_vars/all.yml
  playbook.yml (Best option if you need to import multiple certificates)

The certificate_install_state variable controls the installation state
for the Windows Role File and Storage Services/File Server

Possible Values are:
  present  (default)  : This will import the Certificate
  absent              : This will remove the Certificate

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

The role only imports one certificate a time. To import multiple certificates
update the variables, as needed, and run the role again with the updated values.

Dependencies
------------

No dependencies.


Example Playbook
----------------

    - hosts: servers
      roles:
         - ctxcommunity.common.importpfx

License
-------

GPL-3.0-only

Author Information
------------------

Joe Shonk
