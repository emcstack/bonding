bonding
=========

Role to create / configure properly bonding interfaces

Requirements
------------

Ansible 2.0, python-netaddr

Role Variables
--------------

| Name | Type | Required | Default | Description
|--- |--- |--- |--- |---
| slaves | list | yes | None | List of the slaves part of the bond
| bond | string | yes | None | Name of the bond interface
| apply | boolean | no | false | Set to true to write the real configuration files in sysconfig
| apply_now | boolean | no | false | Restart the network restart after writing the configuration files
| el_network_sysconfig | string | no | /etc/sysconfig/network-scripts | Default directory for RH/CentOS
| tmp_dir | string | no | /tmp | TMP directory for the configuration files
| bond_options | list of dict | no | [{ 'key': 'mode', 'value': 'lacp'}, { 'key': 'miimon', 'value': '80'}] | Some default values for Bonding Options
| mtu | int | no | 1500 | Value of the MTU for the interface
| enable_ipv4 | boolean | no | false | Determines if you want to use ipv4 settings for the bond interface
| manage_gateway | boolean | no | false | Determines if you want to configure the gateway on the bond
| manage_dns_servers | boolean | no | false | Determines if you want to configure DNS on the bond configuration
| manage_hw_addr | boolean | no | true | Determines if you want to write the HWADDR in the slaves configuration
| ip_addr | string | no | None | The IPv4 for the bond interface
| netmask | string | no | None | The Netmask for the bond interface
| gateway | string | no | None | The gateway to use for the bond interface
| dns1 | string | no | None | DNS1 server
| dns2 | string | no | None | DNS2 server
| enable_ipv6 | boolean | no | true | Enable IPv6 on the bond interface
| init_ipv6 | boolean | no | true | Enable IPv6 initiatialization
| ipv6_autoconf | boolean | no | no | Enable IPv6 autoconfiguration
| keep_slave_ipv4 | boolean | no | false | Determines if you want to keep the slaves existing IPv4 configuration


Dependencies
------------

None

Example Playbook
----------------

```

- hosts: nc-9
  roles:
  - bonding
  vars:
  - slaves:
    - eth0
    - eth1
  - bond: bond0

```

```

- hosts: nc-9
  roles:
  - bonding
  vars:
  - slaves:
    - eth0
    - eth1
  - bond: bond0
  - bond_options:
    - { 'key': 'mode', 'value': '4'}
    - { 'key': 'miimon', 'value': '100'}
    - { 'key': 'xmit_hash_policy', 'value': 'layer2+3'}
    - { 'key': 'lacp_rate', 'value': 'fast'}
    - { 'key': 'ad_select', 'value': 'bandwidth'}


```


License
-------

GPLv3

Author Information
------------------

John Preston [John Mille]
