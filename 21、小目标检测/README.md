小目标检测

cv领域目标检测中两大拦路虎：大形变，小尺寸，今天总结一下小目标检测算法。

### **小目标如何定义**

- 国际组织SPIE定义

  小目标为在256*256的图像中目标面积小于80像素，即小于256\*256的0.12%就为小目标

- MS COCO定义

  在MS COCO数据集中对于小目标的定义是小于32\*32像素的目标。如下图所示

  ![截屏2020-03-20下午1.33.30](https://i.loli.net/2020/03/20/heEQMm5SUlJcYjG.png)

在CV领域中，新的SOTA算法一般都是在COCO上进行测评，所以COCO的定义还是很具有参考意义的。对于面积小于32\*32的物体，MS COCO就认为它是小目标，在测评时候，会对这个范围内的物体计算APsmall，不管是任何时候的SOTA检测算法，其测评数据中APsmall永远是最小的那个。一般的通用检测算法在APsmall上很少能达到0.3。

对于MSCOCO对小目标的定义，我觉得有点苛刻，在实际安防领域中行人检测算法中，一般小于70*70的目标，就认为是小目标了。



### **小目标检测进展**

- 改进Loss，例如iou loss
- 在浅层网络上出特征图，因为low level负责小目标，deep level负责大目标
- 更好的特征融合方法，类似于DSSD那样
- data-augmentation
- 先做超分算法，再做检测

例如有一个项目是在1080P的安防视角中检测乒乓球，如果是普通SSD或者YOLO算法对于此类应用来说，其效果应该不好。记得当时采取了两个措施，对于召回率的提升有一定帮助

- 网络输入尺寸变大，例如将300\*300增到500*500
- 做图像金字塔，类似于MTCNN，输入不同尺寸原图
- 使用膨胀卷积(dilated convolution)代替池化



**小目标检测应用**

- 小目标(Tiny Object)
- 小人脸(Tiny Face)
- 小行人(Tiny Pedestrian)

行人检测小目标数据集，我收集了一部分paper的链接，后台回复获取下载链接

### **Papers**

#### Tiny Object Detection

* **Scale Match for Tiny Person Detection** [[Paper]](https://arxiv.org/abs/1912.10664) [[Benchmark]](https://github.com/ucas-vg/TinyBenchmark)
  * Xuehui Yu, Yuqi Gong, Nan Jiang, Qixiang Ye, Zhenjun Han ***WACV 2020***
* **MatrixNets: A New Scale and Aspect Ratio Aware Architecture for Object Detection** [[Paper]](https://arxiv.org/abs/2001.03194) [[Code]](https://github.com/arashwan/matrixnet)
  * Abdullah Rashwan, Rishav Agarwal, Agastya Kalra, Pascal Poupart ***arXiv 2020***
* **M2Det: A Single-Shot Object Detector based on Multi-Level Feature Pyramid Network** [[Paper]](https://arxiv.org/abs/1811.04533) [[Code]](https://github.com/qijiezhao/M2Det)
  * Qijie Zhao, Tao Sheng, Yongtao Wang, Zhi Tang, Ying Chen, Ling Cai, Haibin Ling ***AAAI 2019***
* **Enriched Feature Guided Refinement Network for Object Detection** [[Paper]](http://openaccess.thecvf.com/content_ICCV_2019/papers/Nie_Enriched_Feature_Guided_Refinement_Network_for_Object_Detection_ICCV_2019_paper.pdf) [[Code]](https://github.com/Ranchentx/EFGRNet)
  * Jing Nie, Rao Muhammad Anwer, Hisham Cholakkal, Fahad Shahbaz Khan, Yanwei Pang, Ling Shao ***ICCV 2019***
* **RepPoints: Point Set Representation for Object Detection** [[Paper]](https://arxiv.org/abs/1904.11490) [[Code]](https://github.com/microsoft/RepPoints)
  * Ze Yang, Shaohui Liu, Han Hu, Liwei Wang, Stephen Lin ***ICCV 2019***
* **Scale-Aware Trident Networks for Object Detection** [[Paper]](https://arxiv.org/abs/1901.01892) [[Code]](https://github.com/TuSimple/simpledet/tree/master/models/tridentnet)
  * Yanghao Li, Yuntao Chen, Naiyan Wang, Zhaoxiang Zhang ***ICCV 2019***
* **SCRDet: Towards More Robust Detection for Small, Cluttered and Rotated Objects** [[Paper]](http://openaccess.thecvf.com/content_ICCV_2019/papers/Yang_SCRDet_Towards_More_Robust_Detection_for_Small_Cluttered_and_Rotated_ICCV_2019_paper.pdf)
  * Xue Yang, Jirui Yang, Junchi Yan, Yue Zhang, Tengfei Zhang, Zhi Guo, Xian Sun, Kun Fu ***ICCV 2019***
* **Clustered Object Detection in Aerial Images** [[Paper]](http://openaccess.thecvf.com/content_ICCV_2019/papers/Yang_Clustered_Object_Detection_in_Aerial_Images_ICCV_2019_paper.pdf)
  * Fan Yang, Heng Fan, Peng Chu, Erik Blasch, Haibin Ling ***ICCV 2019***
* **Learning Object-Wise Semantic Representation for Detection in Remote Sensing Imagery** [[Paper]](http://openaccess.thecvf.com/content_CVPRW_2019/papers/DOAI/Li_Learning_Object-Wise_Semantic_Representation_for_Detection_in_Remote_Sensing_Imagery_CVPRW_2019_paper.pdf)
  * Chengzheng Li, Chunyan Xu, Zhen Cui, Dan Wang, Zequn Jie, Tong Zhang, Jian Yang ***CVPR Workshop 2019***
* **AugFPN: Improving Multi-scale Feature Learning for Object Detection** [[Paper]](https://arxiv.org/abs/1912.05384)
  * Chaoxu Guo, Bin Fan, Qian Zhang, Shiming Xiang, Chunhong Pan ***CoRR 2019***
* **R2-CNN: Fast Tiny Object Detection in Large-scale Remote Sensing Images** [[Paper]](https://arxiv.org/abs/1902.06042v2)
  * Jiangmiao Pang, Cong Li, Jianping Shi, Zhihai Xu, Huajun Feng ***TGRS 2019***
* **R3Det: Refined Single-Stage Detector with Feature Refinement for Rotating Object** [[Paper]](https://arxiv.org/abs/1908.05612) [[Code]](https://github.com/Thinklab-SJTU/R3Det_Tensorflow)
  * Yang, Xue and Liu, Qingqing and Yan, Junchi and Li, Ang and Zhiqiang, Zhang and Gang, Yu ***arXiv 2019***
* **SpineNet: Learning Scale-Permuted Backbone for Recognition and Localization** [[Paper]](https://arxiv.org/abs/1912.05027)
  * Xianzhi Du, Tsung-Yi Lin, Pengchong Jin, Golnaz Ghiasi, Mingxing Tan, Yin Cui, Quoc V. Le, Xiaodan Song ***arXiv 2019***
* **EfficientDet: Scalable and Efficient Object Detection** [[Paper]](https://arxiv.org/abs/1911.09070) [[Code]](https://github.com/toandaominh1997/EfficientDet.Pytorch)
  * Mingxing Tan, Ruoming Pang, Quoc V. Le ***arXiv 2019***
* **Learning Spatial Fusion for Single-Shot Object Detection** [[Paper]](https://arxiv.org/abs/1911.09516) [[Code]](https://github.com/ruinmessi/ASFF)
  * Songtao Liu, Di Huang, Yunhong Wang ***arXiv 2019***
* **Augmentation for small object detection** [[Paper]](https://arxiv.org/abs/1902.07296) [[Code]](https://github.com/gmayday1997/SmallObjectAugmentation)
  * Mate Kisantal, Zbigniew Wojna, Jakub Murawski, Jacek Naruniec, Kyunghyun Cho ***arXiv 2019***
* **Small Object Detection using Context and Attention** [[Paper]](https://arxiv.org/abs/1912.06319)
  * Jeong-Seon Lim, Marcella Astrid, Hyun-Jin Yoon, Seung-Ik Lee ***arXiv 2019***
* **Single-Shot Refinement Neural Network for Object Detection** [[Paper]](https://arxiv.org/abs/1711.06897) [[Code]](https://github.com/sfzhang15/RefineDet)
  * Shifeng Zhang, Longyin Wen, Xiao Bian, Zhen Lei, Stan Z. Li ***CVPR 2018***
* **An Analysis of Scale Invariance in Object Detection - SNIP** [[Paper]](https://arxiv.org/abs/1711.08189)
  * Bharat Singh, Larry S. Davis ***CVPR 2018***
* **Cascade R-CNN Delving into High Quality Object Detection** [[Paper]](https://arxiv.org/abs/1712.00726) [[Code]](https://github.com/zhaoweicai/cascade-rcnn)
  * Zhaowei Cai, Nuno Vasconcelos ***CVPR 2018***
* **Single-Shot Object Detection with Enriched Semantics** [[Paper]](https://arxiv.org/abs/1712.00433)
  * Zhishuai Zhang, Siyuan Qiao, Cihang Xie, Wei Shen, Bo Wang, Alan L. Yuille ***CVPR 2018***
* **Scale-Transferrable Object Detection** [[Paper]](http://openaccess.thecvf.com/content_cvpr_2018/CameraReady/1376.pdf) [[Code]](https://github.com/arvention/STDN-PyTorch)
  * Peng Zhou, Bingbing Ni, Cong Geng, Jianguo Hu, Yi Xu ***CVPR 2018***
* **DetNet: A Backbone network for Object Detection** [[Paper]](https://arxiv.org/abs/1804.06215) [[Code]](https://github.com/guoruoqian/DetNet_pytorch)
  * Zeming Li, Chao Peng, Gang Yu, Xiangyu Zhang, Yangdong Deng, Jian Sun ***ECCV 2018***
* **SOD-MTGAN: Small Object Detection via Multi-Task Generative Adversarial Network** [[Paper]](http://openaccess.thecvf.com/content_ECCV_2018/papers/Yongqiang_Zhang_SOD-MTGAN_Small_Object_ECCV_2018_paper.pdf)
  * Yancheng Bai, Yongqiang Zhang, Mingli Ding, Bernard Ghanem ***ECCV 2018***
* **SNIPER: Efficient Multi-Scale Training** [[Paper]](https://arxiv.org/abs/1805.09300) [[Code]](https://github.com/MahyarNajibi/SNIPER) 
  * Bharat Singh, Mahyar Najibi, Larry S. Davis ***NIPS 2018***
* **YOLOv3: An Incremental Improvement** [[Paper]](https://arxiv.org/abs/1804.02767) [[Project]](https://pjreddie.com/darknet/yolo/) [[Code]](https://github.com/ayooshkathuria/pytorch-yolo-v3)
  * Joseph Redmon, Ali Farhadi ***arXiv 2018***
* **You Only Look Twice: Rapid Multi-Scale Object Detection In Satellite Imagery** [[Paper]](https://arxiv.org/abs/1805.09512) [[Code]](https://github.com/avanetten/yolt)
  * Adam Van Etten ***arXiv 2018***
* **MSDNN: Multi-Scale Deep Neural Network for Salient Object Detection** [[Paper]](https://arxiv.org/abs/1801.04187)
  * Fen Xiao, Wenzheng Deng, Liangchan Peng, Chunhong Cao, Kai Hu, Xieping Gao ***arXiv 2018***
* **MDSSD: Multi-scale Deconvolutional Single Shot Detector for Small Objects** [[Paper]](https://arxiv.org/abs/1805.07009)
  * Mingliang Xu, Lisha Cui, Pei Lv, Xiaoheng Jiang, Jianwei Niu, Bing Zhou, Meng Wang ***arXiv 2018***
* **Perceptual Generative Adversarial Networks for Small Object Detection** [[Paper]](https://arxiv.org/abs/1706.05274)
  * Jianan Li, Xiaodan Liang, Yunchao Wei, Tingfa Xu, Jiashi Feng, Shuicheng Yan ***CVPR 2017***
* **Feature Pyramid Networks for Object Detection** [[Paper]](https://arxiv.org/abs/1612.03144) 
  * Tsung-Yi Lin, Piotr Dollár, Ross Girshick, Kaiming He, Bharath Hariharan, Serge Belongie ***CVPR 2017***
* **DSSD : Deconvolutional Single Shot Detector** [[Paper]](https://arxiv.org/abs/1701.06659) [[Code]](https://github.com/chengyangfu/caffe/tree/dssd)
  * Cheng-Yang Fu, Wei Liu, Ananth Ranga, Ambrish Tyagi, Alexander C. Berg ***CVPR 2017***
* **Accurate Single Stage Detector Using Recurrent Rolling Convolution** [[Paper]](https://arxiv.org/abs/1704.05776) [[Code]](https://github.com/xiaohaoChen/rrc_detection)
  * Jimmy Ren, Xiaohao Chen, Jianbo Liu, Wenxiu Sun, Jiahao Pang, Qiong Yan, Yu-Wing Tai, Li Xu ***CVPR 2017***
* **Focal Loss for Dense Object Detection** [[Paper]](https://arxiv.org/abs/1708.02002)
  * Tsung-Yi Lin, Priya Goyal, Ross Girshick, Kaiming He, Piotr Dollár ***ICCV 2017***
* **Deformable Convolutional Networks** [[Paper]](https://arxiv.org/abs/1703.06211) [[Code]](https://github.com/msracver/Deformable-ConvNets)
  * Jifeng Dai, Haozhi Qi, Yuwen Xiong, Yi Li, Guodong Zhang, Han Hu, Yichen Wei ***ICCV 2017***
* **Feature-Fused SSD: Fast Detection for Small Objects** [[Paper]](https://arxiv.org/abs/1709.05054) [[Code]](https://github.com/wnzhyee/Feature-Fused-SSD)
  * Guimei Cao, Xuemei Xie, Wenzhe Yang, Quan Liao, Guangming Shi, Jinjian Wu ***ICGIP 2017***
* **FSSD: Feature Fusion Single Shot Multibox Detector** [[Paper]](https://arxiv.org/abs/1712.00960) [[Code]](https://github.com/lzx1413/CAFFE_SSD/tree/fssd)
  * Zuoxin Li, Fuqiang Zhou ***arXiv 2017***
* **Inside-Outside Net: Detecting Objects in Context with Skip Pooling and Recurrent Neural Networks** [[Paper]](https://arxiv.org/abs/1512.04143)
  * Sean Bell, C. Lawrence Zitnick, Kavita Bala, Ross Girshick ***CVPR 2016***

### Tiny Face Detection

* **Finding Tiny Faces in the Wild with Generative Adversarial Network** [[Paper]](https://ivul.kaust.edu.sa/Documents/Publications/2018/Finding%20Tiny%20Faces%20in%20the%20Wild%20with%20Generative%20Adversarial%20Network.pdf)
  * Yancheng Bai, Yongqiang Zhang, Mingli Ding, Bernard Ghanem ***CVPR 2018***
* **Seeing Small Faces from Robust Anchor’s Perspective** [[Paper]](https://arxiv.org/abs/1802.09058)
  * Chenchen Zhu, Ran Tao, Khoa Luu, Marios Savvides ***CVPR 2018***
* **Face-MagNet: Magnifying Feature Maps to Detect Small Faces** [[Paper]](https://arxiv.org/abs/1803.05258)
  * Pouya Samangouei, Mahyar Najibi, Larry Davis, Rama Chellappa ***WACV 2018***
* **Finding Tiny Faces** [[Paper]](https://arxiv.org/abs/1612.04402)
  * Peiyun Hu, Deva Ramanan ***CVPR 2017***
* **S3FD: Single Shot Scale-invariant Face Detector** [[Paper]](http://openaccess.thecvf.com/content_ICCV_2017/papers/Zhang_S3FD_Single_Shot_ICCV_2017_paper.pdf)
  * Shifeng Zhang Xiangyu Zhu Zhen Lei∗ Hailin Shi Xiaobo Wang Stan Z. Li ***ICCV 2017***
* **Detecting and counting tiny faces** [[Paper]](https://arxiv.org/abs/1801.06504)
  * Alexandre Attia, Sharone Dayan ***arXiv 2018***

### Tiny Pedestrian Detection

* **High-level Semantic Feature Detection: A New Perspective for Pedestrian Detection** [[Paper]](http://openaccess.thecvf.com/content_CVPR_2019/papers/Liu_High-Level_Semantic_Feature_Detection_A_New_Perspective_for_Pedestrian_Detection_CVPR_2019_paper.pdf) [[Code]](https://github.com/liuwei16/CSP)
  * Wei Liu, ShengCai Liao, Weiqiang Ren, Weidong Hu, Yinan Yu ***CVPR 2019***
* **Feature Selective Anchor-Free Module for Single-Shot Object Detection** [[Paper]](http://openaccess.thecvf.com/content_CVPR_2019/papers/Zhu_Feature_Selective_Anchor-Free_Module_for_Single-Shot_Object_Detection_CVPR_2019_paper.pdf) [[PyTorch]](https://github.com/hdjang/Feature-Selective-Anchor-Free-Module-for-Single-Shot-Object-Detection) [[TensorFlow]](https://github.com/xuannianz/FSAF)
  * Chenchen Zhu, Yihui He, Marios Savvides ***CVPR 2019***
* **Seek and You Will Find: A New Optimized Framework for Efficient Detection of Pedestrian** [[Paper]](https://arxiv.org/abs/1912.10241)
  * Sudip Das, Partha Sarathi Mukherjee, Ujjwal Bhattacharya ***arXiv 2019***
* **Small-scale Pedestrian Detection Based on Somatic Topology Localization and Temporal Feature Aggregation** [[Paper]](https://arxiv.org/abs/1807.01438)
  * Tao Song, Leiyu Sun, Di Xie, Haiming Sun, Shiliang Pu ***ECCV 2018***