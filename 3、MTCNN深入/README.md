### MTCNN应用详解

很多人应该是读过[MTCNN](<https://arxiv.org/pdf/1606.03473.pdf>)这篇文章的，所以这里没有简单的流程介绍，如果只是简单地算法介绍，百度上已经有很多了。

*开始之前，先确认以下几个问题*

- 为什么要做图像金字塔，图像金字塔在MTCNN中带来的优势和劣势分别是什么？
- MTCNN为什么可以接受任意尺寸的图片输入？
- 检测最小人脸尺寸ninSize为什么是12？缩放因子factor为什么是0.709？
- 什么是边框回归？
- 为什么ONet可以同时输出人脸位置和5个关键点位置？

---

**现在从头开始将MTCNN梳理一遍**

**1、读取一张图片，按照设置的检测最小人脸参数minSize，来进行图像金字塔操作**

```c++
    float scale = 12.f / minSize;
    float minWH = std::min(imgHeight, imgWidth) *scale;
    std::vector<float> scales;
    while (minWH >= 12) {
        scales.push_back(scale);
        minWH *= factor;
        scale *= factor;
    }
```

scale的个数就是图像金字塔的层数，从这里看出minSize越大，图像金字塔的层数越少

然后将金字塔中不同层的图像分别输入PNet网络

```c++
for (int i = 0; i < scales.size(); i++)
{
    int ws = (int)std::ceil(imgWidth*scales[i]);
    int hs = (int)std::ceil(imgHeight*scales[i]);
    cv::resize(img, resized, cv::Size(ws, hs));
		warpPNetInput(img);
    PNet->Forward();
}
```

从上面可以看出，图像金字塔有多少层就进行了多少次的PNet的forward运算。

*很明显，上面的问题已经有了答案*

- 图像金字塔的优势就是可以输入多尺寸的图像到CNN，提升CNN对多尺度目标的检出能力；劣势也很明显，直接增加了运算次数，也就成比例地增加了推理时间。在通用目标检测领域，影响召回率的两大难题：1，目标尺寸过小；2，目标尺度变化过大。工业界应用中提升召回率常用两种方法
  - 图像金字塔，在输入端进行多尺度变化，以适应多尺度检测，但是其缺点明显就是耗时
  - 特征金字塔，在特征图上进行多尺度，浅层特征负责检出大目标，深层特征负责检出小目标，例如SSD，FPN

- MTCNN可以接受任意尺寸的图像输入。因为PNet是一个[全卷积网络](https://arxiv.org/abs/1411.4038.pdf)，没有全连接层，常见的卷积，池化，非线性激活层都是可以接受任意尺度的输入运算的，全连接是需要事先定义好连接数量所以不能接受任意尺度运算，当然也有例外，例如Kaiming He的[SPP](https://arxiv.org/abs/1406.4729)。MTCNN文章截图如下图1所示，但是实际开源的代码中跟这个结构略有不同，PNet没有进行landmark的回归，只有两个分支，一个用来分类人脸得到confidence值，另外一个用来回归box位置

  ![PNet](https://i.loli.net/2019/12/07/7X29Ftzlqk6gAra.png)

  ![PNet-out](https://i.loli.net/2019/12/07/Hb1PUsx79BpQzr6.png)

- 图像金字塔生成的图像尺寸要和12尽量接近，因为训练PNet的数据是归一化到12大小的。在文章中说明了，图像金字塔低层的面积是上一层的0.5，也就是面积的scale是0.5，对应的边长的scale就是sqrt(0.5)，即0.709。minSize和factor两个参数直接影响到算法性能和推理时间

  ![](https://i.loli.net/2019/12/07/NFsnZQjGSdRa8h4.png)

**2、PNet输出的位置回归**

按照PNet的网络结构，可以得到这样一个结论，12x12的矩阵可以得到1个prob(就是上面softmax的输出也就是人脸的概率)和一个4值向量(上面conv4-2输出，人脸的回归值)。

由于PNet不限制输入尺寸，所以输入的尺寸肯定有很多比12大的。由于卷积池化都是在输入特征图上“滑动”，所以现在把PNet看成是一个判别器，判断每一个12x12区域是否有人脸输出1个confidence和4个regression值，这样PNet就被看成一个12x12的“滑动核”。

假设一个输入图片中，某一个12x12块，左上角为(x，y)。其对应输出特征图大小应该是(x/2-5,y/2-5),所以根据输出信息反推回去，就可以知道哪一个12x12的块出现了人脸。































