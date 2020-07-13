---
# Course title, summary, and position.
linktitle: Command Line Basics
summary: Linux Command Line Basics.
weight: 1

# Page metadata.
title: Overview
date: "2016-06-07T00:00:00Z"
lastmod: "2016-06-07T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  command_line:
    name: Overview
    weight: 1
---

Most computer Operating Systems (OS) provide a graphical user interface (GUI or "gooey") to interact with systems through point-and-click mouse movements. However, using the command-line interface (CLI) provides a more concise and powerful means to control a program or OS. Moreover, using programs with a CLI are usually easier to automate via scripting, which is a necessity for any serious developer, programmer, software engineer, or computer scientist.

*Note: the words **directory** and **folder** are used synonymously.*

---
<br>

`pwd`  
**P**rint the full filename of the current **w**orking **d**irectory.

```ini
$ pwd
```

`ls`  
**L**i**s**t the contents of the current directory.

```ini
$ ls
```

`cd ..`  
The **c**hange **d**irectory and double period combination will move to the parent directory of the current directory.

```ini
$ cd ..
```

`cd ~`  
The **c**hange **d**irectory and **~** (tilde) combination will return to the *home directory*. It is an alternative to using the *$HOME* command.

```ini
$ cd ~
```

`cd /`  
The **c**hange **d**irectory and **/** (forward slash) combination will return to the *root directory*.

```ini
$ cd /
```
<br>

## Creating Directories

`mkdir`  
**M**a**k**e **dir**ectory is used to create a new directory in the current directory or in another directory. It can also create multiple directories by providing a list of file paths, separated by spaces.

```ini
# Create a new directory in the current directory.
$ mkdir dev_projects
$ ls
dev_projects/

# Create a new directory in another directory.
$  mkdir dev_projects/test_1
$ ls dev_projects/
test_1/

# Create multiple directories in another directory.
$ mkdir dev_projects/ex_1 dev_projects/ex_2
$ ls dev_projects/
ex_1/  ex_2/
```
<br>

## Creating Files

`touch`  
**Touch** can create a new file in the current directory or another directory. It can also create multiple files by providing a list of file paths, separated by spaces.

```ini
# Create new file in current directory.
$ touch test.py
$ ls
test.py

# Create new file in another directory.
$ touch dev_env/hello-world.py
$ ls dev_env/
hello-world.py

# Create multiple files in another directory.
$ touch dev_env/ex1.py dev_env/ex2.py
$ ls dev_env/
ex1.py  ex2.py
```

`ls -lSh`  
Use **ls** (list directory contents), the **-l** (long listing format), **-S** (sort by file size), and **-h** (human readable) flags to view additional information.

```ini
$ ls -lSh test_env/

# Total in Kilobytes.
total 4.0K

# The leading dash (-) means this is a file.
-rw-rw-r-- 1 user user 19 Feb 19 06:41 example.py
```
<br>

## Removing Files

`rm`  
The **r**e**m**ove command is used to delete a single file or multiple files.

```ini
# Remove a single file.
$ ls
example.py

$ rm example.py 

# Remove multiple files at once.
$ ls
note_1  note_2  note_3

$ rm note_1 note_2
$ ls
note_3
```
<br>

## Removing Directories

`rmdir`  
The <span class="dark-pink fw9">r</span>e<span class="dark-pink fw9">m</span>ove <span class="dark-pink fw9">dir</span>ectory command will only delete a completely empty directory.

```ini
$ ls
ex_1/  ex_2/  test_1/

$ rmdir test_1/
$ ls
ex_1/  ex_2/
```

`rm -rf`  
The **rm** command in conjunction with the **-rf** flag will delete the directory and all files and folders inside. This is done with *recursive force*, using an approach called *recursion*.  

*Use this command with extreme caution!*

```ini
$ ls
ex_1/  ex_2/

$ rm -rf ex_1/
$ ls
ex_2/
```
<br>

---
## **Summary**  
---
<br>

:heavy_check_mark: `ls -lSh` - list a directory's contents, sorted by file size.  

:heavy_check_mark: `cd` - change to a different directory.  

:heavy_check_mark: `pwd` - print the current working directory's location.  

:heavy_check_mark: `touch` - create a new file or update a file's timestamp.  

:heavy_check_mark: `mkdir` - make a new directory.  

:heavy_check_mark: `rm` - remove a file.  

:heavy_check_mark: `rmdir` - remove an empty directory.  

:heavy_check_mark: `rm -rf` - permanently remove a directory and its contents (caution is advised).  
