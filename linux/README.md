# Linux

## System

```shell
# 查看发行版本
cat /proc/version
cat /etc/os-release
uname
uname -a
```

## Base
```shell
# 日期
date
# 日历
cal
# 退出
exit
# 确定文件类型
file picture.jpg
# 创建目录
mkdir dir1 dir2
# 显示命令的类型
type command
# 显示可执行程序的位置
which command
# 获得shell内置命令的帮助文档
help command
# 显示程序的手册
man program
# 显示命令的简要描述
whatis command
# 别名
alias name='string'
# 删除别名
unalias name
# 查看所有别名
alias
# 清屏
clear
# 历史
hisotry
# 使用历史记录某一行
!line-number
# 查找历史记录
history | grep python
```

## Wildcard

| pattern       | meaning        |
| ------------- | -------------- |
| *             | 0、1、任意多个 |
| ?             | 1、单个        |
| [characters]  | 属于其中       |
| [!characters] | 不属于其中     |
| [:alnum:]     | 字母或数字     |
| [:alpha:]     | 字母           |
| [:digit]      | 数字           |
| [:lower:]     | 小写字符       |
| [:upper:]     | 大写字符       |

## Change Directory

```shell
# 查看当前工作目录
pwd
# 改变目录
cd
# 将工作目录改变成先前的工作目录
cd -
# 用户名目录
cd ~
# 主目录
cd
```

## List Files

```shell
# 列出目录内容
ls
# 列出目录内容 包含隐藏文件.
ls -a
# 列出指定目录
ls ~ /usr
# 详细列出
ls -l
# 时间排序
ls -t
ls -t --reverse
# 文件大小排序
ls -S
```

## Editor

```shell
# 查看文件
less filename
more filename
cat filename

# 向前查找指定的字符
/char
# 查找下一个
n
# 退出
q
```

## Copy and Move

````shell
# 复制所有HTML到指定位置
cp -u *html target
# 将dir1中的所有文件复制的dir2中，dir2必须存在
cp dir1/* dir2
# 将dir1目录（及其内容）复制到dir2目录中
cp –r dir1 dir2
# 复制文件到当前目录
cp file .

# 重命名
mv item1 item2

# 删除
rm file1 file2
rm -r dir
````

## Link

```shell
# 创建硬链接
ln file link
# 创建符号链接
ln -s item link
```

## Redirect

```shell
# 文件描述符：标准输入文件、标准输出文件、标准错误文件 0、1、2
# 标准输出重定向
ls > output.txt
# 删除一个文件内容或者创建一个新的空文件
> output.txt
# 尾部追加内容
echo hello >> output.txt
# 标准错误重定向
error 2> error.txt
# 将标准输出和标准错误重定向到同一个文件
ls > output.txt 2>&1
ls &> output.txt
# 忽略错误输出，位桶（bit bucket）
ls 2> /dev/null
# 合并文件
cat file1 file2 file3
```

## Pipeline

````shell
# 把一个命令的标准输出传送到另一个命令的标准输入中
ls | cat
# 排序
ls | sort | cat
# 去重
ls | uniq | cat
# 查看去重
ls | uniq -d | cat
# 字数统计，word count
wc filename
# 查找包含zip的文件
ls | grep zip | cat
# 查找不包含zip的文件
ls | grep -v zip | cat
# 从标准输入读取数据，并同时输出到标准输出和文件
ls | tee output.txt | grep zip
````

## Preview

```shell
# 打印文件的开头部分
head -n 5 output.txt
# 打印文件的/结尾部分
tail -n 5 output.txt
# 持续监视文件变化
tail -f output.txt
```

## Echo

```shell
echo hello
# 所有文件名
echo *
# A开头的文件
echo A*
# 隐藏文件
echo .*
# 算术表达式
echo $((1+2))
# 打印例子
echo Number_{1..5}
# Number_1 Number_2 Number_3 Number_4 Number_5
echo {Z..A}
# Z Y X W V U T S R Q P O N M L K J I H G F E D C B A
# 打印变量
echo $USER
# 查看环境变量
printenv | cat
# 命令替换
echo $(ls)
# 纯文本使用单引号
echo '$(ls)'
# 输出转义字符
echo "Time's up\n"
```

## Shortcut keys

| Shortcut | Meaning                              |
| -------- | ------------------------------------ |
| Ctrl-A   | 移动光标到行首                       |
| Ctrl-E   | 移动光标到行尾                       |
| Ctrl-Q   | 删除整行                             |
| Ctrl-L   | 清屏                                 |
| Ctrl-D   | 删除光标处的字符                     |
| Ctrl-T   | 使光标处的字符和它前面的字符对调位置 |
| Tab      | 自动补齐                             |

## Permission

`-rwxrw-r--` 文件类型/所有者权限/组权限/其他用户权限

`#`为超级管理员、`$`为用户

0为`-`、1为`x`、2为`w` 、4为`r`

u为`user`、g为`group`、o为`others`、a为`all` 、默认all

`+`表示添加一种权限、`-`表示删除一种权限、`=`表示只有该权限可用

```shell
# 显示身份标识
id
# 更改文件模式 授予所有权限
chmod 777 output.txt
# 默认权限
umask
# 以其他用户身份来运行
su
# 使用超级管理员权限
sudo -l
# 更改文件所有者和所属群组
chown [ower][:[group]] file …
chown tim output.txt
# 更改文件所属群组
chgrp
# 修改密码
passwd [user]
```

## Process

Daemon Program `守护程序`

Prcesss ID `进程ID`

```shell
# 查看进程信息 TTY:teletype电传打字机代表进程的控制终端
ps
# 显示所有进程
ps x
# 更详细的信息
ps aux
# 动态进程信息 3s更新一次 q退出
top
# 更方便的进程信息
htop
# 使进程在后台运行
program &
# 查看所有作业
jobs
# 使进程回到前台运行 jobspec进程编号
fg %jobspec
# 中断进程Ctrl-C 暂停进程Ctrl-Z
# 使进程后台运行
bg %jobspec
# 终止进程
kill %jobspec
kill PID1 PID2
kill -KILL PID
kill -9 PID
# 发送信号给多个进程
killall name
```

## Nohup

nohup(no hang up)用于在后台运行另一个命令，并将其与当前的 Shell 会话分离。这确保即使用户注销或终端关闭，命令仍然会继续运行。使用 `nohup` 会在程序执行过程中忽略挂起信号，而 `&` 只是将命令放入后台执行，但不会忽略挂起信号。因此，在需要长时间运行且不受终端关闭影响的情况下，应该使用 `nohup`。

> \> 标准输出重定向
> 2>&1 将标准错误重定向到与标准输出相同的位置
> & 将进程发送到后台运行

```shell
nohup python main.py > log.txt 2>&1 &
nohup java -jar backend-0.0.1.jar > log.txt 2>&1 &
```

## Environment

`~/.bash_profile` or `~/.bashrc` or `~/.zshrc`

```shell
# 查看环境变量
printenv
# 查看具体变量
printenv PATH
# 查看Shell变量和花氨基比林
set
# 查看单个变量
echo $HOME
# 查看别名
alias
# 激活配置文件
source ~/.bash_profile
```

## Vim

- 插入模式  `I`
- 光标模式 复制  `yy` 粘贴 `p`

- 命令模式 `ESC`
  - 退出 `:q`
  - 保存 `:w`
  - 另存为 `:w filename`
  - 切换到下一个文件 `:n`
  - 切换回上一个文件 `:N`
  - 添加一个文件到编辑会话 `:e output.txt`
  - 查看正在编辑的文件列表 `:buffers`

```shell
# 创建空白文件
vim
# 打开多个文件
vim file1 file2
```

## Software Package Management

### Debian(.deb)

Debian、Ubuntu、Xandros、Linspire

高级工具`apt-get`

低级工具`dpkg`

```shell
# Debian
# 查询
apt-get update apt-cache search name
# 安装
apt-get update apt-get install package_name
dpkg --install package_file
# 删除
apt-get remove package_nam
# 更新
apt-get update; apt-get upgrade
dpkg --install package_file
# 列出已安装的软件包列表
dpkg --list
# 判断软件包是否安装
dpkg --status package_name
# 显示已安装软件包的相关信息
apt-cache show package_name
# 查看某具体文件由哪个软件包安装得到
dpkg --search file_name
```

### Red Hat(.rpm)

Fedora、CentOS、Red Hat Enterprise Linux、openSUSE、 Mandriva、PCLinuxOS

高级工具`npm`

低级工具`yum`

```shell
# Red Hat
# 查询
yum seach name
# 安装
yum install package_name
rpm -i package_file
# 删除
yum erase package_name
# 更新
yum update
rpm -U package_fil
# 列出已安装的软件包列表
rpm -qa
# 判断软件包是否安装
rpm -q package_name
# 显示已安装软件包的相关信息
yum info package_name
# 查看某具体文件由哪个软件包安装得到
rpm -qf file_name
```

## Memory

```shell
# 查看可用内存
free
free -h
```

## Disk

```shell
# 查看可用磁盘大小
df
df -h
# 查看当前目录
du -h .
du -sh .
# 查看文件夹大小
du -h directory
du -h | sort -h
# 查看子文件夹
du -h --max-depth=1
# 查看已挂载的文件系统列表
mount
# 卸载
umount device_name
# 磁盘分区
fdisk device_name
# 创建新的文件系统
mkfs -t ext3 device_name
# 测试、修复文件系统
fsck device_name
# 格式化
fdformat device_name
```

## Curl

```shell
# 查找僵尸进程
ps -A -ostat,ppid,pid,cmd |grep -e '^[Zz]'

# CURL
curl http://127.0.0.1:8000/api/ping

curl -X POST \
    -H "Content-Type: application/json" \
    -d '{"question": "hello"}' \
    http://127.0.0.1:8000/api/say-hello

# 查看端口占用

# 杀死进程
kill -9 PID
```

## Network

```shell
# 查看本机IP地址
ifconfig
# 如果要检查端口号为80的情况，可以运行
netstat -an | grep 80
# 查看特定端口防火墙的规则
iptables -L INPUT -n -v | grep 80
iptables -S | grep 80
# 解析域名
nslookup your_domain
dig your_domain
# ufw Uncomplicated FireWall
systemctl status ufw
systemctl start ufw
systemctl stop ufw
# 发送数据包
ping github.com
# 跟踪网络数据包的传输路径
traceroute github.com
# 检查网络设置
netstat
# 文件传输协议
ftp fileserver
# 下载工具
wget http://linuxcommand.org/index.php
# 安全登录远程计算机
ssh username@remote-computer
# 安全传输文件
scp username@remote-computer:doc.txt .
sftp remote-computer
```

## File Search

```shell
# 查找文件
find directory
# 查找文件
find directory -type f
# 查找目录
find directory -type d
# 查找大于1M的JPG文件
find directory -type f -name "*.JPG" -size +1M
# 查找并删除
find directory -type f -name '*.BAK' -delete
```

## Compress

````shell
sudo apt-get install zip
sudo apt-get install unzip
# compress
zip filename.zip filename1 filename2
zip -r dir_name.zip dir_name
# split the file
split -b 100M -d filename.zip new_name_
# decompress
unzip filename.zip
# add file into zip
zip archive.zip newfile.txt
# check content
zipinfo archive.zip
````

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

