# Anaconda

```shell
# disable auto activate base env
conda config --set auto_activate_base false
# list all env
conda env list
# create a new env
conda create -n env_name python==3.9
# activate
conda activate env_name
# deactivate
conda deactivate
# remove the env
conda env remove --name env_name
# set env path
conda create --prefix /home/user/conda-env python=3.9.2
# channels
conda config --remove-key channels
# configuration
vim .condarc
# export and install the dependency
conda env export > environment.yml
conda env create -f environment.yml
conda install --file requirements.txt
# offline package
conda pack -n env_name -o env_name.tar.gz
tar -xzf env_name.tar.gz -C env_name
source env_name/bin/activate
conda-unpack
# remove temp and cache
conda clean --all
# clone the env
conda create --name new_env --clone old_env
```

