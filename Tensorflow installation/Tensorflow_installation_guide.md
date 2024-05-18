# TensorFlow Installation Guide on Ubuntu 22.04

This guide provides step-by-step instructions to install TensorFlow on Ubuntu 22.04, including setting up NVIDIA drivers, CUDA, cuDNN, Miniconda, and TensorFlow itself.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Installation Steps](#installation-steps)
    1. [Add NVIDIA Repository](#1-add-nvidia-repository)
    2. [Update System Cache](#2-update-system-cache)
    3. [Install NVIDIA Driver](#3-install-nvidia-driver)
    4. [Test Driver Installation](#4-test-driver-installation)
    5. [Download and Install CUDA Toolkit](#5-download-and-install-cuda-toolkit)
    6. [Configure CUDA Environment Variables](#6-configure-cuda-environment-variables)
    7. [Test CUDA Installation](#7-test-cuda-installation)
    8. [Install Miniconda](#8-install-miniconda)
    9. [Configure Conda Path](#9-configure-conda-path)
    10. [Test Conda Installation](#10-test-conda-installation)
    11. [Install TensorFlow in Conda Environment](#11-install-tensorflow-in-conda-environment)
    12. [Install Jupyter Lab and Notebook](#12-install-jupyter-lab-and-notebook)
    13. [Configure IPython Kernel for TensorFlow](#13-configure-ipython-kernel-for-tensorflow)
4. [Conclusion](#conclusion)

## Introduction

### What is CUDA?

CUDA (Compute Unified Device Architecture) is a parallel computing platform and application programming interface (API) model created by NVIDIA. It allows developers to use NVIDIA GPUs for general-purpose processing (an approach known as GPGPU, General-Purpose computing on Graphics Processing Units).

### What is Conda?

Conda is an open-source package management and environment management system that runs on Windows, macOS, and Linux. It quickly installs, runs, and updates packages and their dependencies. Conda is also used to create, export, and manage environments to run different packages in isolation.

### What is TensorFlow?

TensorFlow is an open-source library for machine learning developed by Google. It is used for a wide range of tasks but is particularly known for deep learning. TensorFlow provides a comprehensive, flexible ecosystem of tools, libraries, and community resources that lets researchers push the state-of-the-art in ML, and developers easily build and deploy ML-powered applications.

## Prerequisites

- An NVIDIA GPU compatible with CUDA.
- Ubuntu 22.04 installed.
- Basic knowledge of using the terminal.

## Installation Steps
### 1. Add NVIDIA Repository

Add the NVIDIA repository to get the latest drivers.

```bash
sudo add-apt-repository ppa:graphics-drivers/ppa -y
sudo apt install software-properties-common -y
```
### 2. Update the system cache 

Update your package lists to ensure you get the latest versions.

```bash
sudo apt update
```
### 3. Install NVIDIA Driver
Install the NVIDIA driver. Replace 550 with the version compatible with your GPU. 

```bash
sudo apt install nvidia-driver-550
```

### 4. Test driver installation 

Verify the installation with:
```bash
nvidia-smi
```

### 5. Download and Install CUDA Toolkit

Download the CUDA Toolkit installer.

```bash
wget https://developer.download.nvidia.com/compute/cuda/12.4.1/local_installers/cuda_12.4.1_550.54.15_linux.run
```

Run the installer (unselect the NVIDIA driver during installation).

```bash
sudo sh cuda_12.4.1_550.54.15_linux.run
```
### 6. Configure CUDA Environment Variables
Open the .bashrc file:

```bash
nano ~/.bashrc
```

Add the following lines at the end:

```bash
# CUDA PATH
export PATH=/usr/local/cuda-12.4/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-12.4/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

Reload the .bashrc file to apply the changes:

```bash
source ~/.bashrc
```

### 7.Test CUDA Installation
Verify CUDA installation with:
```bash 
nvcc -v
```

### 8.Install Miniconda 
Create a directory for Miniconda and download the installer.
```bash 
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
```
Initialize Conda:

```bash
~/miniconda3/bin/conda init bash
```
### 9.Configure Conda Path
Open the .bashrc file:

```bash
nano ~/.bashrc
```
Add the following line if it doesn't exist:

```bash
# Add Miniconda to PATH
export PATH="$HOME/miniconda3/bin:$PATH"
```

Reload the .bashrc file:
```bash
source ~/.bashrc
```
### 10.Test Conda Installation
Check the Conda version:
```bash
conda --version
```
### 11.Install TensorFlow in Conda Environment

#### 1.Prevent Conda from auto-activating the base environment:

```bash
conda config --set auto_activate_base false
```

#### 2.Create a Conda environment for TensorFlow:

```bash
conda create --name=tf python=3.10
```

#### 3.Activate the TensorFlow environment:
```bash
conda activate tf
```

#### 4.Install cuDNN:
```bash
conda install -c conda-forge cudnn
```

#### 5.Configure system paths for the Conda environment:
```bash
mkdir -p $CONDA_PREFIX/etc/conda/activate.d
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/' > $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
```
#### 6.Install TensorFlow with GPU support:
```bash
pip3 install tensorflow[and-cuda]
```

#### 7.Test TensorFlow installation:
```bash 
python3 -c "import tensorflow as tf; print(tf.random.normal([5, 5]))"
```
### 12.Install Jupyter Lab and Notebook
#### 1.Install Jupyter Lab:
```bash
pip3 install jupyterlab
```
#### 2.Install Jupyter Notebook:
```bash
pip3 install notebook
```
### 13.Configure IPython Kernel for TensorFlow
#### 1.Install and configure IPython kernel:
```bash
python -m ipykernel install --user --name=tf --display-name "Python (tf)"
```
#### 2.Open Jupyter Notebook:
```bash
jupyter notebook
```
#### 3.In Jupyter Notebook, choose the tf kernel and test if TensorFlow can detect the NVIDIA GPU:
```python
import tensorflow as tf
print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))
```
## 4.Conclusion
You have successfully installed TensorFlow with GPU support on your Ubuntu 22.04 system. Enjoy leveraging the power of TensorFlow for your deep learning projects!




