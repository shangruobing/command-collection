# Nvidia

```shell
# check the usage of GPU
nvidia-smi

# format the output
nvidia-smi --query-gpu=name --format=csv,noheader

# check the usage of GPU every 5 seconds
watch -n 5 -d nvidia-smi

# check the Nvidia driver version
nvcc --version
python -c 'import torch; print(torch.__version__)'
python -c 'import torch; print(torch.version.cuda)'
python -c 'import torch; print(torch.cuda.is_available())'

# install the Nvidia driver
conda install cuda-nvcc -c "nvidia/label/cuda-12.1.0"
```

> https://developer.nvidia.cn/cuda-downloads
