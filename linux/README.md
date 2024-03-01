# Linux

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

# 0、1、任意多个
*
# 1 单个
?
# 属于其中
[characters]
# 不属于其中
[!characters]
# 字母或数字
[:alnum:] 
# 字母
[:alpha:] 
# 数字
[:digit] 
# 小写字符
[:lower:]
# 大写字符
[:upper:]
```

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

## Nohup

nohup(no hang up)用于在后台运行另一个命令，并将其与当前的 Shell 会话分离。这确保即使用户注销或终端关闭，命令仍然会继续运行

> \> 标准输出重定向
> 2>&1 将标准错误重定向到与标准输出相同的位置
> & 将进程发送到后台运行

```shell
nohup python main.py > log.txt 2>&1 &
nohup java -jar backend-0.0.1.jar > log.txt 2>&1 &
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
```

## Memory

```shell
# 查看可用内存
free
```

## Disk

```shell
# 查看可用内存
df
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
lsof -i :8000
# 杀死进程
kill -9 PID
```

