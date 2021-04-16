---
title: Ansible tips
date: 2021-04-16 08:00:00 HH:MM:SS +0100
categories: [System, Linux, Ansible, YAML]
tags: [system, linux, ansible, yaml, tips]
---

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
* `inventory_hostname` = `myMachine.myDomain.com`
