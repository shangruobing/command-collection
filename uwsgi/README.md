# uwsgi

```shell
sudo apt-get install libpcre3 libpcre3-dev
pip3.7 install uwsgi --no-cache-dir

sudo ln -s /home/ubuntu/.local/bin/uwsgi  /usr/bin/uwsgi

uwsgi --http :8000 --module NFQA.wsgi

ps -A 查看所有进程
pkill 进程号
sudo pkill -f uwsgi -9

uwsgi --ini uwsgi.ini
```