Role Name: postgresql
=========

Install and configures a PostgreSQL server on CentOS-based systems.

Requirements
------------

- RHEL-based Linux (CentOS, Rocky, AlmaLinux)
- Ansible contol node with SSH access
- sudo provileges on target hosts

Role Variables
--------------

- postgresql_port: PostgreSQL service port (default: 5432)
- postgresql_data_dir: Data directory path
- postgresql_listen_address: Listen addresses for PostgreSQL

Dependencies
------------

None.

Example Playbook
----------------

- name: Deploy PostgreSQL Server
  hosts: db_servers
  become: true
  roles:
    - postgresql

License
-------

MIT
Internal use only

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
