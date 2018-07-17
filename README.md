- What is the command to create a user with predefined uid / shell and a homedir'

```useradd -m -d /home/user -u 9000 -s /bin/bash user ```

- How to delete a user with homedir?

```userdel -r user ```

- HOw to create a usr specifying primary and secondary group?

``` userdd -g primary_group -G secondary_group user ```

- How to change users primary group?

```usermod -g NEW_GRP user ```

- How to give root priviliges to normal user?

``` cat /etc/sudoers
  --- Review the contents under Allow root to run any commands here.
      root   ALL=(ALL) ALL
      USER   ALL=(ALL) ALL
  --- Or add user to a wheel group, with or without password.
      linux_user ALL=(ALL) NOPASSWD: ALL ```
- How to view users login / logout logs.
``` last $user ```
``` cat /var/log/auth* ```

- How to lock and unlock a local user?
``` grep $user /etc/shadow  # user entry will have ! after username. ```
``` passwd -l $user (lock) ```
``` passwd -u $user (unlock) ```

- How to change expiry date of a user? command to view and change expiry date of any users?
```chage -l $user (shows info related to user)
Last password change                                    : May 12, 2017
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
humber of days of warning before password expires       : 7


[root@:~]# useradd test
[root@:~]# chage -l test
Last password change                                    : Jul 17, 2018
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
[root@:~]# chage -E 2018-12-12 test
[root@:~]# chage -l test
Last password change                                    : Jul 17, 2018
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : Dec 12, 2018
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7

-What are the contents of /etc/passwd
```test:x:40002:40002::/home/test:/bin/bash

1st field : username
2nd field : x : means password is encrypted
3rd field : uid
4th field : gid
5th field : description
6th field : home dir
7th field : default login shell
```
- What is the difference between .bashrc and .bash_profile
``` When you login .bash_profile is executed, if you are already logged in then .bashrc will be executed.
```
- What does command finger do?
``` finger test```
``` provied login shell and other info related to user```

- Name three files which are automatically created when new user is created.
``` .bash_history```
``` .bash_profile```
``` .bash_rc```

- What is the command to view currently logged in users?
``` w```
``` who (current user)```

- How to list hidden files
``` ls -a```

- What is the difference between $ and \# prompts in CLI?
``` # root login```
``` $ normal user prompt```

- How to find an error in a file
``` /bin/grep -i error /path/to/file```

- How to make a directory?
``` mkdir TEST_DIR```

- How to remove a directory?
``` rmdir TEST_DIR for an empty file```
``` rm -rf TEST_DIR```

- How to create a file?
``` touch $FILENAME```
``` vi $FILENAME```

- How to delete a file?
``` rm $FILENAME```

- What is the default port for DNS
``` DNS : UDP port 53```

- What is the name of the DNS rpm package
``` bind```
``` bind-libs-9.8.2-0.62.rc1.el6_9.5.x86_64```

- WHat is the configuration file for DNS and its location?
``` /etc/named.conf```

- List types of filesystems
``` ext3, ext4, xfs, butterfs```

- List four distros of linux
``` fedora, ubuntu, mint, redhat, centos```

- Check if package is installed?
``` rpm -qa |grep $packagename```

- How to check previously ran commands,
```history, ctrl+r for recursive search ```

- Where are the zone files located?
```/var/named```

- Current working directory
```pwd```

- Check file permissions
``` ls -l```

- How to find filetype of file
```file $filename```

- How to find where commands located
``` which $command```

- How to change file permissions?
``` chmod 666 $filename```

- How to command is to read top part of the file
``` head ```


- How to view bottom of the file
``` tail ```

- How to check  MTU, ip AND MACADDR
```ifconfig  - a```
```ip ad```

- How to count total lines of file
``` wc -l filename```

- How to create a group
```groupadd group```

- Reboot system with init command?
```init 6```

- How to view all messgaes generated by system since last reboot
```journalctl ```

- Two diffent ways of checking kernel related messgaed
```dmesg```
```journalctl -k```

- How to keep checking logs as they come in?
``` tail -f /var/log/messages```

- OS installation related logs?
``` /var/log/anaconda/anaconda.log```
```ks.log```

-To improve performance of a the system, how can you set limit of processes for superuser safely?
```unlimit -u unlimited```

- How can you change resource limits for users logged in via PAM?
```/etc/security/limits.conf```

- How to check ulimit of a user?
```ulimit -a```

- How to check and increase limits of opened files in linux?
