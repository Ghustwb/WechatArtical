2000FPS的人脸检测算法，开源了！

> 2019年，南方科技大学的余仕琪老师开源了一个当时有史以来最快的人脸检测算法，影响颇大。前天，这个项目更新了，添加了5点的landmark输出，并且开源了其训练方法。

先来看一组数据，在i7-1065G7 CPU上可以直接干到近2000fps

![3ef7efda8bc38a2b71b19895cb53b2fb](https://i.loli.net/2020/03/08/oDIrcX7LzN6PEAW.png)

于老师团队表示，由于疫情在家，疯狂尝试了很多想法，大部分都失败了，但是最后一个成功了，成功了就直接给发出来了，不仅重写了关键的代码，而且公开了pytorch的训练方法，而且项目的Licence采用了3-Clause BSD License，直接可以商用。

**此次的更新，有以下几个亮点**

- 采用8位整型计算，全部卷积操作无浮点运算，运算速度大幅提升
- 采用指令集加速，Intel平台可以使用AVX，ARM平台可以使用NEON
- 在ARM平台还可以使用Tengine加速，[Tengine详细手册]([https://github.com/OAID/Tengine/tree/master/examples/YuFaceDetectNe](https://github.com/OAID/Tengine/tree/master/examples/YuFaceDetectNet))
- 不依赖任何三方库，只要能编译C++，就能跑起来
- 公开了训练代码，自己想怎么改，就怎么改！！！

去年公布的检测算法，据说是基于caffe框架训练的，这次训练过程全部换成pytorch平台了，因为pytorch平台上修改自定义的模型比caffe上要方便很多。

去年3月份的时候，上一代的libfacedetection算法开源，影响甚广，我还记得当时对于MTCNN派和SSD派一些讨论。有一部分人热衷于在MTCNN上做修改然后工程化，有一部分人热衷于在SSD框架上做项目落地。

![截屏2020-03-08下午10.03.17](https://i.loli.net/2020/03/08/9URraP3Vf1bsKpd.png)

![截屏2020-03-08下午10.03.45](https://i.loli.net/2020/03/08/YDIPrLoK8f41gCR.png)

提出issue的一名北航的博士，在MTCNN上做了很多文章，并且自己做了一套利于部署的框架，叫做[ZQCNN](https://github.com/zuoqing1988/ZQCNN),目前star数量已经超过1.8K

libfacedetection新算法训练程序参考了中科院自动化所张士峰的[FaceBoxes.PyTorch](https://github.com/zisianw/FaceBoxes.PyTorch)以及Max deGroot的[ssd.pytorch](https://github.com/amdegroot/ssd.pytorch)，在训练过程中，前100个epoch只训练人脸检测，后面400个epoch人脸检测和landmark检测同时训练

此次新的更新，对于工业界将是一次重大利好，直接指导了从训练到部署的全套技术流程，从**训练模型合并bn层**，到**模型8位定点化**，并且**自动生成CPP部署**。

![截屏2020-03-08下午10.15.55](https://i.loli.net/2020/03/08/2XUC8dKfcDEuG6J.png)



