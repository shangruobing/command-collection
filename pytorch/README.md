# Pytorch

PyTorch is an optimized tensor library for deep learning using GPUs and CPUs.

```shell
# Install
pip install torch torchvision torchaudio
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia

# Validate
python -c 'import torch; print(torch.__version__)'
python -c 'import torch; print(torch.version.cuda)'
python -c 'import torch; print(torch.cuda.is_available())'
python -c 'import torch; print(torch.cuda.current_device())'

# Analysis
python -m torch.utils.bottleneck script.py
```

## GPU Resource

```python
print("Torch version:", torch.__version__)
print("Torch cuda version:", torch.version.cuda)
print("CUDA available:", torch.cuda.is_available())
print("Current device:", torch.cuda.current_device())
print("Device name:", torch.cuda.get_device_name(0))

# Analysis GPU memory allocated
print(torch.cuda.memory_allocated(0))
```

> https://pytorch.org/
