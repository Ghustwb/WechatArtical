目标检测算法--anchor

给目标检测算法分类，可以从好几个维度去看。例如我们常见的One-Stage和Two-Stage，这是从网络Stage数量上来分的。今天总结的方法，是根据是否有anchor来区分，所以在这个维度上，目标检测算法可以分为anchor based和anchor free，其实归根结底，都被称为Proposal Generation。其实anchor-free并不是一个新概念，大名鼎鼎的yolo应该是目标检测领域最早的anchor-free模型了。

Proposal Generation在目标检测中也是一个非常重要的角色，因为目标检测是需要定位的，定位准不准，全看proposal。一个Proposal生成器可以生成一系列的Bounding Box，这些BBox都是潜在的目标。我们将生成Proposal的方法分为四类：传统计算机视觉方法，anchor-based监督学习方法，anchor-free方法。不管是One-Stage还是Two-Stage算法都会生成Proposal，两者主要的区别是Two-Stage的算法生成的Proposal只有前景或者背景简单的二分类信息，具体类别和精细位置回归值由另一个stage的网络完成；然而One-Stage算法认为图像中每一个区域都是一个潜在的proposal，然后有根据地去预测出潜在目标的坐标和类别。

####  1、传统计算机视觉方法

这类的方法是使用传统计算机视觉的方法去生成Proposal，例如“边”，”角“，”颜色“，”连通域“之类的。从目标检测算法的发展路线中就可以看到，早期的目标检测算法就是通过一些传统视觉方法找到Proposal，例如大名鼎鼎的SS方法(Selective Search)，在fast RCNN中被用来获取推选框的那个。这里涉及到一个概念叫做**超像素**(superpixels),超像素是一系列像素的集合，这些像素具有类似的颜色、纹理、、梯度等特征，并且距离相近，然后把这些像素归于一类。如下图所示

![](https://i.loli.net/2019/12/27/oYTRWv47kIjx2ld.gif)

通过合并超级像素之后，可以很粗略地找到一些潜在的目标，然后再通过一系列分割的算法，最终生成一些Proposals。后来由于此种方法太耗时，逐渐被CNN取代，以至于现在基本上看不到传统算法做proposal了。

#### 2、Anchor-based 方法

anchor-based方法在目标检测算法中占有半壁江山，这种说法绝不为过，此种方法是根据预先定义的anchor来生成Proposal。我是在Faster-RCNN中第一次接触到proposal，使用监督学习RPN网络去生成Proposal，这里引用下关于FasterRCNN的介绍

```
第一步是在一个滑动窗口上生成不同大小和长宽比例的anchor box，取定IoU的阈值来标定这些anchor box的正负。于是，传入RPN网络的样本数据被整理为anchor box（坐标）和每个anchor box是否有物体（二分类标签）。RPN网络将每个样本映射为一个概率值和四个坐标值，概率值反应这个anchor box有物体的概率，四个坐标值用于回归定义物体的位置。最后将二分类和坐标回归的损失统一起来，作为RPN网络的目标训练。由RPN得到Region Proposal在根据概率值筛选后经过类似的标记过程，被传入R-CNN子网络，进行多分类和坐标回归，同样用多任务损失将二者的损失联合。
```

后来SSD直接使用多尺度anchor去匹配目标，这一点跟RPN有一点类似，在预定义的acnhor上使用不同的aspect ratio，所以能够适应多尺度的目标检测。 SSD的思想和RPN不同之处在于，前者可以在每一个Anchor Proposal上输出具体的类别判断，后者只能输出是前景还是背景的概率值，具体的类别需要另一个stage的算法判断。

后面，不管是目标检测还是人脸检测，很多都是anchor-based的方法

#### 3、anchor-free方法

anchor-free的方法提出的还挺早的，早在2015年DenseBox做人脸检测，yoloV1做目标检测，MTCNN做人脸检测，这些都是anchor-free的方法。这些可以被看成是anchor-free的早期探索吧，因为yolov2和yolov3后来都不使用anchor-free了。

![](https://i.loli.net/2019/12/27/cnjC9JVG5sRkuEa.jpg)

- 基于关键点的方法

  基于关键点的方法又可以被分为corner-based和center-based。最早的基于关键点的方法是[CornerNet](https://arxiv.org/pdf/1808.01244.pdf)，是通过检测bbox的对角线来检测出目标，提出corner pooling，更好地定位bbox的角点。首先预测出两组heatmaps，一组为top-left角点，另一组为bottom-right角点，每一组heatmaps有C个通道，表示C个类别，尺寸为HxW。[ExtremeNet](https://arxiv.org/abs/1901.08043)通过预测上下左右四个极值点和一个中心点来检测目标，[CenterNet](https://arxiv.org/abs/1904.08189)是预测左上角点，右下角点和中心点三个值。从目前的目标检测效果来看CenterNet的性能还不错，正在持续跟进。

- 基于密集预测的方法

  密集预测就是直接在特征图上回归出object的坐标，不同于角点检测。关于这一块的内容，我也实践的比较少，经常听说的几类方法有[FCOS](https://arxiv.org/abs/1904.01355)和[FoveaBox](https://arxiv.org/abs/1904.03797)，感兴趣的同学自己去看下原文吧。

从目前的检测算法文章来看，感觉anchor-free的方法更加的流行，新的文章层出不穷。应该去多花点时间学学新的东西了。





