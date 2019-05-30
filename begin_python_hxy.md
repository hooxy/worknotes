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
