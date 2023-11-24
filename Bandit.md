https://overthewire.org/wargames/bandit/

# Level 0
```bash
┌──(parallels㉿kali)-[~]
└─$ ssh bandit0@bandit.labs.overthewire.org -p 2220
```
We enter the password bandit0 as indicated in the level goal tutorial.\
We found a readme file in the home directory and we have the password for the bandit1 user

# Level 1
```bash
┌──(parallels㉿kali)-[~]
└─$ ssh bandit1@bandit.labs.overthewire.org -p 2220
bandit1@bandit:~$ ll
total 24
-rw-r-----  1 bandit2 bandit1   33 Oct  5 06:19 -
drwxr-xr-x  2 root    root    4096 Oct  5 06:19 ./
drwxr-xr-x 70 root    root    4096 Oct  5 06:20 ../
-rw-r--r--  1 root    root     220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root    root    3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root    root     807 Jan  6  2022 .profile
bandit1@bandit:~$ cat ./-
{REDACTED}
```
We found the password in the '-' file but we must use a little trick cause the hyphen is used to pass options to a command too\
So we use the ./- string to access to the file

# Level 2
```bash
┌──(parallels㉿kali)-[~]
└─$ ssh bandit2@bandit.labs.overthewire.org -p 2220
bandit2@bandit:~$ ll
total 24
drwxr-xr-x  2 root    root    4096 Oct  5 06:19 ./
drwxr-xr-x 70 root    root    4096 Oct  5 06:20 ../
-rw-r--r--  1 root    root     220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root    root    3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root    root     807 Jan  6  2022 .profile
-rw-r-----  1 bandit3 bandit2   33 Oct  5 06:19 spaces in this filename
bandit2@bandit:~$ cat spaces\ in\ this\ filename 
{REDACTED}
```
We found the password in the file with spaces in the name "spaces in this filename"\
We can read this file by escaping the space character with a backslash ```cat spaces\ in\ this\ filename```

# Level 3
```bash
┌──(parallels㉿kali)-[~]
└─$ ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit:~$ ll
total 24
drwxr-xr-x  3 root root 4096 Oct  5 06:19 ./
drwxr-xr-x 70 root root 4096 Oct  5 06:20 ../
-rw-r--r--  1 root root  220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root root 3771 Jan  6  2022 .bashrc
drwxr-xr-x  2 root root 4096 Oct  5 06:19 inhere/
-rw-r--r--  1 root root  807 Jan  6  2022 .profile
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ll
total 12
drwxr-xr-x 2 root    root    4096 Oct  5 06:19 ./
drwxr-xr-x 3 root    root    4096 Oct  5 06:19 ../
-rw-r----- 1 bandit4 bandit3   33 Oct  5 06:19 .hidden
bandit3@bandit:~/inhere$ cat .hidden
{REDACTED}
```
We found the password in a hidden file\
In linux, the files beggining by a dot doesn't appears by default\
Here, i use the ll command that is a shortcut to this command : ls -alF\
the a option display the hidden files

# Level 4
```bash
┌──(parallels㉿kali)-[~]
└─$ ssh bandit4@bandit.labs.overthewire.org -p 2220
bandit4@bandit:~$ ls -la
total 24
drwxr-xr-x  3 root root 4096 Oct  5 06:19 .
drwxr-xr-x 70 root root 4096 Oct  5 06:20 ..
-rw-r--r--  1 root root  220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root root 3771 Jan  6  2022 .bashrc
drwxr-xr-x  2 root root 4096 Oct  5 06:19 inhere
-rw-r--r--  1 root root  807 Jan  6  2022 .profile
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls -la
total 48
drwxr-xr-x 2 root    root    4096 Oct  5 06:19 .
drwxr-xr-x 3 root    root    4096 Oct  5 06:19 ..
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file00
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file01
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file02
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file03
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file04
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file05
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file06
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file07
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file08
-rw-r----- 1 bandit5 bandit4   33 Oct  5 06:19 -file09
bandit4@bandit:~/inhere$ cat ./-file0*
```
We found that there is a flag in one of these files and particullary the -file07 file\

# Level 5

