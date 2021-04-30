---
title: Ansible loops
date: 2021-04-29 14:30:00 HH:MM:SS +0200
categories: [System, Linux, Ansible, YAML, loop]
tags: [system, linux, ansible, yaml, tips, loop, loops]
---

## Loops

### Simple loop

### Get loop's index

### Get loop's extended infos

    - name: RHDS installation and customization
      block:      
      - name: Call to installation role
        include_tasks: tasks/installation-and-customization.yml
        loop: "{{ hostvars[inventory_hostname].instances }}"
        vars:
          instance_env: "{{ item.env }}"
          instance_custo_type: "{{ item.custo_type }}"
          instance_index_zero: "{{ ansible_loop.index0 }}"
        loop_control:
          extended: yes

[Ansible loops reference](https://docs.ansible.com/ansible/latest/user_guide/playbooks_loops.html)
