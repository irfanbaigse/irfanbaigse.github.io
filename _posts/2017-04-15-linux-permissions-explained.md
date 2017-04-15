---
layout: post
title: Linux Permissions Explained
image: /img/linux_permissions.jpg
subtitle: Understanding linux file permissions
show-avatar: false
tags: [linux, exciting-stuff]
---



**In Linux, there are two types of users**

	- system users 
    - regular users
    
System users are used to run non-interactive or background processes on a system and regular users used for logging in and running processes interactively  
    
    
**View Permissions**
```
$ls -al [path]
```
    
**Give Permissions**
```
$chmod [permission] [path]
```
    
**Chmod Octal, Binary & Meaning**

| Octal Value | Read | Write | Execute | Binary value | Meaning |
| :------ |:------ | :------ | :------ | :------ | 
| 7 | r | w | x | 111 |	Full permissions	|
| 6 | r | w | - | 110 |	Read & write only	|
| 5 | r | - | x | 101 |	Read & execute only	|
| 4 | r | - | - | 100 |	Read only	|
| 3 | - | w | x | 011 |	Write & execute only	|
| 2 | - | w | - | 010 |	Write only	|
| 1 | - | - | x | 001 |	Execute only	|
| 0 | - | - | - | 000 |	No permissions	|