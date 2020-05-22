聊一聊最新的目标检测算法

上一篇文章写了现在目标检测还有哪些东西可以做，然后有读者就问了目前有哪些值得工程部署去应用的算法，所以今天来聊一聊值得去跟进的一些目标检测算法。

![](/home/lcg/Nutstore Files/Nutstore/11、最新目标检测算法跟进/IMG_0020.JPG)

上面这张图是2015年到2019年的SOAT的算法在coco上的box AP指标变化折线图，从这张图里面可以看出目前最好的成绩是53.3，其方法还是Cascade Mask RCNN，主干网络是Triple-ResNeXt152。目标检测最近值得关注的文章莫过于EfficientDet，虽然其EfficientDet-D7的成绩为51.0稍逊于SOAT的53.3，但是其方法很值得关注一波。

我根据最近的coco上的成绩，列了一个表格，如下

| 排名 | 方法               | Box AP | 文章链接                                               | github                                                       |
| ---- | ------------------ | ------ | ------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | Cascade Mask R-CNN | 53.3   | [CBNet](https://arxiv.org/pdf/1909.03625v1.pdf)        | [CBNet](https://github.com/PKUbahuangliuhe/CBNet)            |
| 2    | EfficientDet-D7    | 51.0   | [EfficientDet](https://arxiv.org/pdf/1911.09070v1.pdf) | [pytorch版](https://github.com/toandaominh1997/EfficientDet.Pytorch) [TF版](https://github.com/xuannianz/EfficientDet) |
| 3    | ATSS               | 50.7   | [ATSS](https://arxiv.org/pdf/1912.02424v1.pdf)         | [ATSS](https://github.com/sfzhang15/ATSS)                    |
| 4    | EfficientDet-D6    | 50.6   |                                                        |                                                              |
| 5    | EfficientDet-D5    | 49.8   |                                                        |                                                              |
| 6    | TridentNet         | 48.4   | [TridentNet](https://arxiv.org/pdf/1901.01892v2.pdf)   | [simpleDet](https://github.com/tusimple/simpledet)           |
| 7    | GCNet              | 48.4   | [GCNet](https://arxiv.org/pdf/1904.11492v1.pdf)        | [GCNet](https://github.com/xvjiarui/GCNet)                   |
| 21   | FCOS               | 44.7   | [FCOS](https://arxiv.org/pdf/1904.01355v5.pdf)         | [FCOS](https://github.com/tianzhi0549/FCOS)                  |
| 26   | M2Det              | 44.2   | [M2Det](https://arxiv.org/pdf/1811.04533v3.pdf)        | [M2Det](https://github.com/qijiezhao/M2Det)                  |
| 27   | YOLO3+ASFF         | 43.9   | [ASSF](https://arxiv.org/pdf/1911.09516v2.pdf)         | [ASSF](https://github.com/ruinmessi/ASFF)                    |

上面排名是根据coco上的box AP值从大到小排出来的，具体的排名可以参考github上的[pwc项目](https://github.com/zziz/pwc)

这里面列举出来的算法都是关注量非常高的算法，一方面其成绩非常不错，另一方面适合部署。如果一个算法的成绩非常好，但是运算非常耗时，这样也不在关注视野内。

**1、Efficient**

![efficientDet](/home/lcg/Nutstore Files/Nutstore/11、最新目标检测算法跟进/Screenshot from 2020-01-06 16-58-38.png)

EfficientDet提出了7种不同的网络结构，根据其复杂度不同，可以适应不同计算能力的平台，直接把YOLOV3按在地上摩擦



**2、ATSS**

张士峰大佬的新作，当然值得去研究。在anchor-free和anchor-based之间做文章，大佬亲自在知乎上做了[评价](https://www.zhihu.com/question/359595879/answer/927861326)

![](/home/lcg/Nutstore Files/Nutstore/11、最新目标检测算法跟进/Screenshot from 2020-01-06 17-06-53.png)

**3、YOLO3+ASFF**

还是使用darknet作为主干网络，在yolov3上加入了ASFF策略。

![assf](/home/lcg/Nutstore Files/Nutstore/11、最新目标检测算法跟进/Screenshot from 2020-01-06 17-13-33.png)

上面列举出来的三个算法非常值得去研究一波

q当然，如果你有时间，表格里面的算法都值得一看

在做上面那个表格的时候，我发现了一个问题，最新开源的出来的复现代码大部分都是Pytorch的，剩下一小部分是TF的，根本没有其他了。如果官方给出的不是pytorch版本，也会马上有大佬用pytorch复现出来。

然后我有点怀念当年的caffe了，于是我找到了这张图

![](/home/lcg/Nutstore Files/Nutstore/11、最新目标检测算法跟进/Screenshot from 2020-01-06 17-21-17.png)

![](/home/lcg/Nutstore Files/Nutstore/11、最新目标检测算法跟进/Screenshot from 2020-01-06 17-22-58.png)

这个图标是根据在某一个具体的月份，开源的目标检测算法使用的深度学习框架的数量画出来的折线图。可以看到，pytorch逐渐壮大，FT貌似一直都很强大，caffe就没在这个统计者严重出现过，属于其它。但是可以肯定，在15年，16年两年，caffe还是占据了其它类别的半壁江山的。

技术飞速发展的今天，唯一不变的也许就是变化了，拥抱变化才能拥抱未来！

