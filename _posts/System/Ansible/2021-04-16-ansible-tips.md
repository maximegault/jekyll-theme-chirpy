---
title: Ansible tips
date: 2021-04-16 08:00:00 HH:MM:SS +0100
categories: [System, Linux, Ansible, YAML]
tags: [system, linux, ansible, yaml, tips]
---

### Ad-hoc mode

Used to test a module without having a playbook. Ie. with a ping on all hosts contained in the `inventory` file (`-m` is the argument for the module name):

```shell
ansible -i inventory all -m ping
```

Same thing with setup:

```shell
ansible -i inventory all -m ansible.builtin.setup
```

[Ad-hoc reference](https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html)

### Format a pattern

Example with the input values:

```yaml
server_pattern: "ldap://%s:%s"
server_uri: "myServer.com"
server_port: 389
```

```yaml
final_server_uri: "{{ server_pattern | format(server_uri, server_port) }}"
```

It will give:

```text
ldap://myServer.com:389
```

### Classic facts

On a target host called `myMachine.myDomain.com`:

* `ansible_hostname` = `myMachine`
* `ansible_fqdn` = `myMachine.myDomain.com`

### Magic variables

On a target host called `myMachine.myDomain.com`:

* `inventory_hostname_short` = `myMachine`
* `inventory_hostname` = `myMachine.myDomain.com`

[Magic variables vs. facts](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#)

### Special variables

Magic variables + classic facts = special variables

[Special variables reference](https://docs.ansible.com/ansible/latest/reference_appendices/special_variables.html)