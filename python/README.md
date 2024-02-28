# Python3.7

```shell
#失败
sudo apt-get install python3.7
#手动安装
apt-get install gcc build-essential
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev  libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev   xz-utils tk-dev

wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
make && make install
PATH=$PATH:$HOME/bin:/usr/local/python3.7.3/bin

```