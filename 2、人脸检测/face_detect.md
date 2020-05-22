### 人脸检测 Face Detection

**目标**：人脸检测的目的是找出一张图片中的所有人脸的位置信息

人脸检测是人脸其他应用的基础，只有获取到了是否有人脸和人脸的精确的位置信息，其它的应用才能继续开展，所以说人脸检测是一个基础且重要的一个技术。

**本篇文章包含内容**：

- 人脸检测工程应用中面临的问题
- 人脸检测算法的发展过程
- 工程中常用的人脸检测算法
- 人脸检测算法案例详细说明

---

#### 一、人脸检测工程应用中面临的问题

在实际工程应用中，常常会面临非常复杂的工况。一方面算法准确度会受到很多因素影响，例如目标遮挡、光线变化、小尺寸人脸等等。另一方面算法的推理时间也会受到很多因素的影响，例如硬件性能，目标数量，图片尺寸等等。下面是几种工程中常见的问题。

- *人脸遮挡*，或者人脸角度较大，都会直接导致目标不完整，对于检测算法召回率有很大影响
- *暗光*，光线不充足条件下，导致成像质量不高，会影响检测算法召回率
- *低分辨率*，低分辨率导致人脸尺寸过小
- *人脸数量过多*，图片中人脸数量多，对检测算法要求较高。例如多目标靠的太近，对于NMS算法会是一种考验，另外数量过多会影响某些算法(图像金字塔类型)的时间复杂度，例如MTCNN

![影响人脸检测的因素](https://i.loli.net/2019/12/06/it3HFMY7CPB9Nje.png)



#### 二、人脸检测算法的发展过程

自从数字图像诞生，人脸检测算法就开始有人研究，历史可谓悠久。

人脸检测算法按照方法可以被分为两大类，基于特征的算法、基于图像的算法。

![人脸检测技术分类](https://i.loli.net/2019/12/06/u1xE3G2QlJBOaNK.png)

**基于特征的算法**就是通过提取图像中的特征和人脸特征进行匹配，如果匹配上了就说明是人脸，反之则不是。提取的特征是人为设计的特征，例如Haar，FHOG，特征提取完之后，再利用分类器去进行判断。通俗的说就是采用模板匹配，就是用人脸的模板图像与待检测的图像中的各个位置进行匹配，匹配的内容就是提取的特征，然后再利用分类器进行判断是否有人脸。

在早期工业界，具有里程碑意义的人脸检测算法----*VJ算法*（Viola-Jones），它是使用Haar-like特征和级联的AdaBoost分类器来进行人脸检测，在提升了精度的同时也兼顾了时间性能，VJ算法是一个框架，之后一段时间大家都是基于这个框架在做文章，例如Haar–AdaBoost, LBP–AdaBoost, GF-SVM

![adaboost示例](https://i.loli.net/2019/12/06/3h7cPUqEL4CJGIA.png)

在基于特征的方法中，学术界的人一直在尝试寻找面部的不变特征来进行更加鲁棒的检测。基于特征的方法如果要做到百分之百准确，有这样一个前提，必须存在不变的特性或特征，这样提取出来的特征百分之百存在并且很稳定。例如轮廓，肤色，眉毛，眼睛，鼻子，嘴巴和发际线。基于提取的特征，建立统计模型来描述它们的关系并验证人脸的存在。但是这些图像特征可能由于光照，噪声和遮挡而受到影响。脸部的特征边界可能会变弱，且阴影可能会导致大量强边缘，这些都会使检测算法失效。

**基于图像的算法**，将图像分为很多小窗口，然后分别判断每个小窗是否有人脸。通常基于图像的方法依赖于统计分析和机器学习，通过统计分析或者学习的过程来找到人脸和非人脸之间的统计关系来进行人脸检测。最具代表性的就是CNN，CNN用来做人脸检测也是目前效果最好，速度最快的。后面着重介绍CNN相关人脸检测算法。



#### 三、工程中常用的人脸检测算法

自从2018年以来，不管是什么硬件平台，基本上都看不到传统算法做人脸检测了，几乎全部都是使用深度学习也就是CNN，来做人脸识别。早起2016年以前，由于很多硬件设备是不具备强大的并行计算能力的，也就是没有GPU，所以很多算法只能运行在CPU上，而传统CNN算法在CPU上运行时间简直是不能忍受，所以那段时间CPU平台运行的算法几乎都是AdaBoost之类的算法。

后来，随着深度学习的发展，有两个重要的原因导致CNN算法直接吞并传统算法。1，硬件计算能力爆发式增长；2，CNN模型压缩和量化部署技术快速发展。正是因为这两个原因，所以现在连树莓派这种纯arm的都可以直接部署CNN，并且效果还不错。

**常用算法**

这里常用的算法有

- [MTCNN](<https://github.com/kpzhang93/MTCNN_face_detection_alignment>)
- [FaceBoxes](<https://github.com/sfzhang15/FaceBoxes>)
- [RetinaFace](<https://github.com/deepinsight/insightface/tree/master/RetinaFace>)
- [LFFD](<https://github.com/YonghaoHe/A-Light-and-Fast-Face-Detector-for-Edge-Devices>)
- [CenterFace](<https://github.com/Star-Clouds/CenterFace>)

*FDDB上数据*

| Algorithm       | FDDB Disc ROC curves score |
| :-------------- | :------------------------: |
| MTCNN           |         94.0@1000          |
| FaceBoxes       |                            |
| RetinaFace-mnet |         96.0@1000          |
| LFFD            |         97.3@1000          |
| CenterFace      |         98.1@1000          |

*在WIDER FACE 的test数据集上数据*

| Algorithm       | Easy Set | Medium Set | Hard Set |
| --------------- | :------: | :--------: | :------: |
| MTCNN           |  0.851   |   0.820    |  0.607   |
| FaceBoxes       |  0.791   |   0.794    |  0.715   |
| RetinaFace-mnet |  0.896   |   0.871    |  0.681   |
| LFFD            |  0.910   |   0.881    |  0.780   |
| CenterFace      |  0.932   |   0.921    |  0.873   |

**1、MTCNN**

MTCNN是kaipeng Zhang在本科阶段研究出来的，它是一个3级联的CNN网络，分为PNet，RNet，ONet，层层递进。PNet的输入是原图经过图像金字塔之后不同尺寸的图片，最后结果由ONet输出。![MTCNN](https://i.loli.net/2019/12/06/pwGqnDxs2NSCy4u.png)



**优点**：网络轻量推理时间快，工程部署灵活性大，能够输出5点landmark

**缺点**：检测时间受人脸数量影响，模型训练复杂

**2、FaceBoxes、RetinaFace mnet、LFFD**

以上都属于轻量级人脸检测算法，也属于One Stage 算法，FaceBoxes类似于SSD算法框架，采用多尺度特征层融合方式，采用anchor proposal，在不同尺度特征层上进行检测，这样就顾及到多尺度的人脸检测，FaceBoxes的文章旨在CPU上实现实时检测。

**3、CenterFace**

最新开源的一个人脸检测算法，github上同名项目。目前从数据来看，效果最好。

在实际工程应用中，要根据部署环境来选择人脸检测算法。例如在多人脸抓拍的场景，就不能选择MTCNN这类级联的算法，因为级联网络的推理速度与人脸数成反比，受人脸数量影响较大，MTCNN适用于人脸考勤或者人证对比的场景，只可能出现固定数量人脸的场景。

**4、另外**

还有一种，开袋即食。那就是dlib，这是一个人脸算法库，并且开源。不管你是用c++还是python，都可以直接使用dlib来做检测。如果想用python做实验，直接 import dlib，直接搞定。

这种自己学习一下可以，但是工程部署中一般不用。



#### 四、人脸检测算法案例详细说明

人脸检测算法的选取跟应用场景息息相关，本人使用过以下几种算法

- MTCNN
- 改进过的MTCNN
- resnet10-SSD 人脸检测
- pelee 人脸检测

因为本人工作倾向于嵌入式部署，所以选择模型都会考虑硬件推理时间消耗，而每一个新的人脸检测算法发表出来，很大一部分的都是为了刷榜来表现自己的实力，一般不考虑推理实时性。所以算法实际工程落地，一般都会去修改一些东西达到自己的应用目的。

MTCNN由于是级联结构，所以其可玩性非常大，例如将RNet金字塔层数降低或者ONet通道数减半，加速推理时间；例如单独使用ONet做人脸跟踪；例如MTCNN魔改之后输出最大人脸消耗非常短时间，等等

详细案例、网络搭建细节、检测器训练过程将会在下一篇文章中写出。



**最后，求一个关注**

![关注一下](https://i.loli.net/2019/12/06/NbysvFelAgLdqxi.jpg)

参考：

Filali H, Riffi J, Mahraz AM, Tairi H (2018) Multiple face detection based on machine learning. In: Proceeding of international conference on intelligent systems and computer vision, pp 1–8

Kaipeng Zhan, Zhanpeng Zhang, Zhifeng L, Yu Qiao. Joint Face Detection and Alignment Using Multitask Cascaded Convolutional Networks. 2016, IEEE Signal Processing Letters