# Python

```shell
# install
apt-get install install python3 python3-dev

# source code complie and install
apt-get install gcc build-essential
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev

wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
make && make install
PATH=$PATH:$HOME/bin:/usr/local/python3.7.3/bin

# run python module
python -m venv venv
python -m pip install tqdm
```
