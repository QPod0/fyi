# 基于micromba安装Python和conda

`mamba`( https://github.com/mamba-org/mamba ) is a reimplementation of the conda package manager in C++.
It provides:

* parallel downloading of repository data and package files using multi-threading
* libsolv for much faster dependency solving, a state of the art library used in the RPM package manager of Red Hat, Fedora and OpenSUSE
* core parts of `mamba` are implemented in C++ for maximum efficiency 

## Step 0. 路径配置

在本地选取一个目录，作为安装microamba的路径并新建该文件夹，下面将该路径称为`prefix`，并以该路径作为示例：

* Windows示例：`D:/Programs/mamba`
* Linux示例：`/opt/mamba`

## Step 1. 添加操作系统环境变量

将上面的prefix路径添加到操作系统的PATH变量中。

* Windows示例： PATH中应当包含：`D:/Programs/mamba`
* Linux示例：`export PATH=$PATH:/opt/mamba/bin`

## Step 2. 下载microamba

从该链接下载micramba可执行文件，下载好之后，将其中的可执行文件（一般在`Library/bin/`下）解压到prefix目录中：

* Windows下载：https://micro.mamba.pm/api/micromamba/win-64/latest  ->  如：`D:/Programs/mamba/microamba.exe`
* Linux下载，refer to：https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html#linux-and-macos

## Step 3. 配置好condarc文件

配置好`~/.condarc`文件：

* 如果使用镜像源，确保镜像源可用，例如参考：https://developer.aliyun.com/mirror/anaconda/
* 如果在内网需要使用代理，确保配置中的`http_proxy`和`https_proxy`配置正确，尤其是密码部分

配置好后，可以通过命令`micromamba config list`来进行校验配置情况。

## Step 4. 执行安装

### On Windows

```bat
micromamba install -y --root-prefix=D:/Programs/mamba --prefix=D:/Programs/mamba -c "conda-forge" pip conda python=3.12
```

### On Linux

```bash
micromamba install -y --root-prefix=/opt/mamba --prefix=/opt/mamba -c "conda-forge" pip conda python=3.12
```

## Step 5. 校验安装

执行完上面的步骤之后，prefix目录中应该就安装好了conda和指定版本的Python。
