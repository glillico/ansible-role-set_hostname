# Ansible Role : set_hostname

This role set the servers hostname based on the MAC address of the primary network interface.

## Requirements

None.

## Role Variables

### vars/main.yml

Required the MAC addresson the primary network interface and the desired hostname to be entered.

```
  mac_address_mapping:
  "00:50:56:e4:3b:74":
    name: centos7.test
  "00:50:56:13:3f:c6":
    name: centos8.test
  "00:50:56:55:f5:d8":
    name: debian10.test
```

This means that a server with the primary network interface mac address set to `00:50:56:e4:3b:74` would get its hostname set to `centos7.test`.

#### NOTE

It is worth noting that a couple of things are set differently depending on the
OS family.  This includes the /etc/hostname file and the servers hostname.

For example:
- On a RedHat based systems the hostname would be set to servername.domainname.
- On a Debian based systems the hostname would be set to servername.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
        - glillico.set_hostname

## License

MIT

## Author Information

This role was created in 2020 by Graham Lillico. (Inspired by [geerlingguy/raspberry-pi-dramble](https://github.com/geerlingguy/raspberry-pi-dramble)).
