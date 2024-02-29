# uwsgi

```shell
# source code complie
sudo apt-get install libpcre3 libpcre3-dev
pip install uwsgi --no-cache-dir

# precomplie file
pip install pyuwsgi --no-cache-dir

sudo ln -s /home/ubuntu/.local/bin/uwsgi  /usr/bin/uwsgi

uwsgi --http :8000 --module yourfile.wsgi

ps -A 查看所有进程
pkill 进程号
sudo pkill -f uwsgi -9

uwsgi --ini uwsgi.ini
```

## example

```ini
# uwsgi.ini
[uwsgi]
callable = app
http = 0.0.0.0:8000
# 执行文件所在目录
chdir = /app/src
wsgi-file = src/main.py
module = main:app
master = true
processes = 2
threads = 4
chmod-socket = 660
die-on-term = true
vacuum = true
enable-threads = true
# 使进程在后台运行，并将日志打到指定的日志文件或者udp服务器（不会影响nginx日志的输出）
# daemonize = /app/logs/uwsgi.log
# 在失去权限前，将master的pid写到当前文件中
# pidfile = /app/logs/uwsgi.pid
```
