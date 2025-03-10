# Pytorch

PyTorch is an optimized tensor library for deep learning using GPUs and CPUs.

> https://pytorch.org/

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

## Torch Profile

```python
import torch
from torch.profiler import profile, record_function, ProfilerActivity

activities = [ProfilerActivity.CPU, ProfilerActivity.CUDA, ProfilerActivity.XPU]
sort_by_keyword = "cuda" + "_time_total"

with profile(activities=activities, record_shapes=True, profile_memory=True) as prof:
    with record_function("model_inference"):
        model = Model().to("cuda")
        shape = (4, 3, 128, 128)
        input_tensor = torch.rand(shape).to("cuda")
        output_features = model(input_tensor)
        print("Output features shape:", output_features.shape)

key_averages = prof.key_averages(group_by_input_shape=True)
print(key_averages.table(sort_by=sort_by_keyword, row_limit=10))
```
