# Checking Disk Space and Deleting Large files

I had a disk space issue at work where the machine had some large files eating all the disk spaces. I had found out a couple hacks to help me find those files and deleting them more efficiently.

## Disk Utility du
* Use `du -sh` to check the used disk space in the current directory .
* Use `du -sh *` to check the used disk space of all files in the current directory . (non recursive)
* Use `du -sh * | sort -h` to check the used disk space of all files in the current directory . (non recursive) and sort by file sizes where the largest file are at the bottom of the output
* Use `du -s` to check the used disk space in the current directory recursively
* `du` also has a couple useful options such as `--exclude` to exclude files and `--time` to show the last modified time of the files

## find!
* Use `find . -type f -size +100M` to find files in the current directory . recursively
* You can change the directory to whatever you want. (e.g. glob support `./*.log`)
* Pass in option `-delete` to delete all the files found in your specified directory
