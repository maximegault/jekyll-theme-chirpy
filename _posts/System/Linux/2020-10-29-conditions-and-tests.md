---
title: Conditions and tests
date: 2020-10-29 09:30:00 HH:MM:SS +0100
categories: [System, Linux]
tags: [system, linux, shell, tests, conditions]
---

### Conditions
* `-d` returns true if a directory exists
* `-e` returns true if a file exists
* `-o` perform a logical or between two tests
* `-z` returns true if the given command returns an empty string
```shell
if [ -z "`grep "DIRECTORY" /etc/sudoers`" ]
```
[More conditions](https://fr.wikibooks.org/wiki/Programmation_Bash/Tests)

### Test command
* `&&`
```shell
test cmd1 && cmd2
```
cmd1 is executed, if its return code equals 0 then cmd2 is executed
* `||`
```shell
test cmd1 || cmd2
```
cmd1 is executed, if its return code is different than 0 then cmd2 is executed

[test command](https://en.wikipedia.org/wiki/Test_(Unix))