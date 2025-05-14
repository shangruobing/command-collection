# Pip

Pip is the package installer for Python. You can use pip to install packages from the Python Package Index and other indexes.

```shell
# View the version
pip --version

# Upgrade
python -m ensurepip --upgrade
pip install --upgrade pip

# List installed Python packages
pip list

# Install the pandas package using pip
pip install pandas

# Install tensorflow from the Tsinghua University mirror
pip install tensorflow -i https://pypi.tuna.tsinghua.edu.cn/simple

# Install tensorflow from the University of Science and Technology of China mirror
pip install matplotlib -i https://pypi.mirrors.ustc.edu.cn/simple

# Install torch and specify a custom cache directory
pip install torch --cache-dir=/cache

# Install scipy with no cache
pip install scipy --no-cache-dir

# Trust the SSL
pip install icecream --trusted-host pypi.tuna.tsinghua.edu.cn

# Show information about the numpy package
pip show numpy

# Export currently installed packages to requirements.txt
pip freeze > requirements.txt

# Install dependencies listed in requirements.txt
pip install -r requirements.txt

# Install the package without installing its dependencies
pip install package --no-deps

# Remove all packages
pip freeze | xargs pip uninstall -y

# Remove all packages (Windows)
pip freeze | ForEach-Object { pip uninstall $_ -y }
```

### Set Default Mirror

```shell
# Linux and Mac
mkdir -p ~/.config/pip
echo "[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple" > ~/.config/pip/pip.conf

# Windows
mkdir C:\Users\%USERNAME%\pip
echo [global] > C:\Users\%USERNAME%\pip\pip.ini
echo index-url = https://pypi.tuna.tsinghua.edu.cn/simple >> C:\Users\%USERNAME%\pip\pip.ini

# Check
pip config list
```

