# Nvidia

```shell
nvidia-smi
nvidia-smi --query-gpu=name --format=csv,noheader

nvcc --version
python -c 'import torch; print(torch.version.cuda)'
python -c 'import torch; print(torch.cuda.is_available())'

watch -n 5 -d nvidia-smi

conda install cuda-nvcc -c "nvidia/label/cuda-12.1.0"
```

> https://developer.nvidia.cn/cuda-downloads
