---
layout: post
title: Linux Permissions Explained
image: /img/linux_permissions.jpg
subtitle: Understanding linux file permissions
show-avatar: false
tags: [linux, exciting-stuff]
---

This post is not intend to redefine the linux permissions its is just get to basic idea what it means.

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
    
**Chmod Octal Format**

| Octal Value | Read | Write | Execute |
| :------ |:--- | :--- |
| 7 | r | w | ✗ |
| 6 | r | w | - |
| 5 | r | - | ✗ |
| 4 | r | - | - |
| 3 | - | w | ✗ |
| 2 | - | w | - |
| 1 | - | - | ✗ |
| 0 | - | - | - |