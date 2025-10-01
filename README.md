# Jetson Orin Nano / aarch64 Deep Learning Wheels

This repository hosts pre-built Python wheels (`.whl`) for PyTorch, TorchVision, Torchaudio, and TensorRT specifically compiled for NVIDIA Jetson Orin NX (ARM64 / aarch64) with JetPack 6.0 (L4T R36.2/36.3), CUDA 12.6.

---

## 📦 Included Packages

| Package | Version | Notes |
|---------|---------|------|
| PyTorch | 2.3.0a0 | Built from source for CUDA 12.6, includes ARM64 optimizations |
| TorchVision | 0.18.0a0 | Compatible with PyTorch 2.3 |
| Torchaudio | 2.3.0 | Minimal build, CTC decoder and FFmpeg disabled to avoid compilation issues on Jetson |
| TensorRT | 10.3.0 | Python wheel for CUDA 12.5/12.6 |

---

## ⚙️ System Requirements

- NVIDIA Jetson Orin NX or compatible Jetson device
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
uv install ./torch-2.3.0a0+git97ff6cf-cp310-cp310-linux_aarch64.whl
uv install ./torchvision-0.18.0a0+6043bc2-cp310-cp310-linux_aarch64.whl
uv install ./torchaudio-2.3.0+952ea74-cp310-cp310-linux_aarch64.whl

# 3. Install the precompiled TensorRT wheel
uv install ./tensorrt-10.3.0-cp310-none-linux_aarch64.whl

# 4. Verify the installation
python -c "import torch; import torchvision; import torchaudio; import tensorrt; print('Installation successful!')"
```

🔗 References

[PyTorch for Jetson](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048)
