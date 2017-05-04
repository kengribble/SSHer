# README #

ssher - used to ssh to multiple systems

### What is this repository for? ###

* perl program called ssher

### How do I get set up? ###

* requires perl
* download and ensure the #!/usr/local/perl is set to the correct directory for your system

### Useage ###
ssher useage: 
	ssher [-v] -f file [-l login] command
	   -v is verbose output
	   -f is a file name with a required list of IP addresses or hostnames in that file
		command is the required command to send to the list of nodes with ssh
	   -l is a login name - if not used the login name of the user executing the command is used

### file example ###
This is an example file one might use with ssher:

```
my.host.com
your.host.net
192.168.1.123
another.host.com
10.0.2.37
```

### TODO ###

* figure out how to add the hostnames to the command line -- no need for file
* consider how to do quiet mode - show nothing normally and add a -h to display hostnames, or 
	* -q quiet mode -- displays only the returns from the ssh command, no hostnames shown
	* -qq -- super quiet mode, displays nothing

