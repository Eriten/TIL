# Opened File Descriptors

## What is a file descriptor
A file descriptor is a placeholder/indication for accessing IO/Network resources. This could be opening a file, connecting to another machine via SSH, or connecting to a socker server

## Useful commands
* `lsof` is the program for listing opened files and it lists what processes are using using file descriptors for whatever purpose
* To check how many opened files a system can handle for all users and processes, `cat /proc/sys/fs/file-max`
* To check how many opened files a user can handle. In the case of the jenkins user, use the following two commands to check the soft and hard limit (Difference between soft and hard limit in http://serverfault.com/questions/265155/soft-limit-vs-hard-limit)
  * `su - jenkins -c "ulimit -Sn"`
  * `su - jenkins -c "ulimit -Hn"`
* To check how many the file descriptors are used currently, `lsof | wc -l`


## Changing File Descriptors limit
We can temporarily increase the soft limit of opened file descriptors for a specific user in with `ulimit -Sn <NUMBER>` in a terminal session logged in as that user. 

A permanent solution is to modify `/etc/security/limits.conf` to have the following entries if you want to set the opened file descriptors limit for the jenkins user. You can also specify the limit for all users except root with asterisk *

```
jenkins         soft    nofile          4096
jenkins         hard    nofile         10240
````
