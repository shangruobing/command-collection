# uwsgi

```shell
# check the version
uwsgi --version

# source code complie
sudo apt-get install libpcre3 libpcre3-dev
pip install uwsgi --no-cache-dir

# precomplie file recommended
pip install pyuwsgi --no-cache-dir

sudo ln -s /home/ubuntu/.local/bin/uwsgi  /usr/bin/uwsgi

# launch server
uwsgi --ini uwsgi.ini

# simple launch
uwsgi --http :8000 --module yourfile.wsgi

# stop server
uwsgi --stop /path/to/uwsgi.pid
# or
ps ax | grep uwsgi
sudo kill -9 pid
```

## Example

```ini
# uwsgi.ini
[uwsgi]
# 指定可调用的应用程序对象
callable = app
# 监听所有网络接口的8000端口
http = 0.0.0.0:8000
# 指定执行文件所在目录
chdir = /app/src
# 指定WSGI应用程序的入口文件
wsgi-file = src/main.py
# 指定WSGI应用程序的模块和可调用对象
module = main:app
# 启用Master进程管理器
master = true
# 设置工作进程数量
processes = 2
# 每个工作进程的线程数量
threads = 4
# 设置UNIX套接字的权限
chmod-socket = 660
# 在接收到SIGTERM信号时立即退出
die-on-term = true
# 自动清理UNIX套接字
vacuum = true
# 启用线程支持
enable-threads = true
# 后台运行uWSGI进程，并将日志输出到指定文件或UDP服务器
daemonize = /app/logs/uwsgi.log
# 在Master进程失去权限之前，将其PID写入指定文件
pidfile = /app/logs/uwsgi.pid
```
