# Anaconda

```shell
# disable auto activate base env
conda config --set auto_activate_base false
# list all env
conda env list
# create a new env
conda env create env_name
# activate
conda activate env_name
# deactivate
conda deactivate
# remove the env
conda env remove env_name
# set env path
conda create --prefix /home/user/conda-env python=3.9.2
# pip
pip install tensorflow -i https://pypi.tuna.tsinghua.edu.cn/simple --cache-dir=/cache
# export and install the dependency
conda env export > environment.yml
conda env create -f environment.yml
conda install --file requirements.txt
# export and install the dependency
pip freeze > requirements.txt
pip install -r requirements.txt
```
