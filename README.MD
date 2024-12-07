<div align="center">
    <img src="https://github.com/KernFerm/exporting-YOLO/blob/main/Logo/yolo.png" alt="yolo png" width="400"/>
</div>

## Support the Project ⭐

If you find this project useful, please give it a star! Your support is appreciated and helps keep the project growing. 🌟


# YOLO Export Script

This repository contains scripts and commands for exporting YOLO models to different formats, including TensorRT (`.engine`) and ONNX (`.onnx`).

## Requirements

Ensure you have installed the necessary dependencies to run the export script:

- Python 3.11.6 or higher [Python 3.11.6](https://github.com/KernFerm/Py3.11.6installer)
- PyTorch 2.5.1 or higher
- TorchVision 0.20.1
- CUDA 11.8
- ONNX
- Engine
- AMD GPU
- Nvidia GPU
- `YOLOv5` & `YOLOv8` exporting


## Project Structure

```
.
├── .github                           # GitHub configuration files
│   └── dependabot.yml                # Configuration for Dependabot
├── Logo                              # Directory for project logo or images
│   └── yolo.png                      # YOLO logo image
├── models                            # Directory for model-related files
│   └── ...                           # (Files related to YOLO models)
├── ultralytics1                      # YOLO-related utilities and scripts
│   └── utils                         # Directory for additional utility scripts
│       └── additional_requirements.txt  # Additional requirement files (YOLO-specific)
├── utils                             # General utilities and scripts
│   └── additional_requirements.txt   # Utility and helper functions or scripts
├── CODE_OF_CONDUCT.md                # Code of conduct for contributors
├── LICENSE                           # Project license file
├── README.md                         # Main project README with documentation
├── SECURITY.md                       # Security policies and guidelines
├── amd_requirements.txt              # Requirements for AMD GPUs with DirectML
├── commands-to-export.txt            # Useful commands for exporting YOLO models
├── export.py                         # Main script to handle YOLO model export
├── nvidia_requirements.txt           # Requirements for NVIDIA GPUs with CUDA support
├── update_ultralytics.bat            # Batch script to update Ultralytics' YOLO version or utilities
```

### For NVIDIA GPUs (CUDA Support)

You can install the necessary Python packages for NVIDIA GPUs with the following command:

```
pip3 install torch==2.5.1+cu118 torchvision==0.20.1+cu118 torchaudio==2.5.1+cu118 --index-url https://download.pytorch.org/whl/cu118
```

### Files in the Repository

- **commands-to-export.txt:** A file containing useful commands for exporting your YOLO model.
- **export.py:** The Python script responsible for handling the export process.

## Exporting YOLO Models (NVIDIA and AMD GPUs)

### Export to TensorRT Engine (For NVIDIA GPUs)

To export your YOLO model to a TensorRT engine (for NVIDIA GPUs only), use the following command:

```
python .\export.py --weights ./"your_model_path.pt" --include engine --half --imgsz 320 320 --device 0
```
- Replace `"your_model_path"` with the path to your YOLO `.pt` file.
- The `--half` flag enables half-precision inference for faster performance and lower memory usage.
- `--imgsz 320 320` sets the image size to 320x320 pixels for export.
- `--device 0` specifies the GPU device ID (use `--device cpu` for CPU-based inference).
- **Note**: TensorRT is only compatible with **NVIDIA GPUs**.

### Export to ONNX

To export your YOLO model to ONNX format, use the following command:

```
python .\export.py --weights ./"your_model_path.pt" --include onnx --half --imgsz 320 320 --device 0
```
- Replace `"your_model_path"` with your YOLO `.pt` model.
- The `--half` flag enables half-precision inference (if supported).
- `--imgsz 320 320` sets the image size to 320x320 pixels.

### Export for AMD GPU

To export your YOLO model for an AMD GPU, use the following command:

```
python .\export.py --weights .\your_model_path.pt --include onnx --imgsz 320 320
```
- Replace `"your_model_path"` with the path to your YOLO `.pt` file.
- This command will export the model in the ONNX format for AMD GPU inference.

## Troubleshooting

- If you encounter issues during export, ensure that your `CUDA`, `cuDNN`, and `TensorRT` versions are compatible with the version of `PyTorch` you are using.
- For `ONNX` export issues, ensure you have the `correct ONNX version` installed.


# 🚀 NVIDIA CUDA Installation Guide

### 1. **Download the NVIDIA CUDA Toolkit 11.8**

First, download the CUDA Toolkit 11.8 from the official NVIDIA website:

👉 [Nvidia CUDA Toolkit 11.8 - DOWNLOAD HERE](https://developer.nvidia.com/cuda-11-8-0-download-archive)

### 2. **Install the CUDA Toolkit**

- After downloading, open the installer (`.exe`) and follow the instructions provided by the installer.
- Make sure to select the following components during installation:
  - CUDA Toolkit
  - CUDA Samples
  - CUDA Documentation (optional)

### 3. **Verify the Installation**

- After the installation completes, open the `cmd.exe` terminal and run the following command to ensure that CUDA has been installed correctly:
  ```
  nvcc --version
  ```
This will display the installed CUDA version.

### **4. Install Cupy**
Run the following command in your terminal to install Cupy:
  ```
  pip install cupy-cuda11x
  ```

## 5. CUDNN Installation 🧩
Download cuDNN (CUDA Deep Neural Network library) from the NVIDIA website:

👉 [Download CUDNN](https://developer.nvidia.com/downloads/compute/cudnn/secure/8.9.6/local_installers/11.x/cudnn-windows-x86_64-8.9.6.50_cuda11-archive.zip/). (Requires an NVIDIA account – it's free).

## 6. Unzip and Relocate 📁➡️
Open the `.zip` cuDNN file and move all the folders/files to the location where the CUDA Toolkit is installed on your machine, typically:

```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8
```


## 7. Get TensorRT 8.6 GA 🔽
Download [TensorRT 8.6 GA](https://developer.nvidia.com/downloads/compute/machine-learning/tensorrt/secure/8.6.1/zip/TensorRT-8.6.1.6.Windows10.x86_64.cuda-11.8.zip).

## 8. Unzip and Relocate 📁➡️
Open the `.zip` TensorRT file and move all the folders/files to the CUDA Toolkit folder, typically located at:

```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8
```


## 9. Python TensorRT Installation 🎡
Once all the files are copied, run the following command to install TensorRT for Python:

```
pip install "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\python\tensorrt-8.6.1-cp311-none-win_amd64.whl"
```

🚨 **Note:** If this step doesn’t work, double-check that the `.whl` file matches your Python version (e.g., `cp311` is for Python 3.11). Just locate the correct `.whl` file in the `python` folder and replace the path accordingly.

## 10. Set Your Environment Variables 🌎
Add the following paths to your environment variables:
- system varaibles 
- edit `PATH`
- add `NEW`
- click okay 

```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\lib
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\libnvvp
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin
```

# Setting Up CUDA 11.8 with cuDNN on Windows

Once you have CUDA 11.8 installed and cuDNN properly configured, you need to set up your environment via `cmd.exe` to ensure that the system uses the correct version of CUDA (especially if multiple CUDA versions are installed).

## Steps to Set Up CUDA 11.8 Using `cmd.exe`

### 1. Set the CUDA Path in `cmd.exe`

You need to add the CUDA 11.8 binaries to the environment variables in the current `cmd.exe` session.

Open `cmd.exe` and run the following commands:

```
set PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin;%PATH%
set PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\libnvvp;%PATH%
set PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\extras\CUPTI\lib64;%PATH%
```
These commands add the CUDA 11.8 binary, lib, and CUPTI paths to your system's current session. Adjust the paths as necessary depending on your installation directory.

2. Verify the CUDA Version
After setting the paths, you can verify that your system is using CUDA 11.8 by running:
```
nvcc --version
```
This should display the details of CUDA 11.8. If it shows a different version, check the paths and ensure the proper version is set.

3. **Set the Environment Variables for a Persistent Session**
If you want to ensure CUDA 11.8 is used every time you open `cmd.exe`, you can add these paths to your system environment variables permanently:

1. Open `Control Panel` -> `System` -> `Advanced System Settings`.
Click on `Environment Variables`.
Under `System variables`, select `Path` and click `Edit`.
Add the following entries at the top of the list:
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\libnvvp
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\extras\CUPTI\lib64
```
This ensures that CUDA 11.8 is prioritized when running CUDA applications, even on systems with multiple CUDA versions.

4. **Set CUDA Environment Variables for cuDNN**
If you're using cuDNN, ensure the `cudnn64_8.dll` is also in your system path:
```
set PATH=C:\tools\cuda\bin;%PATH%
```
This should properly set up CUDA 11.8 to be used for your projects via `cmd.exe`.

#### Additional Information
- Ensure that your GPU drivers are up to date.
- You can check CUDA compatibility with other software (e.g., PyTorch or TensorFlow) by referring to their documentation for specific versions supported by CUDA 11.8.
---
---
## 🚀 AMD GPU Setup Instructions (DirectML Support)

While NVIDIA GPUs utilize CUDA for deep learning, AMD GPUs can be leveraged on Windows using DirectML, a GPU-accelerated backend for machine learning.

### 1. Install PyTorch for AMD GPUs (DirectML)

For AMD GPUs on Windows, PyTorch supports DirectML as the backend. You can install PyTorch with DirectML using the following command:

```
pip install torch==2.5.1+cpu torchvision==0.20.1+cpu torchaudio==2.5.1+cpu --extra-index-url https://download.pytorch.org/whl/cpu
```

### 2. Install ONNX Runtime with DirectML
To use ONNX with AMD GPUs, install the `onnxruntime-directml` package:

```
pip install onnxruntime-directml
```

### 3. Verify AMD GPU Support
To ensure that your AMD GPU is properly set up, you can verify DirectML support by running the following script:

```
import onnxruntime as ort
print(ort.get_device())
```

If your setup is correct, this should return `"DML"`, indicating that ONNX Runtime is using DirectML.
