---
title: Ansible lists and dictionaries
date: 2021-05-06 16:00:00 HH:MM:SS +0100
categories: [System, Linux, Ansible, YAML, Lists, Dictionaries]
tags: [system, linux, ansible, yaml, tips, lists, dictionaries]
---

### Convert a simple list into a dictionary

With the input list:

```yaml
strings:
  - 'firstString'
  - 'secondString'
```

To convert it into a dictionary, here with the list item as key and `false` as value:
<!-- {% raw %} -->
```yaml
- ansible.builtin.set_fact:
    strings_with_state_into_dictionary: "{{ strings_with_state_into_dictionary | default({}) | combine ({ string_item : false }) }}"
  loop: "{{ strings }}"
  loop_control:
    loop_var: string_item
```
<!-- {% endraw %} -->
`default({})` initializes `strings_with_state_into_dictionary` with an empty dictionary, `combine` fills the dictionary with the `key : value` syntax.
