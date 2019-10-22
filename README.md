Role Zeenea
===============

<p align="center">
	<img src="img/zeenea.png"/>
</p>

This role is used to install, configure, update and manage zeenea

Requirements
------------

* Certificat & trustore deployed
* Java version 1.8 and more

Inventory
---------

Set your inventory for setting each Zeenea host, example :

```
[ZEENEA]
host1
host2
...
hostn
```` 

Manage Zeenea lifecycle
------------

 * Installing Zeenea ```state=role_zeenea_install```
 * Remove Zeenea ```state=role_zeenea_whole_remove```
 * Installing + Config + Start  ```state=role_zeenea_whole_install```

Role Variables
--------------

Ownership & Mode  variables :

```
role_zeenea_owner: Launcher owner
role_zeenea_group: Launcher group
role_zeenea_user_default_shell: Default shell for the owner
```

JAVA :
```
role_zeenea_java_path: path to JAVA's home
```

Path installer :
```
role_zeenea_install_dir: Directory where Zeenea'll be installed
role_zeenea_repo_host: host where zeenea tarball is hosted
role_zeenea_tarball_path: Where we'll download Zeenea (HTTP mode)
role_zeenea_zeenea_version: Zeenea's release
role_zeenea_tarball_name: Tarball's Zeenea to install
```

Server Variables :
```
role_zeenea_server_tls_port: Zeenea's port
role_zeenea_server_tls_keyManagerPassword: Password to decrypt Keystore
role_zeenea_server_tls_keystore_path: Path to keystore dedicated to Zeenea
role_zeenea_server_tls_keystore_password: Keystore password
role_zeenea_authentication_ldap_host: Ldap's host
role_zeenea_authentication_ldap_port: Ldap's port
role_zeenea_authentication_ldap_base_dn: Ldap DN
role_zeenea_authentication_ldap_bind_dn: Bind Zeenea to get information in LDAP Server
role_zeenea_authentication_ldap_bind_password: Zeenea bind password to get information in LDAP Server
role_zeenea_authentication_ldap_tls_trutstore_path: Trustore path
role_zeenea_authentication_ldap_tls_trutstore_password: Password to decrypt trustore
role_zeenea_authentication_ldap_profile_group_superadmin: Ldap group to access to Zeenea as a Super Admin
role_zeenea_authentication_ldap_profile_group_admin: Ldap group to access to Zeenea as a Admin
role_zeenea_authentication_ldap_profile_group_user: Ldap group to access to Zeenea as a user
role_zeenea_security_keystore_password: Keystore password created by Zeenea
role_zeenea_security_data_password: Password to encrypt Data for Zeenea
role_zeenea_security_jwt_password: Password to encrypt JWT ticket 
role_zeenea_orientdb_connection_password: Password to connect to Data base
```

Playbook
-----------

Playbook name is playbook_zeenea, you can find it here : https://sgithub.fr.world.socgen/BigDataHub-I2T/playbook_zeenea.git

It's a example playbook to install Zeenea in PROD/DEV/INT-F environment.

Example Playbook
----------------

Install Zeenea
```

- name: "Deploy Zeenea"
  hosts: "zeenea"
  tasks:
    - name: "Launch role_zeenea with present state"
      become: True
      include_role:
        name: role_zeenea
      vars:
        state: "role_zeenea_whole_install"
```

Author Information
------------------

Franck Vieira
