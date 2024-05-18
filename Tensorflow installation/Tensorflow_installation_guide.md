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
- Ubuntu 22.04 installed on your system.
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


