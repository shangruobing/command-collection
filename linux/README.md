# Linux

```shell
# 查找僵尸进程
ps -A -ostat,ppid,pid,cmd |grep -e '^[Zz]'

# 后台挂起运行
nohup python main.py > log.txt 2> error.txt & echo $! > pid.txt

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