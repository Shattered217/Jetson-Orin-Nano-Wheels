# Jetson Orin Nano / aarch64 Deep Learning Wheels

This repository hosts pre-built Python wheels (`.whl`) for PyTorch, TorchVision, Torchaudio, and TensorRT specifically compiled for NVIDIA Jetson Orin Nano (ARM64 / aarch64) with JetPack 6.2.1(rc1), CUDA 12.6.

---

## 📦 Included Packages

| Package | Version | Notes |
|---------|---------|------|
| PyTorch | 2.3.0a0 | Built from source for CUDA 12.6, includes ARM64 optimizations |
| TorchVision | 0.18.0a0 | Compatible with PyTorch 2.3 |
| Torchaudio | 2.3.0 | Minimal build, CTC decoder and FFmpeg disabled to avoid compilation issues on Jetson |
| TensorRT | 10.3.0 | Python wheel for CUDA 12.5/12.6 |
| OpenCV | 4.11.0 | Precompiled wheel for aarch64; **requires `numpy<2`** for compatibility |

---

## ⚙️ System Requirements

- NVIDIA Jetson Orin Nano or compatible Jetson device
- JetPack 6.2.1(rc1)
- CUDA 12.6
- cuDNN 9 (for CUDA 12.6)
- Python 3.10
- `pip` >= 23.0

> Make sure your Python virtual environment is active before installing.

---

## 💻 Installation

```python
# 1. (Optional) Create and activate a new UV environment
uv venv jetson-dl python=3.10
source jetson-dl/bin/activate

# 2. Install precompiled PyTorch, TorchVision, and TorchAudio wheels
uv pip install ./torch-2.3.0a0+git97ff6cf-cp310-cp310-linux_aarch64.whl
uv pip install ./torchvision-0.18.0a0+6043bc2-cp310-cp310-linux_aarch64.whl
uv pip install ./torchaudio-2.3.0+952ea74-cp310-cp310-linux_aarch64.whl

# 3. Install the precompiled TensorRT wheel
uv pip install ./tensorrt-10.3.0-cp310-none-linux_aarch64.whl

# 4. Install OpenCV (note: ensure numpy<2 is installed)
uv pip install numpy<2
uv pip install ./opencv_python-4.11.0-py3-none-any.whl

# 4. Verify the installation
python -c "import torch; import torchvision; import torchaudio; import tensorrt; print('Installation successful!')"
```

## ✅ YOLO Check
After installation, you can verify that your Ultralytics YOLO environment is correctly set up:

# Make sure your venv is active
```
yolo check
```

Example output should include:
```
Ultralytics 8.3.204 🚀 Python-3.10.18 torch-2.3.0a0+git97ff6cf CUDA:0 (Orin, 7620MiB)
Setup complete ✅ (6 CPUs, 7.4 GB RAM, 90.9/232.2 GB disk)

OS                     Linux-5.15.148-tegra-aarch64-with-glibc2.35
Environment            Linux
Python                 3.10.18
Install                pip
Path                   /home/ros/yolo/venv/lib/python3.10/site-packages/ultralytics
RAM                    7.44 GB
Disk                   90.9/232.2 GB
CPU                    ARMv8 Processor rev 1 (v8l)
CPU count              6
GPU                    Orin, 7620MiB
GPU count              1
CUDA                   12.6

numpy                  ✅ 1.26.4>=1.23.0
matplotlib             ✅ 3.10.6>=3.3.0
opencv-python          ✅ 4.11.0>=4.6.0
pillow                 ✅ 11.3.0>=7.1.2
pyyaml                 ✅ 6.0.3>=5.3.1
requests               ✅ 2.32.5>=2.23.0
scipy                  ✅ 1.15.3>=1.4.1
torch                  ✅ 2.3.0a0+git97ff6cf>=1.8.0
torch                  ✅ 2.3.0a0+git97ff6cf!=2.4.0,>=1.8.0; sys_platform == "win32"
torchvision            ✅ 0.18.0>=0.9.0
psutil                 ✅ 7.1.0
polars                 ✅ 1.33.1
ultralytics-thop       ✅ 2.0.17>=2.0.0
```

🔗 References

[PyTorch for Jetson](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048)

[TensorRT 10.3](https://github.com/NVIDIA/TensorRT/tree/release/10.3/python)

[Install OpenCV on Jetson Orin Nano](https://qengineering.eu/install-opencv-on-orin-nano.html)
