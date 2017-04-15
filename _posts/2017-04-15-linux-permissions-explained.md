---
layout: post
title: Linux Permissions Explained
image: /img/linux_permissions.jpg
subtitle: Understanding linux file permissions
show-avatar: false
tags: [linux, linux-permissions, exciting-stuff]
---
***File permissions ?***

In linux, every file or folder has access permissions. Linux file permissions are **9** bits of information (3 types x 3 type of users)

[comment]:Linux has 2 basic file types _normal and special_

***Permissions types:***

	- (r)read access
	- (w)write access
	- (x)execute access

***Permissions are defined for 3 types of users:***

	- (u)owner of the file 
    - (g)group the owner belongs
    - (o)other users
    
`u` is the user's permissions, `g` is the group's permissions & `o` other, can be any number between 0-7

---
   
***Chmod Octal, Binary & Meaning:***
`chmod` stands for `change mode`

Dash (–) means no permission.

| Octal | Read | Write | Execute | Binary | Meaning |
| :------ |:----| :---- | :---- | :------ | :------ |
| 7 | r | w | x | 1 1 1 | Full permissions	|
| 6 | r | w | - | 1 1 0 | Read & write only	|
| 5 | r | - | x | 1 0 1 | Read & execute only	|
| 4 | r | - | - | 1 0 0 | Read only	|
| 3 | - | w | x | 0 1 1 | Write & execute only	|
| 2 | - | w | - | 0 1 0 | Write only	|
| 1 | - | - | x | 0 0 1 | Execute only	|
| 0 | - | - | - | 0 0 0 | No permissions	|

---
    
***View Permissions:***

Syntax below

`[~]$ls -l` -- List items in current directory and show permissions.
 
`[~]$ls -l [path of file or folder]` -- Show permissions for the given path.

---
   
***Setting Permissions with chmod:***

Syntax below

`[~]$chmod [permission] [path of file or folder]`

where `[permission]` can be either octal or symbolic notation e.g:

```
chmod 077 foo.sh   # octal
chmod +x bar.sh    # symbolic
```
---
   