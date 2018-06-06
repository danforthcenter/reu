# Introduction to Linux

In this session we will learn to work with command-line Linux. For detailed information about the Bioinformatics Core 
Facility, see [here](http://bioinformatics.readthedocs.io/). 

# Outline
1. Connecting to the system using Jupyter
2. Basic file operations
3. Connecting to a remote system (Raspberry Pi)

# Connecting to Jupyter

In your web browser open https://jupyter.bioinformatics.danforthcenter.org/

At the login screen, enter your username and password.

For shell access, click the `New` menu, then select `Terminal`.

Once connected, try changing your password:

```bash
passwd
```

You should be prompted with the messages below. Note that the password inputs are hidden for security, so you will
not see text while typing.

```
Changing password for user <username>.
(current) LDAP Password:
New password:
Retype new password:
```

## Get some files

Clone the our workshop materials from GitHub

```bash
git clone https://github.com/danforthcenter/reu.git
```

# Basic Linux shell commands

`pwd` - print the current working directory path

`ls` - list the files and directories in the current working directory

Modify a program's default behavior using flags/options

`ls -l` - list files and directories in list view

```
total 12
drwxr-xr-x  2 nfahlgren bioinfo   28 Mar 18 09:53 condor
drwxr-xr-x 11 nfahlgren bioinfo 4096 Jun  4 23:10 github
drwxr-xr-x  4 nfahlgren bioinfo   70 Apr 27 17:08 jbrowse
-rw-r--r--  1 nfahlgren bioinfo    0 Jun  5 22:03 myfile.txt
lrwxrwxrwx  1 nfahlgren bioinfo   11 Jun  5 22:05 myscript -> myscript.py
-rwxr-xr-x  1 nfahlgren bioinfo    0 Jun  5 22:04 myscript.py
-rw-------  1 nfahlgren bioinfo    0 Jun  5 22:02 password.txt
drwxr-xr-x 16 nfahlgren bioinfo 4096 Jun  4 10:36 projects
drwxr-xr-x  4 nfahlgren bioinfo 4096 Jun  5 21:59 reu
drwxr-xr-x  7 nfahlgren bioinfo  153 Dec  4  2017 support
drwxr-xr-x  3 nfahlgren bioinfo   88 May  4 14:56 transect_data
```

`cd` - change directories directly to home

**cd** ***dir*** - change directories from the current working directory to *dir*

```bash
pwd

cd reu

pwd

ls -l
```

Absolute versus relative paths. `.` = current directory, `..` = parent directory.

```bash
# Absolute
ls -l /home/$USER/reu/examples

# Relative
ls -l ./examples
```

Create and delete files and directories

**touch** ***file*** - create the empty file *file*

**rm** ***file*** - remove the file *file*

```bash
touch test.txt

ls -l

rm test.txt

ls -l
```

**mkdir** ***dir*** - make the directory *dir*

**rmdir** ***dir*** - remove the directory *dir* (has to be empty)

```bash
mkdir test

ls -l

rmdir test

ls -l
```

**cp** ***file1*** ***file2*** - create a copy of *file1* called *file2*

**cp -r** ***dir1*** ***dir2*** - create a copy of *dir1* and its contents called *dir2*

```bash
cp README.md readme.md

cp -r examples examples_copy

ls -l
```

**mv** ***file1*** ***file2*** - move/rename *file1* to *file2*

**head** ***file*** - print the first 10 lines of *file* to *stdout*

**tail** ***file*** - print the last 10 lines of *file* to *stdout*

**less** ***file*** - opens *file* using a paging viewer

```bash
mv readme.md readme

head LICENSE

tail LICENSE

less LICENSE
# press q to quit
```

`htop` - display the current running processes (task manager/activity monitor). It is a modern version of **top** 
which should be available if **htop** is not.

`df -h` - display disk usage with human-readable units

**gzip** ***file*** - compress *file*

**gunzip** ***file.gz*** - decompress *file.gz*

**tar zcf** ***archive.tar.gz*** ***dir*** - create a compressed archive of *dir* (or a set of files)

**tar zxf** ***archive.tar.gz*** - decompress and extract the contents of *archive.tar.gz*

**Ctrl+C** - stop the current command

**exit** - log out of the current session

# Connecting to a remote server

To connect to a Raspberry Pi we will use Secure Shell (SSH). The three pieces of information you need to connect are 
the hostname/IP address of the server, a username, and a password. The command will take the form: 

```bash
ssh <username>@<hostname>
```
