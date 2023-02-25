# Colab 
## RAM
```python
from psutil import virtual_memory
ram_gb = virtual_memory().total / 1e9
print('Your runtime has {:.1f} gigabytes of available RAM\n'.format(ram_gb))

if ram_gb <20:
    print('Not using a high-RAM runtime')
else:
    print('You are using a high-RAM runtime!')
```
## GPU information
```python
gpu_info = !nvidia-smi
gpu_info = '\n'.join(gpu_info)
if gpu_info.find('failed') >=0:
    print('Not connected to a GPU')
else:
    print(gpu_info)
```
# Pytorch
Before installing new version of Pytorch, please uninstall old version
```shell
pip uninstall torch torchvision torchaudio
```
## Pytorch-CPU
### Install for Pytorch-CPU
```shell
pip3 install torch torchvision torchaudio  # For Windows-Pip-Python-CPU
```
```shell
conda install pytorch torchvision torchaudio cpuonly -c pytorch # For Windows-Conda-Python-CPU
```
### Test code for Pytorch-CPU
```python
import torch
print('pytorch版本：', torch.__version__)
```
## Pytorch-GPU
### Install for Pytorch-GPU (e.g CUDA11.7) (recommended)
```shell
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117 # For Windows-Pip-Python-CUDA11.7
```
```shell
conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia # For Windows-Conda-Python-CUDA11.
```
### Test code for Pytorch-GPU
```python
import torch
print('pytorch版本：', torch.__version__)
print('cuda版本：', torch.version.cuda)
print('cudnn版本号：', torch.backends.cudnn.version())
ngpu = 1
device = torch.device("cuda:0" if (torch.cuda.is_available() and ngpu > 0) else "cpu")
print('cuda设备名：', device)
print('gpu名称：', torch.cuda.get_device_name(0))
```
# TensorFlow
## t
