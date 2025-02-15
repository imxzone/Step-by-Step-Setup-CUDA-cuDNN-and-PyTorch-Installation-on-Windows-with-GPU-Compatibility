<h1 align="center">  Step by Step Setup CUDA, cuDNN and PyTorch Installation on Windows with GPU Compatibility </h1> 
This repository provides a step-by-step guide to completely remove, install, and upgrade CUDA, cuDNN, and PyTorch on Windows, including GPU compatibility checks, environment setup, and installation verification.

---

## Step 1: Uninstall Existing NVIDIA Drivers and CUDA Components

1. **Navigate to 'Add or Remove Programs':**
   - Open the Windows Settings and go to **Apps > Installed Apps**.
   - Search for **NVIDIA** and uninstall all related components, including:
     - NVIDIA Graphics Driver
     - CUDA Toolkit
     - cuDNN
     - NVIDIA PhysX, GeForce Experience, etc.
2. **Restart Your System:**
   - After uninstalling, restart your computer to ensure all components are removed.
3. **Manually Delete Remaining NVIDIA Files:**
   - Navigate to `C:\Program Files\NVIDIA Corporation` and `C:\Program Files\NVIDIA GPU Computing Toolkit`.
   - Delete any remaining NVIDIA folders.
4. **Remove NVIDIA Paths from Environment Variables:**
   - Open **Environment Variables** and remove any NVIDIA-related paths from the `Path` variable.

---

## Step 2: Check GPU Compatibility

1. **Identify Your GPU Model:**
   - Open the **Device Manager** and check your GPU model under **Display Adapters**.
2. **Find GPU Compute Capability:**
   - Visit the [NVIDIA CUDA GPUs page](https://developer.nvidia.com/cuda-gpus) to find the compute capability and architecture of your GPU.
3. **Verify CUDA and cuDNN Compatibility:**
   - Ensure the CUDA and cuDNN versions you plan to install are compatible with your GPU.

---

## Step 3: Install CUDA Toolkit

1. **Download the CUDA Toolkit:**
   - Go to the [NVIDIA CUDA Toolkit Archive](https://developer.nvidia.com/cuda-toolkit-archive) and download the version compatible with your GPU and operating system.
2. **Run the CUDA Installer:**
   - Follow the installation prompts:
     - Select **Custom Installation**.
     - Ensure the **Graphics Driver** and **CUDA Toolkit** components are selected.
     - Optionally, install **Visual Studio Integration** if you plan to use Visual Studio.
3. **Verify CUDA Installation:**
   - Open Command Prompt and run:
     ```bash
     nvcc --version
     ```
   - This should display the installed CUDA version.

---

## Step 4: Install cuDNN

1. **Download cuDNN:**
   - Visit the [NVIDIA cuDNN Download Page](https://developer.nvidia.com/cudnn) and download the version compatible with your CUDA installation.
2. **Extract and Install cuDNN:**
   - Extract the downloaded cuDNN files.
   - Copy the contents of the `bin`, `include`, and `lib` folders to the corresponding folders in your CUDA installation directory (e.g., `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vX.X`).
3. **Update Environment Variables:**
   - Add the cuDNN `bin` folder path to the `Path` variable in **Environment Variables**.

---

## Step 5: Install PyTorch with CUDA Support

1. **Install Python:**
   - Download and install Python from the [official Python website](https://www.python.org/).
   - Ensure Python is added to the `Path` during installation.
2. **Install PyTorch:**
   - Open Command Prompt and run the PyTorch installation command. For example:
     ```bash
     pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
     ```
   - Replace `cu118` with the CUDA version you installed.
3. **Verify PyTorch Installation:**
   - Open Python and run:
     ```python
     import torch
     print(torch.__version__)
     print(torch.cuda.is_available())
     ```
   - This should display the PyTorch version and confirm CUDA availability.

---

## Step 6: Verify Full Setup

1. **Test CUDA and cuDNN:**
   - Run a simple PyTorch script to ensure CUDA and cuDNN are functioning correctly.
2. **Check GPU Utilization:**
   - Use tools like `nvidia-smi` to monitor GPU usage and confirm everything is working as expected.

---

## Troubleshooting

- **Installation Errors:**
  - Ensure all previous NVIDIA components are completely removed.
  - Verify compatibility between CUDA, cuDNN, and your GPU.
- **Environment Variables:**
  - Double-check that all paths (CUDA, cuDNN, Python) are correctly set in the `Path` variable.
- **Visual Studio Integration:**
  - If using Visual Studio, ensure the necessary components (e.g., C++ build tools) are installed.

---

## References

- [NVIDIA CUDA Toolkit Documentation](https://docs.nvidia.com/cuda/)
- [PyTorch Installation Guide](https://pytorch.org/get-started/locally/)
- [NVIDIA cuDNN Documentation](https://docs.nvidia.com/deeplearning/cudnn/)
