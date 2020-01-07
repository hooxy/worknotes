# 我的python环境搭建入门

## 1. 环境
- pythono可以在主流的桌面系统中运行，包括windows、Linux和Mac OS。我的工作环境主要是：简单项目在Mac OS上，复杂项目在Linux服务器上。

- python有自己的解释器，自带的IDE（集成开发环境）很不太好用。因此一般都会选择其它的环境。我的环境是：简单项目在交互式环境上，复杂项目在IDE上。
  - 交互式环境：jupyter notebook。
    - 使用pip安装。
  - IDE：PyCharm。
    - 需要专门的安装包来安装，需要找激活码。

## 2. 安装
- 安装方法可以百度关键字“python jupyter 安装”，"python pycharm 安装 入门"等等。这里随便放两个博客链接：
  - [python+jupyter](https://www.cnblogs.com/jiangfengtomhuo/p/7987419.html)
  - [python+pycharm](https://www.runoob.com/w3cnote/pycharm-windows-install.html)

- 官网：
[python](https://www.python.org/)，
[jupyter](https://jupyter.org/)，
[pycharm](http://www.jetbrains.com/pycharm/)

## 3. Tips
#### 3.1 jupyter
- jupyter通常是在terminal（Linux）或cmd（windows）等命令行工具中通过命令行启动，启动以后所处的目录就是命令行当前路径。此时创建的new notebook也会直接存在该目录下。

- 因此最好在启动之前就在命令行中切换到项目所在目录。我将所有jupyter项目都放在同一个/$MYPATH/jupyter_env/目录下，因此可以写一个小的批处理文件：
```
cd /$MYPATH/jupyter_env/
jupyter notebook
```
保存为jupyteri.bat，将文件放置于环境变量path中的某个目录下，比如```C:\Windows\System32```中
下次启动时，只需在cmd下输入```jupyteri```即可。


## 4. Tensorflow+Cuda+keras
- pip install --upgrade --ignore-installed tensorflow-gpu
- nvdia-smi
- nvcc查看cuda版本
  - sudo apt install nvidia-cuda-toolkit
  - nvcc --version

```
# Add NVIDIA package repositories
# Add HTTPS support for apt-key
sudo apt-get install gnupg-curl
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_10.0.130-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1604_10.0.130-1_amd64.deb
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
sudo apt-get update
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/nvidia-machine-learning-repo-ubuntu1604_1.0.0-1_amd64.deb
sudo apt install ./nvidia-machine-learning-repo-ubuntu1604_1.0.0-1_amd64.deb
sudo apt-get update

# Install NVIDIA driver
# Issue with driver install requires creating /usr/lib/nvidia
sudo mkdir /usr/lib/nvidia
sudo apt-get install --no-install-recommends nvidia-418
# Reboot. Check that GPUs are visible using the command: nvidia-smi

# Install development and runtime libraries (~4GB)
sudo apt-get install --no-install-recommends \
    cuda-10-0 \
    libcudnn7=7.6.2.24-1+cuda10.0  \
    libcudnn7-dev=7.6.2.24-1+cuda10.0


# Install TensorRT. Requires that libcudnn7 is installed above.
sudo apt-get install -y --no-install-recommends libnvinfer5=5.1.5-1+cuda10.0 \
    libnvinfer-dev=5.1.5-1+cuda10.0

```

https://blog.csdn.net/hhy_csdn/article/details/82860192
