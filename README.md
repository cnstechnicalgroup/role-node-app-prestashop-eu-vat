Role: cns.node-app-prestashop-eu-vat
========

This role installs the prestashop-eu-vat nodejs app into a defined folder, runs npm install to install dependencies defined in the project's package.json, and optionally creates a script to expose the app to a whitelisted set of clients.

Requirements
------------

Nothing, it runs out of the box.

Role Variables
--------------

In the current version, you can specify the following variables:

| Name               | Default |                                      |
|--------------------|---------|--------------------------------------|
| system_user        |   ---   | System account that owns the app    |
| system_group       |   ---   | System group that owns the app      |
| node_app_name      |   ---   | Name of the node app                 |
| node_app_root      |   ---   | Root directory where app lives |
| node_app_git_repo  |   ---   | Git repository URL |
| node_app_deploy_key|   ---   | Git repository deploy key |
| node_app_db_name|   ---   | DB name to connect |
| node_app_db_user|   ---   | DB username|
| node_app_db_password|   ---   | DB user password |
| node_app_execute|   ---   | Command to use to run app |
| node_app_db_tax_rules_group|   ---   | Tax Rule ID to use for configuration |
| node_app_whitelist|   ---   | IP addressess allowed to access exposed php script|
| node_app_exposed|   ---   | Script to expose publicly |


Dependencies
------------

This package has no dependencies.

License
-------

GPLv2

Author Information
------------------

Sam Morrison

Examples
--------

```yaml
# Variable file

node_app_name: prestashop-eu-vat
node_app_root: /opt/prestashop-eu-vat
node_app_git_repo: https://github.com/cnstechnicalgroup/prestashop-eu-vat.git
node_app_deploy_key: ../../keys/prestashop-eu-vat
node_app_db_name: "{{ ps_db_name }}"
node_app_db_user: "{{ ps_db_user }}"
node_app_db_password: "{{ ps_db_password }}"
node_app_execute: "/usr/local/bin/node app.js"
node_app_db_tax_rules_group: 5
node_app_whitelist: "'123.45.67.89', '123.45.67.90'"
node_app_exposed: "/srv/{{ domain }}/apply_tax_rules.php"
```

```yaml
---
- name: cns.node-app-prestashop-eu-vat example
  hosts: all
  roles:
    - cns.node-app-prestashop-eu-vat
```
