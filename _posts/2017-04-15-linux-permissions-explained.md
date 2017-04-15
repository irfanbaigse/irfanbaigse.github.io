---
layout: post
title: Linux Permissions Explained
image: /img/linux_permissions.jpg
subtitle: Understanding linux file permissions
show-avatar: false
tags: [linux, linux-permissions]
meta-data: access, calculator, chgrp, chmod, chown, cli, command, convert, file, group line, linux, lookup, lpi octal, permission, permissions, perms, program, script, shell, symbolic, unix, user
---

## Contents

* [Linux Permissions](#)
	* [What are File permissions ?](#file-permissions-?)
	* [Permissions types](#what-are-file-permissions-?)
	* [Types of users](#permissions-types)
	* [Octal table](#chmod-octal-value-binary-value-and-meaning)
* [Code Examples](#code-examples)

---
   
#### What are File Permissions ?
In linux, every file or folder has access permissions. Linux file permissions are **9** bits of information (3 types x 3 type of users)

[comment]:Linux has 2 basic file types _normal and special_

#### Permissions Types:
	- (r)read access
	- (w)write access
	- (x)execute access

#### Types of users:
	- (u)owner of the file 
    - (g)group the owner belongs
    - (o)other users
    
`u` is the user's permissions, `g` is the group's permissions & `o` other, can be any number between 0-7

---
   
#### Chmod octal value binary value and meaning:
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
    
#### View Permissions:

Syntax below

`[~]$ls -l` -- List items in current directory and show permissions.
 
`[~]$ls -l [path of file or folder]` -- Show permissions for the given path.

---
   
#### Setting Permissions with chmod:
Syntax below

`[~]$chmod [permission] [path of file or folder]`

where `[permission]` can be either octal or symbolic notation e.g:

```
chmod 077 foo.sh   # octal
chmod +x bar.sh    # symbolic
```

changes permission of file bar.sh the named file to executable.

* `+` - adds permissions
* `x` - executable rights 

---

### Code Examples:

----

#### Golang:
***Format***: 
`os.Chmod(path, mode)`  [click here for docs](https://golang.org/pkg/os/#Chmod){:target="_blank"}

```
package main

import "os"

err := os.Chmod("file.txt", 0777)
 if err != nil {
     fmt.Println(err)
 }
```

-----

#### PHP:
***Format***: `chmod( string $path, int $mode);`  [click here for docs](https://secure.php.net/manual/en/function.chmod.php){:target="_blank"}

```
<?php
   chmod("/somedir/somefile", 755);   // decimal; probably incorrect
   chmod("/somedir/somefile", "u+rwx,go+rx"); // string; incorrect
   chmod("/somedir/somefile", 0755);  // octal; correct value of mode
?>
```

-----

#### Python:
***Format***: `os.chmod(path, mode)`  [click here for docs](https://docs.python.org/2/library/os.html#os.chmod){:target="_blank"}

``` 
import os
os.chmod("/anydir/anyfile", 0777)
```

---
   