# 自动驾驶资源汇总: 

自动驾驶是一个非常复杂非常大的一个系统，技术层面的就有感知、决策、规划、控制，非技术层面的有伦理，法律等等。整个系统异常复杂，2015年之前说自动驾驶5年内落地，2016年的时候说自动驾驶10年内可以落地，现在说自动驾驶20年之内可能落不了地。对系统了解的越深，就越知道其难度之大。下面整理的是目前自动驾驶相关的一些教程和资料，不仅仅有教程，更有SOTA的能运行的代码。点击上面蓝字，关注公众号，后台回复 “ 03 ”，获取度盘下载链接。

*文章资源整理来自[github](<https://github.com/DeepTecher/awesome-autonomous-vehicle>)*

![](https://i.loli.net/2019/12/18/UY2XbZFmI35gtnd.png)

---



### 人工智能|Artificial Intelligence

* [GitHub: Awesome Machine Learning](https://github.com/josephmisiti/awesome-machine-learning) :star:38.8K - `机器学习`框架、库和软件的`精选列表`。 由Joseph Misiti.Joseph Misiti维护
* [GitHub: Deep Learning Papers Reading Roadmap](https://github.com/songrotek/Deep-Learning-Papers-Reading-Roadmap) :star:22.2K - `深度学习论文阅读路线图`从大纲到细节构建，从最新到最先进，从通用到特定领域，重点关注从深度学习开始的SOTA技术。 由Flood Sung维护。
* [Web: Open Source Deep Learning Curriculum](http://www.deeplearningweekly.com/pages/open_source_deep_learning_curriculum)  - `深度学习课程`旨在成为每个有兴趣认真学习该领域的人的起点。

### 机器人学|Robotics
* [GitHub: Awesome Robotics](https://github.com/Kiloreux/awesome-robotics) :star:1.19K - 由kiloreux维护的机器人技术的各种书籍，课程和其他资源的列表。

### 计算机视觉|Computer Vision
* [Awesome Computer Vision](https://github.com/jbhuang0604/awesome-computer-vision) :star: 9.7K (4年前更新)- 计算机视觉资源精选清单
* [Awesome Deep Vision](https://github.com/kjw0612/awesome-deep-vision) :star:7.9K(2年前更新) - 计算机视觉深度学习资源的精选清单

## 课程
* [[优达学城] Self-Driving Car Nanodegree Program](https://www.udacity.com/course/self-driving-car-engineer-nanodegree--nd013) - 教学自动驾驶团队使用的技能和技巧。 可以在[这里](https://medium.com/self-driving-cars/term-1-in-depth-on-udacitys-self-driving-car-curriculum-ffcf46af0c08#.bfgw9uxd9)找到课程大纲 .
* [[多伦多大学] CSC2541 Visual Perception for Autonomous Driving](http://www.cs.toronto.edu/~urtasun/courses/CSC2541/CSC2541_Winter16.html) - 自动驾驶视觉感知研究生课程。 本课程简要介绍了定位，自我运动估计，自由空间估计，视觉识别（分类，检测，分割）等主题。
* [[INRIA] Mobile Robots and Autonomous Vehicles](https://www.fun-mooc.fr/courses/inria/41005S02/session02/about?utm_source=mooc-list) - 介绍了对移动机器人和自动驾驶汽车进行编程所需的关键概念。 该课程提供了算法工具，并针对其上周的主题（行为建模和学习），它还将提供Python中的实际示例和编程练习。
* [[格拉斯哥大学] ENG5017 Autonomous Vehicle Guidance Systems](http://www.gla.ac.uk/coursecatalogue/course/?code=ENG5017)  - 介绍自动驾驶仪指导和协调背后的概念，使学生能够设计和实施规划、优化和反应的车辆的指导策略。
* [[David Silver - 优达学城] How to Land An Autonomous Vehicle Job: Coursework](https://medium.com/self-driving-cars/how-to-land-an-autonomous-vehicle-job-coursework-e7acc2bfe740#.j5b2kwbso) - 来自Udacity的David Silver回顾了他在软件工程背景下从事自动驾驶汽车工作的课程。
* [[斯坦福] - CS221 Artificial Intelligence: Principles and Techniques](http://stanford.edu/~cpiech/cs221/index.html)  - 包含一个简单的自动驾驶项目以及模拟器。
* [[MIT] 6.S094: Deep Learning for Self-Driving Cars](http://selfdrivingcars.mit.edu/)  - 通过构建自动驾驶汽车的应用主题介绍深度学习的实践。
* [[MIT] 2.166 Duckietown](http://duckietown.mit.edu/index.html)  - 关于研究生水平的自动化科学课程。 这是一个实践性的，以项目为中心的课程，侧重于自动驾驶车辆和高级自动化。 问题：**为Duckietown（小鸭城）设计自动机器人出租车系统。**



## 数据集
* [nuScenes](https://www.nuscenes.org/) - 安波福于2019年3月公开了其数据集，并在[GitHub](https://github.com/nutonomy/nuscenes-devkit)公开教程。数据集拥有从波士顿和新加坡收集的1000个“场景”的信息，包含每个城市环境中都有的最复杂的一些驾驶场景。该数据集由140万张图像、39万次激光雷达扫描和140万个3D人工注释边界框组成，是迄今为止公布的最大的多模态3D AV数据集。
* [H3D - HRI-US](https://usa.honda-ri.com/hdd/introduction/h3d) - 本田研究所于2019年3月发布其无人驾驶方向数据集，相关介绍于[arXiv:1903.01568](https://arxiv.org/abs/1903.01568)介绍。本数据集使用3D LiDAR扫描仪收集的大型全环绕3D多目标检测和跟踪数据集。 其包含160个拥挤且高度互动的交通场景，在27,721帧中共有100万个标记实例。凭借独特的数据集大小，丰富的注释和复杂的场景，H3D聚集在一起，以激发对全环绕3D多目标检测和跟踪的研究。
* [ApolloCar3D] - 该数据集包含5,277个驾驶图像和超过60K的汽车实例，其中每辆汽车都配备了具有绝对模型尺寸和语义标记关键点的行业级3D CAD模型。该数据集比PASCAL3D +和KITTI（现有技术水平）大20倍以上。
* [KITTI Vision Benchmark Suite](http://www.cvlibs.net/datasets/kitti/raw_data.php) - 数据集为使用各种传感器模式，例如高分辨率彩色和灰度立体相机，Velodyne 3D激光扫描仪和高精度GPS/IMU惯性导航系统，在10-100 Hz下进行6小时拍摄的交通场景。
* [Cityscape Dataset](https://www.cityscapes-dataset.com/)  - 专注于对城市街景的语义理解。 大型数据集，包含从50个不同城市的街景中记录的各种立体视频序列，高质量的像素级注释为5000帧，另外还有一组较大的20000个弱注释帧。 因此，数据集比先前的类似尝试大一个数量级。 可以使用带注释的类的详细信息和注释示例。
* [Mapillary Vistas Dataset](https://www.mapillary.com/dataset/vistas?pKey=xyW6a0ZmrJtjLw2iJ71Oqg&lat=20&lng=0&z=1.5)-数据集是一个新颖的大规模街道级图像数据集，包含25,000个高分辨率图像，注释为66个对象类别，另有37个类别的特定于实例的标签。通过使用多边形来描绘单个对象，以精细和细粒度的样式执行注释。
* [CamVid](http://mi.eng.cam.ac.uk/research/projects/VideoRec/CamVid/) -剑桥驾驶标签视频数据库（CamVid）是第一个具有对象类语义标签的视频集合，其中包含元数据。 数据库提供基础事实标签，将每个像素与32个语义类之一相关联。 该数据库解决了对实验数据的需求，以定量评估新兴算法。 虽然大多数视频都使用固定位置的闭路电视风格相机拍摄，但我们的数据是从驾驶汽车的角度拍摄的。 驾驶场景增加了观察对象类的数量和异质性。
* [Caltech数据集](http://www.vision.caltech.edu/Image_Datasets/CaltechPedestrians/) - 加州理工学院行人数据集包括大约10小时的640x480 30Hz视频，这些视频来自在城市环境中通过常规交通的车辆。 大约250,000个帧（137个近似分钟的长段）共有350,000个边界框和2300个独特的行人被注释。 注释包括边界框和详细遮挡标签之间的时间对应。 更多信息可以在我们的PAMI 2012和CVPR 2009基准测试文件中找到。
* [Comma.ai](https://archive.org/details/comma-dataset) - 7.25小时的高速公路驾驶。 包含10个可变大小的视频片段，以20 Hz的频率录制，相机安装在Acura ILX 2016的挡风玻璃上。与视频平行，还记录了一些测量值，如汽车的速度、加速度、转向角、GPS坐标，陀螺仪角度。 这些测量结果转换为均匀的100 Hz时基。
* [Oxford's Robotic Car](http://robotcar-dataset.robots.ox.ac.uk/) - 超过100次重复对英国牛津的路线进行一年多采集拍摄。 该数据集捕获了许多不同的天气，交通和行人组合，以及建筑和道路工程等长期变化。
* [伯克利BDD100K数据](https://bdd-data.berkeley.edu/) - 超过100K的视频和各种注释组成，包括图像级别标记，对象边界框，可行驶区域，车道标记和全帧实例分割，该数据集具有地理，环境和天气多样性
* [Udacity](https://github.com/udacity/self-driving-car/tree/master/datasets) - 为[Udacity Challenges](https://www.udacity.com/self-driving-car)发布的Udacity数据集。 包含ROSBAG训练数据。 （大约80 GB）。
* [University of Michigan North Campus Long-Term Vision and LIDAR Dataset](http://robots.engin.umich.edu/nclt/) -  包括全方位图像，3D激光雷达，平面激光雷达，GPS和本体感应传感器，用于使用Segway机器人收集的测距。
* [University of Michigan Ford Campus Vision and Lidar Data Set](http://robots.engin.umich.edu/SoftwareData/Ford)  - 基于改进的福特F-250皮卡车的自动地面车辆测试台收集的数据集。 该车配备了专业（Applanix POS LV）和消费者（Xsens MTI-G）惯性测量单元（IMU），Velodyne 3D激光雷达扫描仪，两个推扫式前视Riegl激光雷达和Point Grey Ladybug3全方位摄像头 系统。
* [DIPLECS Autonomous Driving Datasets (2015)](http://cvssp.org/data/diplecs/)  - 通过在Surrey乡村周围驾驶的汽车中放置高清摄像头来记录数据集。 该数据集包含大约30分钟的驾驶时间。 视频为1920x1080，采用H.264编解码器编码。 通过跟踪方向盘上的标记来估计转向。 汽车的速度是从汽车的速度表OCR估算的（但不保证方法的准确性）。
* [Velodyne SLAM Dataset from Karlsruhe Institute of Technology](http://www.mrt.kit.edu/z/publ/download/velodyneslam/dataset.html)  - 在德国卡尔斯鲁厄市使用Velodyne HDL64E-S2扫描仪记录的两个具有挑战性的数据集。
* [SYNTHetic collection of Imagery and Annotations (SYNTHIA)](http://synthia-dataset.net/)  - 包括从虚拟城市渲染的照片般逼真的帧集合，并为13个类别提供精确的像素级语义注释：misc，天空，建筑，道路，人行道，围栏，植被，杆，汽车，标志，行人， 骑自行车的人，车道标记。
* [CSSAD Dataset](http://aplicaciones.cimat.mx/Personal/jbhayet/ccsad-dataset)  - 包括若干真实世界的立体数据集，用于在自动驾驶车辆的感知和导航领域中开发和测试算法。 然而，它们都没有记录在发展中国家，因此它们缺乏在街道和道路上可以找到的特殊特征，如丰富的坑洼，减速器和特殊的行人流。 该立体数据集是从移动的车辆记录的，并且包含高分辨率立体图像，其补充有从IMU，GPS数据和来自汽车计算机的数据获得的定向和加速度数据。
* [Daimler Urban Segmetation Dataset](http://www.6d-vision.com/scene-labeling)  - 包括城市交通中记录的视频序列。 该数据集由5000个经过校正的立体图像对组成，分辨率为1024x440。 500帧（序列的每10帧）带有5个类的像素级语义类注释：地面，建筑，车辆，行人，天空。 提供密集视差图作为参考，但是这些不是手动注释的，而是使用半全局匹配（sgm）计算的。
* [Self Racing Cars - XSens/Fairchild Dataset](http://data.selfracingcars.com/)  - 文件包括来自Fairchild FIS1100 6自由度（DoF）IMU，Fairchild FMT-1030 AHRS，Xsens MTi-3 AHRS和Xsens MTi-G-710 GNSS / INS的测量结果。 事件中的文件都可以在MT Manager软件中读取，该软件可作为MT软件套件的一部分提供，可在此处获得。
* [MIT AGE Lab](http://lexfridman.com/automated-synchronization-of-driving-data-video-audio-telemetry-accelerometer/)  -  由AgeLab收集的1,000多小时多传感器驾驶数据集的一小部分样本。
* [LaRA](http://www.lara.prd.fr/lara) -巴黎的交通信号灯数据集
* [KUL Belgium Traffic Sign Dataset](http://www.vision.ee.ethz.ch/~timofter/traffic_signs/)  - 具有10000多个交通标志注释的大型数据集，数千个物理上不同的交通标志。 用8个高分辨率摄像头录制的4个视频序列安装在一辆面包车上，总计超过3个小时，带有交通标志注释，摄像机校准和姿势。 大约16000张背景图片。 这些材料通过GeoAutomation在比利时，佛兰德斯地区的城市环境中捕获。
* [博世小交通灯](https://hci.iwr.uni-heidelberg.de/node/6132) - 用于深度学习的小型交通灯的数据集。
* [LISA: Laboratory for Intelligent & Safe Automobiles, UC San Diego Datasets](http://cvrr.ucsd.edu/LISA/datasets.html)  - 交通标志，车辆检测，交通灯，轨迹模式。
* [Multisensory Omni-directional Long-term Place Recognition (MOLP) dataset for autonomous driving](http://hcr.mines.edu/code/MOLP.html) - 它是在美国科罗拉多州的一年内使用全向立体相机录制的。[论文](https://arxiv.org/abs/1704.05215)
* [DeepTesla](https://selfdrivingcars.mit.edu/deeptesla/) - 主要包括tesla在两种不同驾驶模式（human driving和autopilot）下的前置相机录制的视频和车辆的转向控制信号。数据可以从这里下载:[百度云](https://pan.baidu.com/s/1c2J2IFA#list/path=%2F)。可以参考此[GitHub](https://github.com/CJHMPower/deep-tesla)

## SOTA代码
### 物体检测|Object Detection  
* `Stereo R-CNN` [HKUST-Aerial-Robotics/Stereo-RCNN](https://github.com/HKUST-Aerial-Robotics/Stereo-RCNN)  - `CVPR2019`   
研究机构 : 港科大Aerial Robotics Group和大疆  
论文 : [Stereo R-CNN based 3D Object Detection for Autonomous Driving](https://arxiv.org/abs/1902.09738)
* `SimpleDet`[tusimple/simpledet](https://github.com/tusimple/simpledet) - `SOTA on consumer grade hardware at large scale`   
研究机构 : 图森  
论文 : [SimpleDet: A Simple and Versatile Distributed Framework for Object Detection and Instance Recognition](https://arxiv.org/abs/1903.05831)      
* `PointPillars` [traveller59/second.pytorch](https://github.com/traveller59/second.pytorch) -`SOTA for Birds Eye View Object Detection on KITTI Cyclists Moderate`   
研究机构 : nuTonomy（安波福下的公司）  
论文 : [PointPillars: Fast Encoders for Object Detection from Point Clouds](https://arxiv.org/abs/1812.05784),
* `PointRCNN`[sshaoshuai/PointRCNN](https://github.com/sshaoshuai/PointRCNN) -
`KITTI for 3D Object Detection (Cars)` : #2,Cars-Easy(AP:84.32%); #1,Cars-Moderate(AP:75.42%); #1,Cars-Hard(AP:67.86%)   
研究机构 : 香港中文大学  
论文 : [PointRCNN: 3D Object Proposal Generation and Detection from Point Cloud](https://arxiv.org/abs/1812.04244)
* [sshkhr/BigDataCup18_Submission](https://github.com/sshkhr/BigDataCup18_Submission) -
IEEE International Conference On Big Data Cup 2018(2018年IEEE国际大数据杯会议的道路损伤检测和分类挑战),   
研究机构 :  印度科学研究所   
论文 : [Road Damage Detection And Classification In Smartphone Captured Images Using Mask R-CNN](https://arxiv.org/abs/1811.04535)
* `Complex-YOLO`[AI-liu/Complex-YOLO](https://github.com/AI-liu/Complex-YOLO) -  
研究机构 : 法里奥、伊尔默瑙理工大学  
论文:[Complex-YOLO: Real-time 3D Object Detection on Point Clouds](https://arxiv.org/abs/1803.06199)
* [kujason/avod](https://github.com/kujason/avod) -`KITTI 3D Object Detection for cars`#2 Cars-Hard(AP:66.38%)   
研究机构 : 滑铁卢大学工程学院机械与机电工程系    
论文 : [Joint 3D Proposal Generation and Object Detection from View Aggregation](https://arxiv.org/abs/1712.02294)  
* `PointNet`[charlesq34/pointnet](https://github.com/charlesq34/pointnet)- 
`SOTA（Object Localization & 3D Object Detection）` :Cars、Cyclists、Pedestrian   
研究机构 : 斯坦福大学、Nuro公司、加州大学圣地亚哥分校     
论文 : [Frustum PointNets for 3D Object Detection from RGB-D Data](https://arxiv.org/abs/1711.08488)
* `SqueezeDet`[BichenWuUCB/squeezeDet](https://github.com/BichenWuUCB/squeezeDet) -`SOTA for KITTI(2016)`  
研究机构 : 伯克利、[DeepScale](http://deepscale.ai/)（专注于自动驾驶感知技术）         
论文 : [SqueezeDet: Unified, Small, Low Power Fully Convolutional Neural Networks for Real-Time Object Detection for Autonomous Driving](https://arxiv.org/abs/1612.01051) 
* `VoxelNet`[charlesq34/pointnet](https://github.com/charlesq34/pointnet) - 
`SOTA（Object Localization & 3D Object Detection）`:Cars、Cyclists、Pedestrian  
研究机构 : 苹果公司    
论文 : [VoxelNet: End-to-End Learning for Point Cloud Based 3D Object Detection](https://arxiv.org/abs/1711.06396)  
### 分割|Segmentation  
* `LEDNet`[xiaoyufenfei/LEDNet](https://github.com/xiaoyufenfei/LEDNet) - 暂未released，Semantic Segmentation: `Real-time(71FPS)`、Semantic Segmentation(Mean IoU 70.6%)，ICIP 2019  
研究机构 : 南京邮电大学、天普大学   
论文 : [LEDNet: A Lightweight Encoder-Decoder Network for Real-Time Semantic Segmentation](https://arxiv.org/abs/1905.02423)，
* `swiftnet`[orsic/swiftnet](https://github.com/orsic/swiftnet) - 
Real-Time Semantic Segmentation on Cityscapes #9,Semantic Segmentation(Mean IoU:75.5%);#2,`Real-time(Mean IoU:75.5%)`;#3,`Real-time(Frame:39.9 fps)`,`CVPR2019`   
研究机构 : 萨格勒布大学 电气工程与计算学院   
论文 : [In Defense of Pre-trained ImageNet Architectures for Real-time Semantic Segmentation of Road-driving Images](https://arxiv.org/abs/1903.08469) 
* [YangZhang4065/AdaptationSeg](https://github.com/YangZhang4065/AdaptationSeg) - SOTA for `Image-to-Image Translation` on SYNTHIA-to-Cityscapes  
研究机构 :  IEEE Member  
论文 : [A Curriculum Domain Adaptation Approach to the Semantic Segmentation of Urban Scenes](https://arxiv.org/abs/1812.09953)
* `BiSeNet`[ycszen/TorchSeg](https://github.com/ycszen/TorchSeg) -
Cityscapes：#2，Real-time（`Frame:65.5 Fps`）;#8 (`Mean IoU 78.9%`)、CamVid：#2，Mean IoU 68.7%;ECCV 2018  
研究机构 : 多谱信息处理技术国家级重点实验室、华中科技大学自动化学院、北大、旷视  
论文 : [BiSeNet: Bilateral Segmentation Network for Real-time Semantic Segmentation](https://arxiv.org/abs/1808.00897)
* [MSiam/TFSegmentation](https://github.com/MSiam/TFSegmentation) - 
Benchmarking Framework（Cityscapes dataset for urban scenes）      
研究机构 : 阿尔伯塔大学、开罗大学    
论文 : [RTSeg: Real-time Semantic Segmentation Comparative Study](https://arxiv.org/abs/1803.02758)
* `MultiNet`[MarvinTeichmann/MultiNet](https://github.com/MarvinTeichmann/MultiNet) -  SOTA for KITTI(Road Segmentation)  
研究机构 : 多伦多大学计算机科学、剑桥大学工程系、[FZI研究中心](https://www.fzi.de/en/about-us/)、Uber ATG   
论文 : [MultiNet: Real-time Joint Semantic Reasoning for Autonomous Driving](https://arxiv.org/abs/1612.07695)  
* [bermanmaxim/LovaszSoftmax](https://github.com/bermanmaxim/LovaszSoftmax) - Cityscapes:#1 for `Real-Time（76.9 fps）`、#16 for Mean IoU(63.06%),`CVPR 2018`   
研究机构 : 鲁汶大学  
论文 : [The Lovász-Softmax loss: A tractable surrogate for the optimization of the intersection-over-union measure in neural networks](https://arxiv.org/abs/1705.08790),
* [BichenWuUCB/SqueezeSeg](https://github.com/BichenWuUCB/SqueezeSeg) -  
研究机构 : 伯克利      
论文 : [SqueezeSeg: Convolutional Neural Nets with Recurrent CRF for Real-Time Road-Object Segmentation from 3D LiDAR Point Cloud](https://arxiv.org/abs/1710.07368),  
* `PSPNet`[tensorflow/models](https://github.com/tensorflow/models/tree/master/research/deeplab)和[hszhao/PSPNet](https://github.com/hszhao/PSPNet) - `SOTA in (Semantic Segmentation & Real-Time Semantic Segmentation)`，[more detail](https://paperswithcode.com/paper/pyramid-scene-parsing-network),`CVPR 2017`   
研究机构 : 香港中文大学、商汤    
论文 : [Pyramid Scene Parsing Network](https://arxiv.org/abs/1612.01105)   

### 传感器融合|Sensor Fusion  
* [HKUST-Aerial-Robotics/VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono) - SOTA，IROS 2018,IMU和（单目）摄像头融合的校正方法，用来校准IMU和相机之间的时间偏移。  
研究机构 : [港科大Aerial Robotics Group](http://uav.ust.hk/)  
论文 : [Online Temporal Calibration for Monocular Visual-Inertial Systems](https://arxiv.org/abs/1808.00692),
### 决策系统|Decision Making
* [xinleipan/VirtualtoReal-RL](https://github.com/xinleipan/VirtualtoReal-RL) -在虚拟环境通过强化学习来训练无人驾驶   
研究机构 : Berkley、清华大学、上海交通大学  
论文 : [Virtual to Real Reinforcement Learning for Autonomous Driving](https://arxiv.org/abs/1704.03952)
* [非官方][marsauto/europilot](https://github.com/marsauto/europilot)和[非官方][SullyChen/Autopilot-TensorFlow](https://github.com/SullyChen/Autopilot-TensorFlow)   
研究机构 : 英伟达  
论文 : [End to End Learning for Self-Driving Cars](https://arxiv.org/abs/1604.07316)  
### 运动规划|Motion Planer
* [非官方][Iftimie/ChauffeurNet](https://github.com/Iftimie/ChauffeurNet) -  Waymo出品，通过模仿学习对无人车进行运动规划，全文中文翻译:[知乎|每周一篇 & 无人驾驶](https://zhuanlan.zhihu.com/p/57275593)  
研究机构 : Waymo Research  
论文 : [ChauffeurNet: Learning to Drive by Imitating the Best and Synthesizing the Worst](https://arxiv.org/abs/1812.03079),


## 软件
### 仿真平台
* [英伟达 Drive Constellation](https://www.nvidia.cn/self-driving-cars/drive-constellation/) - 采用逼真的模拟技术，以更安全、更易扩展、
更经济有效的方式推动自动驾驶汽车上路行驶的进程。它利用两台不同服务器的计算能力来提供革命性的云计算平台，从而实现数十亿英里的自动驾驶汽车测试。 
* [优达 self-driving car|开源](https://github.com/udacity/self-driving-car) -用于纳米课程学习
* [英特尔Carla|开源](https://github.com/carla-simulator/carla)  - 用于城市自动驾驶系统的开发、训练和验证的开源模拟器，支持多种传感模式和环境条件的灵活配置
* [微软 Airsim|开源](https://github.com/Microsoft/AirSim) - 作为人工智能研究的平台，以实验自动驾驶汽车的深度学习，计算机视觉和强化学习算法。
* [LG LGSVL|开源](https://github.com/lgsvl/simulator) - 帮助开发者集中测试无人驾驶算法，目前平台已经集成了Duckietown, Autoware软件和百度Apollo平台。
* [百度 Apollo|开源](https://github.com/ApolloAuto/apollo) - 帮助汽车行业及自动驾驶领域的合作伙伴结合车辆和硬件系统，快速搭建一套属于自己的自动驾驶系统。

### 软件
* [Autoware|开源](https://github.com/CPFL/Autoware)  - 用于城市自动驾驶的集成开源软件。
* [Comma.ai Openpilot|开源](https://github.com/commaai/openpilot)  - 开源驱动代理。

### 可视化工具
* [优步ATG AVS|开源](https://avs.auto/#/) - 其主要包括两个repo: [xviz](https://github.com/uber/xviz)处理数据
和 [streetscape.gl](https://github.com/uber/streetscape.gl)进行场景渲染。
* [通用Cruise WorldView|开源](https://github.com/cruise-automation/webviz) -开放可视化组件便于开发者进行无人驾驶数据可视化处理。

### 其他
* [Stanford Driving Software](https://sourceforge.net/projects/stanforddriving/)  - 斯坦福自动驾驶汽车的较早时候软件基础设施。
* [GTA Robotics SDC Environment](https://github.com/OSSDC/self-driving-car-1)  - 为Udacity无人驾驶车（SDC）挑战做好准备的开发环境。
* [The OSCC Project](http://oscc.io/)  - 用于自动驾驶汽车开发的线控控制套件。

## 硬件


## 小游戏
* [TensorKart](https://github.com/kevinhughes27/TensorKart)  - 使用TensorFlow搭建的自驾驾驶MarioKart。
* [NeuroJS](https://github.com/janhuenermann/neurojs)  - javascript深度学习和强化学习库。 一个样本自动驾驶汽车实施。
* [Metacar](https://github.com/thibo73800/metacar) - 仅需通过浏览器就可以进行训练，为自动驾驶汽车提供强化学习环境。
* [DeepTraffic](https://github.com/lexfridman/deeptraffic) - 作为MIT深度学习课程的一部分, 作为认知深度强化学习小游戏。仅需通过浏览器设置参数就可以进行训练和评估。



#### 博客
* [Deep Learning and Autonomous Driving](https://handong1587.github.io/deep_learning/2015/10/09/dl-and-autonomous-driving.html)
* [[Medium] Self-Driving Cars](https://medium.com/self-driving-cars)

#### 知乎
##### 用户
* 黄浴
* 陈光
---

#### 推特
* [comma.ai](https://twitter.com/comma_ai)
* [[Udacity] David Silver](https://twitter.com/dsilver829)
* [[Udacity] Dhruv Parthasarathy](https://twitter.com/dhruvp)
* [[Udacity] Eric Gonzalez](https://twitter.com/ericrgon)
* [[Udacity] Oliver Cameron](https://twitter.com/olivercameron)
* [[Udacity] MacCallister Higgins](https://twitter.com/macjshiggins)
* [[Udacity] Sebastian Thrun](https://twitter.com/SebastianThrun)
* [[Google] Chris Urmson](https://twitter.com/chris_urmson)


## 法规

美国
* [California Regulatory Notice](https://www.dmv.ca.gov/portal/dmv/detail/vr/autonomous/testing)
* [Michigan Just Passed the Most Permissive Self-Driving Car Laws in the Country](http://fortune.com/2016/12/09/michigan-self-driving-cars/)
* [Car accidents involving a SDC in California](https://www.dmv.ca.gov/portal/dmv/detail/vr/autonomous/autonomousveh_ol316)
* [Nvidia starts testing its self-driving cars on public roads](http://www.theinquirer.net/inquirer/news/2479432/nvidia-starts-testing-its-self-driving-cars-on-public-roads)
