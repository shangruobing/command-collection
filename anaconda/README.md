# Anaconda

```shell
# check version
conda --version

# update conda
conda update conda

# show config
conda config --show

# add default channel
conda config --add channels conda-forge

# disable auto activate base env
conda config --set auto_activate_base false

# list all envs
conda env list

# create a new env
conda create -n env_name python==3.9

# activate
conda activate env_name

# deactivate
conda deactivate

# remove the env
conda env remove --name env_name

# create env in the specified path
conda create --prefix /home/user/conda-env python=3.9

# configuration
vim .condarc

# export and install the dependency
conda env export > environment.yml
conda env create -f environment.yml
conda install --file requirements.txt

# offline package
conda pack -n env_name -o env_name.tar.gz
# load offline package
tar -xzf env_name.tar.gz -C env_name
source env_name/bin/activate
conda-unpack

# remove temp and cache
conda clean --all

# clone the env
conda create --name new_env --clone old_env

# check channels
conda config --get channels

# recover the default channel
conda config --remove-key channels

# add mirror
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda
```

