bonding
=========

Role to create / configure properly bonding interfaces

Requirements
------------

Ansible 2.0, python-netaddr

Role Variables
--------------

slaves: list of the slaves part of the bond
bond: name of the bond interface


Dependencies
------------

None

Example Playbook
----------------

- hosts: nc-9
  roles:
  - bonding
  vars:
  - slaves:
    - eth0
    - eth1
  - bond: bond0

License
-------

GPLv3

Author Information
------------------

John Preston [John Mille]

