# YOLO Export Script

This repository contains scripts and commands for exporting YOLO models to different formats, including TensorRT (`.engine`) and ONNX (`.onnx`).

## Requirements

Ensure you have installed the necessary dependencies to run the export script:

- Python 3.11.6 or higher
- PyTorch 2.4.1 or higher
- TorchVision 0.19.1
- CUDA 11.8
- ONNX

### For NVIDIA GPUs (CUDA Support)

You can install the necessary Python packages for NVIDIA GPUs with the following command:

```
pip3 install torch==2.4.1+cu118 torchvision==0.19.1+cu118 torchaudio==2.4.1+cu118 --index-url https://download.pytorch.org/whl/cu118
```

### Files in the Repository

- **commands-to-export.txt:** A file containing useful commands for exporting your YOLO model.
- **export.py:** The Python script responsible for handling the export process.

## Exporting Your YOLO Model

### Export to TensorRT Engine (For NVIDIA GPUs)
- To export your YOLO model to a TensorRT engine, use the following command:
```
python .\export.py --weights ./<your_model_path>.pt --include engine --half --imgsz 320 320 --device 0
```
- Replace `<your_model_path>` with the path to your YOLO `.pt` file.
- The `--half` flag enables half-precision inference.
- `--imgsz 320 320` sets the image size to 320x320 pixels for export.
- `--device 0` specifies the GPU device ID (use `--device cpu` for CPU-based inference).

### Export to ONNX
- To export your YOLO model to ONNX format, use the following command:
```
python .\export.py --weights ./<your_model_path>.pt --include onnx --half --imgsz 320 320
```
- As above, replace `<your_model_path>` with your YOLO `.pt` model.
- The `--half` flag enables half-precision inference (if supported).
- `--imgsz 320 320` sets the image size to 320x320 pixels.

## Troubleshooting

- If you encounter issues during export, ensure that your `CUDA`, `cuDNN`, and `TensorRT` versions are compatible with the version of `PyTorch` you are using.
- For `ONNX` export issues, ensure you have the `correct ONNX version` installed.

