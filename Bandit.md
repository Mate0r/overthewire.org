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
