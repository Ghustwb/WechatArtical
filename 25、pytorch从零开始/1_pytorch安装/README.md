## 一、pytorch安装

### 1、环境配置

- 显卡驱动
- cuda
- cudnn
- python环境

安装Ubuntu系统选择iso的时候，有amd64和i386两种iso可供下载，直接选择amd64格式，amd64格式其实是intel沿用至今的，只不过格式是amd发明的所以带amd标志。直接记住64位系统选择amd64,32位系统选择i386。虽然选择i386也没太大问题，但是后面坑非常多
直接使用linux命令行制作U盘启动盘

#### 1.1 卸载旧的驱动程序

```shell
sudo apt-get --purge remove nvidia*
sudo apt autoremove
sudo apt-get purge nvidia-cuda*
sudo apt-get purge nvidia-*
```

#### 1.2 关闭X Server

```shell
sudo service lightdm stop
```

#### 1.3安装显卡驱动

**注意:**

直接在software里面安装，简单快捷，版本是nvidia-384，版本会比较老。如果使用cuda的版本比较高，那么这个驱动是不能用的，例如cuda10.1要求最低驱动版本不能低于410。

cuda里面自带的驱动程序，可能会出现安装错误，安装成功之后，也可能出现进不去图形界面的情况，重复在登录界面。

我最终没有采用cuda里面的驱动程序，直接使用ppa安装的

```shell
#卸载原有驱动
sudo nvidia-uninstall
#ppa 安装
sudo add-apt-repository ppa:graphics-drivers/ppa 
sudo apt-get update 
sudo apt-get install nvidia-430
```

#### 1.4安装cuda和cudnn

将cudnn的库拷贝到对应的位置

```shell
sudo cp cudnn.h /usr/local/cuda/include
sudo cp lib* /usr/local/cuda/lib64/
#设置环境变量
sudo gedit /etc/profile
#在文件末尾加入一行
export PATH=/usr/local/cuda/bin:$PATH
#设置动态链接库路径
安装cuda的时候，安装程序默认生成了一个文件/etc/ld.so.conf.d/cuda**
```

#### 1.5配置python环境

安装anaconda，创建虚拟环境管理

- **修改anaconda的源**

替换为[清华镜像源](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/)

修改用户目录下的.condarc文件，复制一下内容到文件保存

```
channels:
  - defaults
show_channel_urls: true
channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

运行 `conda clean -i`清除索引缓存，确保使用的镜像提供的索引

- **创建虚拟环境**

```shell
conda create -n pytorch python=3.7
```

- 激活环境

```shell
conda activate pytorch
```
- [安装pytorch](https://pytorch.org/)

在官网上有选项可以选择自定义安装选项

```shell
# -i 参数是指定pip的安装源，临时
pip install torch torchvision -i https://pypi.mirrors.ustc.edu.cn/simple
```

- 测试是否安装成功
```python
#进入Python环境
from __future__ import print_function
import torch
x = torch.rand(5, 3)
print(x)
#如果有输出，则证明pytorch运行正常
print(torch.cuda.is_available())
#如果返回True，则证明cuda版本安装成功
```

