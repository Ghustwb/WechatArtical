## Xavier安装pytorch

Xaiver上安装pytorch有两种方式

- 直接下载nvidia提供的whl文件
- 源码编译

nvidia官方下载[链接](https://forums.developer.nvidia.com/t/pytorch-for-jetson-nano-version-1-5-0-now-available/72048)提供了很多版本的编译好的pytorch二进制文件，只需要下载使用pip安装即可

所以这里选择下载pytorch的预编译文件安装，然后安装torchvision采用编译源码安装



**安装pytorch**

PiNet的python代码是基于python2版本的，所以注意这里安装都要选择python2版本

```shell
#查看pip版本
pip --version
#如果默认pip是python3，则将下面pip改为pip2即可
```

```shell
#安装依赖
sudo apt-get install libopenblas-base libopenmpi-dev 
#从whl文件安装
pip install future torch-1.4.0-cp27-cp27mu-linux_aarch64.whl
```



**安装torchvision**

```shell
sudo apt-get install libjpeg-dev zlib1g-dev
git clone --branch <version> https://github.com/pytorch/vision torchvision  
cd torchvision
sudo python setup.py install
pip install 'pillow<7'
```

pytorch的版本要和torchvision版本对应上

![1](https://i.loli.net/2020/05/24/pEg4oWeQT1BMic8.png)



**安装TensorRT依赖**

xavier在刷机的时候已经将tensorRT环境安装好了，所以只需要安装TensorRT的依赖即可

```shell
#安装boost
sudo apt-get install libboost-all-dev
#安装glog
sudo apt-get install libgoogle-glog-dev
#安装pycuda
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pycuda
```



**如果运行过程中报错**

```shell
Exception has occurred AttributeError
‘module’ object has no attribute ‘take_along_axis’
```

这是numpy版本过低导致的，使用pip升级numpy版本就可以了

```shell
pip install -U numpy
```

