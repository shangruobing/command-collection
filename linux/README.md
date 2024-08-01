# Linux

Linux is an operating system that evolved from a kernel created by Linus Torvalds when he was a student at the University of Helsinki. Generally, it is obvious to most people what Linux is. However, both for political and practical reasons, it needs to be explained further. To say that Linux is an operating system means that it's meant to be used as an alternative to other operating systems, Windows, Mac OS, MS-DOS, Solaris and others. Linux is not a program like a word processor and is not a set of programs like an office suite. Linux is an interface between computer/server hardware, and the programs which run on it.

## System Information

```shell
# View the system version
cat /proc/version
cat /etc/os-release

# View the system information
uname
uname -a
```

## Basic Commands

```shell
# View the current date
date

# View the current calendar
cal

# Exit the current shell
exit

# View the file type
file picture.jpg

# Create directories
mkdir dir1 dir2

# Show the type of command
type command
which command

# Show the manual of the shell built-in command
help command

# Show the manual of the program
# 显示程序的手册
man program

# Show the description of the command
whatis command

# Create a alias
alias name='string'

# Remove a alias
unalias name

# List all alias
alias

# Clean the screen
clear

# Show the history of input
hisotry
# Execute the history command
!line-number
# Search the history command
history | grep python
```

## Wildcard

| pattern       | meaning        |
| ------------- | -------------- |
| \*            | 0, 1, n        |
| ?             | 1, n           |
| [characters]  | Belongs to     |
| [!characters] | Not belongs to |
| [:alnum:]     | Alphanumeric   |
| [:alpha:]     | Alphabetic     |
| [:digit]      | Numeric        |
| [:lower:]     | Lower case     |
| [:upper:]     | Upper case     |

## Change Directory

```shell
# Show the current directory
pwd

# Change the directory
cd

# Change the directory to previous directory
cd -

# Change the directory to the home directory
cd ~

# Change the directory to the root directory
cd
```

## List Files

```shell
# List the files in the current directory
ls

# List the files in the current directory, including hidden files
ls -a

# List the specified directory
ls ~ /usr

# List the files details
ls -l

# List and Sort the files by time
ls -t
ls -t --reverse

# List and Sort the files by size
ls -S
```

## Editor

```shell
# View the file content
less filename
more filename
cat filename

# Find the content in the file
/char
# Find the next content
n
# Quit
q
```

## Copy and Move

```shell
# Copy all html files to the target directory
cp -u *html target

# Copy files in dir to the target directory
cp dir/* target

# Cope the directory to the target directory
cp –r dir target

# Cope the file to the current directory
cp file .

# Fename file
mv file_name new_file_name

# Remove the files
rm file1 file2

# Remove the directory
rm -r dir
```

## Link

```shell
# Create a file link
ln file link

# Create a symbol link
ln -s item link
```

## Redirect

File descriptor:

- 0: Standard input file
- 1: Standard output file
- 2: Standard error file

```shell
# Standard output redirection to a file
ls > output.txt

# Create a new file
> output.txt

# Append the content to the file
echo hello >> output.txt

# Standard error redirection to a file
error 2> error.txt

# Standard output and error redirection to a file
ls > output.txt 2>&1
ls &> output.txt

# Ignore the error with bit bucket
ls 2> /dev/null

# Combine files
cat file1 file2 file3
```

## Pipeline

```shell
# Passes the output of one command to the another command
ls | cat

# Sort
ls | sort | cat

# Unique
ls | uniq | cat

# View Unique Result
ls | uniq -d | cat

# Word count
wc filename

# Find the zip file
ls | grep zip | cat

# Find don't contain the zip file
ls | grep -v zip | cat
```

## Preview

```shell
# View the first 5 lines of the file
head -n 5 output.txt

# View the last 5 lines of the file
tail -n 5 output.txt

# Continuously view the file
tail -f output.txt
```

## Echo

```shell
echo hello

# Show the all files
echo *

# Show the all files start with A
echo A*

# Show the hidden files
echo .*

# Calculate the expression
echo $((1+2))

echo Number_{1..5}
# Number_1 Number_2 Number_3 Number_4 Number_5

echo {Z..A}
# Z Y X W V U T S R Q P O N M L K J I H G F E D C B A

# Show the environment variable
echo $USER

# View the environment variables
printenv | cat

# Command substitution
echo $(ls)

# Show the plain text
echo '$(ls)'

# Show the escape character
echo "Time's up\n"
```

## Shortcut keys

| Shortcut | Meaning                                      |
| -------- | -------------------------------------------- |
| Ctrl-A   | Move the cursor to the beginning of the line |
| Ctrl-E   | Move the cursor to the end of the line       |
| Ctrl-Q   | Clear the all input                          |
| Ctrl-L   | Clear the screen                             |
| Ctrl-D   | Delete the character before the cursor       |
| Ctrl-T   | Adjust the cursor position                   |
| Tab      | Auto complete                                |

## Permission

`-rwxrw-r--` file `type/owner/group/others`

`#` Super admin `$` User

- 0 as `-`
- 1 as`x`
- 2 as`w`
- 4 as`r`

u is `use`, g is `group`, o is `others`, a is `all`, default all

- `+` means add one kind of permission
- `-` means remove one kind of permission
- `=` means set one kind of permission

```shell
# Show the identity of the user
id

# Grant all permissions to the file
chmod 777 output.txt

# Default permission
umask

# Change the user
su

# Use the admin permission
sudo -l

# Change the owner of file
chown [ower][:[group]] file …
chown tim output.txt

# Change the group of file
chgrp

# Modify the password
passwd [user]
```

## Process

```shell
# Show the process status
ps

# Show the all process status
ps x

# Show the all process status with the full format
ps aux

# Display the process tree
top
htop

# run the program in the background
program &

# Show the all jobs
jobs

# Run the program in the background
fg %jobspec
# terminate Ctrl-C pause Ctrl-Z

# Run the program in the background
bg %jobspec

# Kill the process
kill %jobspec
kill PID1 PID2
kill -KILL PID
kill -9 PID
```

## Nohup

`nohup`(no hang up) is used to run another command in the background and separate it from the current `Shell` session. 
This ensures that the command will **continue to run** even if **the user logs out or the terminal is closed**. 
Using `nohup` ignores pending signals during program execution, while `&` simply puts the command into the background but does not ignore pending signals. 
Therefore, `nohup` should be used in cases where you need to **run for a long time and not be affected by terminal shutdowns**.

> \> Starnard output redirection
> 2>&1 Standard error redirection to the same position with standard output
> & Run the command in the background

```shell
nohup python main.py > log.txt 2>&1 &
nohup java -jar backend-0.0.1.jar > log.txt 2>&1 &
```

## Environment Variables

`~/.bash_profile` or `~/.bashrc` or `~/.zshrc`

```shell
# Show environment variables
printenv

# Show the environment variable
printenv PATH
echo $HOME

# set the environment variable
set

# Show the alias
alias

# activate the profile file
source ~/.bash_profile
```

## Vim

- Insert Mode `I`
- Cursor Mode
  - copy `yy`
  - paste `p`
- Command Mode `ESC`
  - quit `:q`
  - write `:w`
  - save as `:w filename`
  - change next file `:n`
  - change previos file `:N`
  - add a file in edit session `:e output.txt`
  - show the edit file list `:buffers`

```shell
# Create a blank file
vim

# Open files
vim file1 file2
```

## Software Package Management

### Debian(.deb)

Debian、Ubuntu、Xandros、Linspire

Advance Tool `apt-get`

Basic Tool `dpkg`

```shell
# Search for a package
apt-get update apt-cache search name

# Install
apt-get update apt-get install package_name
dpkg --install package_file

# Remove
apt-get remove package_nam

# Update
apt-get update; apt-get upgrade

# List
dpkg --install package_file
dpkg --list

# Show the package information
dpkg --status package_name
apt-cache show package_name

# Show the installed package information
dpkg --search file_name
```

### Red Hat(.rpm)

Fedora、CentOS、Red Hat Enterprise Linux、openSUSE、 Mandriva、PCLinuxOS

Advance Tool `npm`

Basic Tool `yum`

```shell
# Search
yum seach name

# Install
yum install package_name
rpm -i package_file

# Delete
yum erase package_name

# Updtae
yum update
rpm -U package_fil

# List
rpm -qa
rpm -q package_name

# Show the package information
yum info package_name

# Show the installed package information
rpm -qf file_name
```

## Memory

```shell
# Show the available memory
free
free -h
```

## Disk

```shell
# Show the avaliable disk
df
df -h

# Show the disk usage in the current directory
du -h .
du -sh .

# Show the disk usage in the directory
du -h directory
du -h | sort -h
du -h --max-depth=1

# Show the mount file list
mount

# Unmount the device
umount device_name

# Create a new partition
fdisk device_name

# Create a new file system
mkfs -t ext3 device_name

# Test and repair the file system
fsck device_name

# Format the device
fdformat device_name
```

## Curl

```shell
# CURL
curl http://127.0.0.1:8000/api/ping

curl -X POST \
    -H "Content-Type: application/json" \
    -d '{"question": "hello"}' \
    http://127.0.0.1:8000/api/say-hello
```

## Network

```shell
# Show the IP address 
ifconfig

# Show the port network status
netstat -an | grep 80

# Show the iptables status
iptables -L INPUT -n -v | grep 80
iptables -S | grep 80

# Decode the domain name
nslookup your_domain
dig your_domain

# ufw Uncomplicated FireWall
systemctl status ufw
systemctl start ufw
systemctl stop ufw

# Send the package
ping github.com

# Trace the route
traceroute github.com

# Check the network connection
netstat

# File transfer protocol
ftp fileserver

# Download the file
wget http://linuxcommand.org/index.php

# SSH remote login
ssh username@remote-computer

# SCP file transfer
scp username@remote-computer:doc.txt .
sftp remote-computer
```

## File Search

```shell
# Find the directory
find directory

# Find the file
find directory -type f

# Find the directory
find directory -type d

# Find the file with the name and size
find directory -type f -name "*.JPG" -size +1M

# Find and delete the file
find directory -type f -name '*.BAK' -delete
```

## Compress

```shell
# Install the zip and unzip
sudo apt-get install zip
sudo apt-get install unzip

# Compress
zip filename.zip filename1 filename2
zip -r dir_name.zip dir_name

# Split the file
split -b 100M -d filename.zip new_name_

# Decompress
unzip filename.zip

# Add file into zip
zip archive.zip newfile.txt

# Check content
zipinfo archive.zip
```

## Auto Start

```sh
# ubuntu
sudo vim /lib/systemd/system/rc-local.service

[Install]
WantedBy=multi-user.target
Alias=rc-local.service

sudo vim /etc/rc.local
#!/bin/bash
echo "start!"

sudo chomod +x /etc/rc.local
```

## Firewall

```shell
# Install the Uncomplicated Firewall (UFW)
sudo apt install ufw

# Show the status of UFW with verbose output
sudo ufw status verbose

# Enable UFW
sudo ufw enable

# Disable UFW
sudo ufw disable

# Set the default incoming policy to deny
sudo ufw default deny

# Allow incoming traffic on port 7474
sudo ufw allow 7474
```
