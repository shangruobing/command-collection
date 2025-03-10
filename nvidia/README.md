# Nvidia

NVIDIA CUDA (Compute Unified Device Architecture) is a parallel computing platform and programming model developed by NVIDIA. It enables developers to use NVIDIA graphics processing units (GPUs) for general-purpose processing. CUDA provides developers with a powerful and efficient way to harness the computing power of GPUs for a wide range of applications beyond traditional graphics rendering.

```shell
# check the usage of GPU
nvidia-smi

# format the output
nvidia-smi --query-gpu=name --format=csv,noheader

# check the usage of GPU every 5 seconds
watch -n 5 -d nvidia-smi

# check the Nvidia driver version
nvcc --version

# install the Nvidia driver
conda install cuda-nvcc -c "nvidia/label/cuda-12.1.0"

# install cuda 12.3 on ubuntu
wget https://developer.download.nvidia.com/compute/cuda/12.3.0/local_installers/cuda_12.3.0_545.23.06_linux.run
sudo sh cuda_12.3.0_545.23.06_linux.run
echo 'export PATH=/usr/local/cuda-12.3/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-12.3/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

> https://developer.nvidia.cn/cuda-downloads

> https://developer.nvidia.com/cuda-toolkit-archive
