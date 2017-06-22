# openvpn

[![Build Status](https://travis-ci.org/m31271n/ansible-role-openvpn.svg?branch=master)](https://travis-ci.org/m31271n/ansible-role-openvpn)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-m31271n.openvpn-blue.svg)](https://galaxy.ansible.com/m31271n/openvpn)

Ansible role that setups OpenVPN.

## Requirements

None.

## Role Variables

```
openvpn_version: 2.4.2

openvpn_type: '' # client or server

openvpn_server_conf_path: /etc/openvpn/server
openvpn_client_conf_path: /etc/openvpn/client
openvpn_conf_name: default

openvpn_ca_cert: ca.crt
openvpn_tls_auth_key: ta.key

openvpn_server_addr: 127.0.0.1
openvpn_server_port: 1194
openvpn_server_cert: server.crt
openvpn_server_key: server.key
openvpn_server_dh: dh2048.pem

openvpn_client_cert: '{{ inventory_hostname }}.crt'
openvpn_client_key: '{{ inventory_hostname }}.key'
```

## Dependencies

None.

## Example Playbook

Place OpenVPN related files in `{{ playbook_dir }}/files/openvpn`.

General:
+ `ca.crt`
+ `ta.key`

For Server:

+ `dh2048.pem`
+ `server.crt`
+ `server.key`

For Clients:

+ `{{ inventory_hostname }}.crt`
+ `{{ inventory_hostname }}.key`

```
- hosts: server
  roles:
    - role: m31271n.openvpn
      openvpn_conf_name: 'my-openvpn'
      openvpn_server_port: '1194'
      openvpn_type: client
```

```
- hosts: clients
  roles:
    - role: m31271n.openvpn
      openvpn_conf_name: 'my-openvpn'
      openvpn_server_addr: '111.111.111.111'
      openvpn_server_port: '1194'
      openvpn_type: client
```


* * *

<p align="center">Made with ❤ by <a href="http://index.m31271n.com">m31271n</a></p>
