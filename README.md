# Ansible role Wireguard

![syntax check](https://github.com/tanlinhnd/ansible-role-wireguard/actions/workflows/main.yml/badge.svg)

This Ansible role performs a [Wireguard](https://www.wireguard.com/) installtion.

## Requirements

This role does work with the following minimum versions:

* Ansible: 2.8.4
* Wireguard: v1.0.20210914
* Ubuntu: 16.04
* Debian: 9
* Fedora: 32

## Example

```yaml
---
- hosts: localhost
  become: yes
  vars:
    - wireguard_users:
        - username: "client_1"
          email: "client_1@example.com"
          private_ip: "10.99.0.2"
          allow_ips: "10.69.0.0/16"
          state: "present"
  roles:
    - ansible-role-wireguard
```

## Roles Variables

The role defines variables in `defaults/main.yml`.

### `private_ip`

- Private IP address of instance. Use to config SNAT with iptables.
- Default: `ansible_default_ipv4.address`

### `wireguard_interface`

- Name of wireguard network interface
- Default: `wg0`

### `wireguard_subnet`

- Subnetwork to use in `AllowedIPs` configuration
- Default: `10.99.0.0/24`

### `wireguard_server_address`

- IP address use to config for server (interface `wg0`)
- Default: `10.99.0.1/24`

### `wireguard_port_listen`

- Wireguard UDP port to listen.
- Default: `51820`

### `wireguard_users`

- List of user to provision. Follow this structure.
- Example:

```yaml
wireguard_users:
  - username: "client_1"
    email: "client_1@example.com"
    private_ip: "10.99.0.2"
    allow_ips: "10.69.0.0/16"
    state: "present"
```
### `mail_from`

- Set the mail address that you send from.
- Example: notifications@github.com, info@shopee.vn, ...etc

### `mail_title`

- Title for mails, usually name of company.

### `smtp_user`

- Key of your AWS SES

### `smtp_pass`

- Secret of your AWS SES


## License

BSD-2-Clause

## Author Information

[Linh Nguyen](https://blog.dmesg.sh)
