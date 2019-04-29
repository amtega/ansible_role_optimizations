# Ansible optimizations role

This is an [Ansible](http://www.ansible.com) role to configure some kernel optimizations.

There are three way to perform this adjusts:

- Adjust sysctl values.
- Configure kernel modules parameters.
- Apply a perfomance profile with tuned daemon.

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - amtega.optimizations
  vars:
    optimizations_nfs: yes
    optimizations_nfs_module:
      - udp_slot_table_entries=64
      - tcp_slot_table_entries=128
      - tcp_max_slot_table_entries=128

    optimizations_tuned_enabled: yes
    optimizations_tuned_profile: virtual-guest
```

## Testing

Tests are based on vagrant virtual machines. You can setup vagrant engine quickly using the playbook `files/setup.yml` available in the role [amtega.vagrant_engine](https://galaxy.ansible.com/amtega/vagrant_engine).

Once you have vagrant, you can run the tests with the following commands:

```shell
$ cd amtega-optimizations/test
$ ansible-playbook main.yml
```

## License

Copyright (C) 2019 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- José Enrique Mourón Regueira
