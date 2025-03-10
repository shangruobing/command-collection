# Python

Python is a programming language that lets you work more quickly and integrate your systems more effectively.

```shell
# install
apt install -y python3.12

# source code complie and install
apt-get install gcc build-essential
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev
wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
make && make install
PATH=$PATH:$HOME/bin:/usr/local/python3.7.3/bin

# run python file
python app.py

# run python module
python -m venv venv
python -m pip install tqdm
```

> https://www.python.org/

## line-profiler

```shell
pip install line-profiler

kernprof -l -v script.py
```

