---
layout: post
title:  "Settings for machine learning environment with GPU"
date:   2024-01-22 11:16:00 +0900
categories: setup AI
---

## Requirements

- **Ubuntu:** Version 13.04 or higher (Recommended version is 22.04; all examples below were tested on this version)
    - **PyTorch** requires minimum Ubuntu version of 13.04, due to glibc ≥ v2.17. For more detailed information, please refer to the [linux prerequisites](https://pytorch.org/get-started/locally/#linux-prerequisites) on the PyTorch official website.
- **Python**: Version 3.8-3.11 ([Detailed information](https://pytorch.org/get-started/locally/#linux-prerequisites))

## Anaconda

- **Conda tool**, provided by [**Anaconda**](http://anaconda.com), is designed to make package and environment management simpler and more uniform across various operating systems.

### Installation

1. Visit the official Anaconda [download page](https://www.anaconda.com/download).
2. Select the Anaconda version compatible with Ubuntu OS.Open the terminal (Short cut **`Ctrl+Alt+T`**). Change the directory where the Anaconda installer has beed downloaded. If, for example, the installer is in the `Download` directory, you would enter the following command:
    
    ```bash
    user@computer:~$ cd ~/Downloads # Make sure to replace the path 
                                    # if the installer is located 
                                    # in a different directory.
    ```
    ![Download link](/imgs/Settings%20for%20machine%20learning%20environment%20with%20GPU%205bd9d02562bb4ce5a1a3eff36004b0c6/Untitled.png)
    
3. Install Anaconda with the `bash <Anaconda installer file>`. As of January 19, 2024, the latest version of the Anaconda installer is `Anaconda3-2023.09.0-Linux-x86_64.sh`. In this case, `bash **Anaconda3-2023.09.0-Linux-x86_64.sh`.**
    
    ```bash
    user@computer:~/Downloads$ bash Anaconda3-2023.09.0-Linux-x86_64.sh
    ```
    
4. In the initial installation, simply press `Enter` to proceed with the default installation location.
    
    ```bash
    Anaconda3 will now be installed into this location:
    /root/anaconda3
    
      - Press ENTER to confirm the location
      - Press CTRL-C to abort the installation
      - Or specify a different location below
    
    [/root/anaconda3] >>> Enter
    ```
    
5. After installation completes, you’ll be asked whether to initialize Anaconda by running `conda init`. Type `yes` and press `Enter`.
    
    ```bash
    installation finished.
    Do you wish the installer to initialize Anaconda3
    by running conda init? [yes|no]
    [no] >>>  yes
    ```
    
6. Installation is finished.

## Pytorch

- PyTorch is an open-source deep learning library that is widely used for applications like computer vision and natural language processing.

### Installation

1. After installing Anaconda, you'll typically see the `(base)` prefix in your terminal, indicating that the base Anaconda environment is active. If this prefix does not appear, you can activate Conda by typing `conda init`.

    ```bash
    (base) user@computer:~$ 
    ```
    
2. To create a new environment specifically for PyTorch with Python 3.11, use the `conda create` command followed by the `-n` flag to name your environment, here named `pytorch`.
    
    ```bash
    (base) user@computer:~$ conda create -n pytorch python=3.11
    ```
    
3. Activate **PyTorch** environment by using the `conda activate` command followed by the name of the environment:
    
    ```bash
    (base) user@computer:~$ conda activate pytorch
    (pytorch) user@computer:~$    # pytorch environment is activated.
    ```
    
4. Install **PyTorch** and its corresponding packages:
    - The following command is provided by PyTorch [official site](https://pytorch.org/get-started/locally/). You may find the latest version of PyTorch and suitable version of **cuda** can be found in the link.
    
    ```bash
    (pytorch) user@computer:~$ conda install pytorch torchvision torchaudio \
                               pytorch-cuda=12.1 -c pytorch -c nvidia
    ```
    
5. After installation is done, verify whether **cuda** is available by **PyTorch**. First run python by using the `python` command.
    
    ```bash
    (pytorch) user@computer:~$ python
    ```
    
6. Run the following commands. If **PyTorch** successfully load GPU resources, `True` output is shown.
    
    ```python
    Python 3.11.7 (main, Dec 15 2023, 18:12:31) [GCC 11.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import torch
    >>> torch.cuda.is_available()
    True
    ```
    
7. Installation is finished.