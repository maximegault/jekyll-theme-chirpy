---
title: Ansible IO
date: 2021-05-06 16:00:00 HH:MM:SS +0100
categories: [System, Linux, Ansible, YAML]
tags: [system, linux, ansible, yaml, tips]
---

### Check if a file exists and creates it if it doesn't

With the [stat module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/stat_module.html):

```yaml
- ansible.builtin.stat: 
    path: pathToFile
  register: file_exists
```

Can be used like that in a test, ie. create it if does not exist:

```yaml
- ansible.builtin.file:
    path: pathToFile
    state: touch
  when: file_exists.stat.exists == false
```
