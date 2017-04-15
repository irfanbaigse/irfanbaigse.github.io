---
layout: post
title: Linux Permissions Explained
image: /img/linux_permissions.jpg
share-img: /img/linux_permissions.jpg
subtitle: Understanding linux file permissions
show-avatar: true
comments: true
tags: [linux, linux-permissions]
meta-data: access, calculator, chgrp, chmod, chown, cli, command, convert, file, group line, linux, lookup, lpi octal, permission, permissions, perms, program, script, shell, symbolic, unix, user
---

Linux file access permissions are used to control who is able to read, write and execute a certain file.

## Contents

* [Linux Permissions](#)
	* [What are File permissions ?](#file-permissions-?)
	* [Permissions types](#what-are-file-permissions-?)
	* [Types of users](#permissions-types)
	* [Permission Indicators](#permission-indicators)
	* [Octal table](#chmod-octal-value-binary-value-and-meaning)
	* [Setting Permissions with Chmod](#chmod-octal-value-binary-value-and-meaning)
* [Chmod Helper](#chmod-helper)
* [Code Examples](#code-examples)

---
   
### Linux Permissions   

---
   
#### What are File Permissions ?
In linux, every file or folder has access permissions. Linux file permissions are **9** bits of information (3 types permissions x 3 type of users)

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

#### Permission Indicators:

[comment]:![Permission Indicators](/assets/posts/2017-04-15-linux-permissions-explained/permission_indicators.jpg){:class="img-responsive"}

{% include image.html name="permission_indicators.jpg"  alt="Linux Permission Indicators" %}
   
#### View Permissions:
Syntax below

`[~]$ls -l` -- List items in current directory and show permissions.
 
`[~]$ls -l [path of file or folder]` -- Show permissions for the given path.

---
   
#### Setting Permissions with Chmod: 
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
   
### Chmod Helper

---

<form name="chmod"><p><table cellpadding="0" cellspacing="0" border="0" bgcolor="#03075D"><tr><td width="100%" valign="top"><table width="100%" cellpadding="5" cellspacing="2" border="0"><tr><td width="100%" bgcolor="#52847B" align="center" colspan="5"><font color="#ffffff" size="3"><b>chmod (File Permissions) helper</b></font></td></tr><tr bgcolor="#bcbcbc"><td align="left"><b>Permission</b></td><td align="center"><b>Owner</b></td><td align="center"><b>Group</b></td><td align="center"><b>Other</b></td><td bgcolor="#dddddd" rowspan="4"> </td></tr><tr bgcolor="#dddddd"><td align="left" nowrap><b>Read</b> (r=4)</td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="owner4" value="4" onclick="do_chmod('owner')"></td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="group4" value="4" onclick="do_chmod('group')"></td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="other4" value="4" onclick="do_chmod('other')"></td></tr><tr bgcolor="#dddddd"><td align="left" nowrap><b>Write</b> (w=2)</td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="owner2" value="2" onclick="do_chmod('owner')"></td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="group2" value="2" onclick="do_chmod('group')"></td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="other2" value="2" onclick="do_chmod('other')"></td></tr><tr bgcolor="#dddddd"><td align="left" nowrap><b>Execute</b> (x=1)</td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="owner1" value="1" onclick="do_chmod('owner')"></td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="group1" value="1" onclick="do_chmod('group')"></td><td align="center" bgcolor="#ffffff"><input type="checkbox" name="other1" value="1" onclick="do_chmod('other')"></td></tr><tr bgcolor="#dddddd"><td align="right" nowrap>Octal:</td><td align="center"><input type="text" name="t_owner" value="" size="1"></td><td align="center"><input type="text" name="t_group" value="" size="1"></td><td align="center"><input type="text" name="t_other" value="" size="1"></td><td align="left"><b>=</b> <input type="text" name="t_total" value="" size="3"></td></tr><tr bgcolor="#dddddd"><td align="right" nowrap>Symbolic:</td><td align="center"><input type="text" name="sym_owner" value="" size="3"></td><td align="center"><input type="text" name="sym_group" value="" size="3"></td><td align="center"><input type="text" name="sym_other" value="" size="3"></td><td align="left"><b>=</b> <input type="text" name="sym_total" value="" size="10"></td></tr><tr bgcolor="#dddddd"><td colspan="5" align="center"><font face="Arial" size="1">Provided free by <a href="http://abledesign.com/programs/" target="_blank">AbleDesign</a>, inspired by <a href="http://wsabstract.com/script/script2/chmodcal.shtml" target="_blank">Chmod Calculator</a></font></td></tr></table></td></tr></table></p></form>

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

#### Python:
***Format***: `os.chmod(path, mode)`  [click here for docs](https://docs.python.org/2/library/os.html#os.chmod){:target="_blank"}

``` 
import os
os.chmod("/anydir/anyfile", 0777)
```

---

<script type="text/javascript">
function do_chmod(c){var o=c+"4",e=c+"2",d=c+"1",m="t_"+c,u="sym_"+c,t=0,h="";1==document.chmod[o].checked&&(t+=4),1==document.chmod[e].checked&&(t+=2),1==document.chmod[d].checked&&(t+=1),h+=1==document.chmod[o].checked?"r":"-",h+=1==document.chmod[e].checked?"w":"-",h+=1==document.chmod[d].checked?"x":"-",0==t&&(t=""),document.chmod[m].value=t,document.chmod[u].value=h,document.chmod.t_total.value=document.chmod.t_owner.value+document.chmod.t_group.value+document.chmod.t_other.value,document.chmod.sym_total.value="-"+document.chmod.sym_owner.value+document.chmod.sym_group.value+document.chmod.sym_other.value}
</script>
   