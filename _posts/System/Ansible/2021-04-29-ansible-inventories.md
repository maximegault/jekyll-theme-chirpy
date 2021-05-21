---
title: Ansible inventories
date: 2021-04-29 14:30:00 HH:MM:SS +0200
categories: [System, Linux, Ansible, YAML, inventory]
tags: [system, linux, ansible, yaml, tips, inventory, inventories]
---

### Inventory in YAML format

Example:

```yaml
---
all:
  children:
    group_1:
      hosts:
        customAlias:
          ansible_host: "realHostName.myDomain.com" 
          var_1: "Foo" 
        customAlias_2:
          ansible_host: 192.168.1.2 
          var_2: 12345 
    group_2:
      hosts:
        "realHostName2.myDomain.com"
```

### Inventory in INI format

[Excellent article on Ansible inventories - INI format only](https://www.digitalocean.com/community/tutorials/how-to-set-up-ansible-inventories)

### Check an inventory syntax

Examples with the one given in YAML. To have a list:

```shell
ansible-inventory -i inventory --list
```

Output:

```json
{
    "_meta": {
        "hostvars": {
            "customAlias": {
                "ansible_host": "realHostName.myDomain.com",
                "var_1": "Foo"
            },
            "customAlias_2": {
                "ansible_host": "192.168.1.2",
                "var_2": 12345
            },
            "realHostName2.myDomain.com": {}
        }
    },
    "all": {
        "children": [
            "group_1",
            "group_2",
            "ungrouped"
        ]
    },
    "group_1": {
        "hosts": [
            "customAlias",
            "customAlias_2"
        ]
    },
    "group_2": {
        "hosts": [
            "realHostName2.myDomain.com"
        ]
    },
    "ungrouped": {}
}
```

To have a simplier graph:

```shell
ansible-inventory -i inventory --graph
```

Output:

```text
@all:
  |--@group_1:
  |  |--customAlias
  |  |--customAlias_2
  |--@group_2:
  |  |--realHostName2.myDomain.com
  |--@ungrouped:
```

## Inventories to use in local

### In INI format

Most basic:

```ini
localhost ansible_connection=local
```

### In YAML format

The same one in YAML:

```yaml
all:
  children:
    ungrouped:
      hosts:
        localhost:
          ansible_connection: local
```

### Convert INI inventory in YAML one

The YAML seems more easy to me to manage complex structures:

```shell
ansible-inventory -i inventory_ini -y --list > inventory_yaml
```
