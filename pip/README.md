# Pip

```shell
# List installed Python packages
pip list

# Install the pandas package using pip
pip install pandas

# Install tensorflow from the Tsinghua University mirror
pip install tensorflow -i https://pypi.tuna.tsinghua.edu.cn/simple 

# Install torch and specify a custom cache directory
pip install torch --cache-dir=/cache

# Show information about the numpy package
pip show numpy

# Export currently installed packages to requirements.txt
pip freeze > requirements.txt

# Install dependencies listed in requirements.txt
pip install -r requirements.txt

# Install the package without installing its dependencies
pip install package --no-deps

```

