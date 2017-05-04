# README #

ssher - used to ssh to multiple systems

This is best used when you have your ssh key on mutiple systems and need to run a command on those systems.



## What is this repository for? ##

* perl program called ssher

## How do I get set up? ##

* requires perl
* download and ensure the #!/usr/local/perl is set to the correct directory for your system

## Useage ##
ssher useage: 

	ssher [-v] -f file [-l login] command

	   -v is verbose output

	   -f is a file name with a required list of IP addresses or hostnames in that file
		command is the required command to send to the list of nodes with ssh

	   -l is a login name - if not used the login name of the user executing the command is used

### file example ###
This is an example file one might use with the -f file in ssher:

```
my.host.com
your.host.net
another.host.com
```
## Examples ##

This will run the w command on the systems listed in the file labmachines.list:
```
$ ssher -f labmachines.list w
my.host.com:
 10:44:33 up  5:37,  1 user,  load average: 0.02, 0.01, 0.00
USER     TTY        LOGIN@   IDLE   JCPU   PCPU WHAT
usera   pts/0     08:07   16:41   0.05s  0.05s -tcsh

your.host.net:
 10:44:34 up  5:16,  1 user,  load average: 0.00, 0.02, 0.00
USER     TTY        LOGIN@   IDLE   JCPU   PCPU WHAT
userb   pts/0     10:12   42.00s  0.07s  0.07s -tcsh

another.host.com:
 10:44:34 up  5:39,  3 users,  load average: 0.07, 0.03, 0.00
USER     TTY        LOGIN@   IDLE   JCPU   PCPU WHAT
userc pts/0     09:11    1:33m  0.03s  0.03s -tcsh
userc pts/1     09:11    1:33m  0.03s  0.03s -tcsh
userc pts/2     09:11    1:33m  0.03s  0.03s -tcsh
```

This will run a more complex command line on all the machines in the same list:
```
$ ssher -f labmachines.list "grep MemTotal /proc/meminfo"
my.host.com:
MemTotal:       16337980 kB

your.host.net:
MemTotal:       16337968 kB

another.host.com:
MemTotal:       16337980 kB
``` 

Make sure and use quotes if you are going to use redirects and the like, or you will be 
doing parts of those commands on your localhost. For instance:
```
$ ssher -f labmachines.list "echo 'this and that' > /tmp/testfile && cat /tmp/testfile"
my.host.com: 
this and that

your.host.net: 
this and that

another.host.com: 
this and that
```
