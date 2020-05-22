## 中科视拓发布seetaface6

3月31日，山世光团队中科视拓发布了最新的免费商业正式人脸识别应用包——SeetaFace6

- 基于[BSD协议]([https://baike.baidu.com/item/BSD%E5%8D%8F%E8%AE%AE/8013651?fr=aladdin](https://baike.baidu.com/item/BSD协议/8013651?fr=aladdin))，可以商业使用
- 基于tennis引擎，再也没有社区版和商业版的区别
- 开放基于MobileNet的识别模型，利于边缘设备部署
- 活体检测、口罩人脸识别、人脸属性分析，闭眼检测等等均开放

---

### 一、SeetaFace历史

**SeetaFace1**

2016年，深度学习刚刚开始进入到中小企业，我记得当时我们公司还在玩haar特征，当时在工控机上做人脸识别，又慢效果有不好。2016年中旬的时候，[SeetaFace1](https://github.com/seetaface/SeetaFaceEngine)发布，直接在LFW上做到98.6%的精度，速度还不算太慢，里面包含三个部分，人脸检测，人脸对齐，人脸识别，直接一套解决了人脸识别整个应用。

当时不少的实验室或者小公司就凭借一个SeetaFace的三个模型就可以出去接人脸识别项目了，我们自己捣鼓了很久的的识别算法，跟SeetaFace一比，直接决定不搞了，项目部署直接上SeetaFace了。真可谓是人脸识别开源界的一股清流。

**SeetaFace2**

2019年，[SeetaFace2](https://github.com/seetafaceengine/SeetaFace2)发布，千呼万唤始出来。但是从16年到19年这三年时间，人脸领域早已变成厮杀一片的红海，各种人脸算法层出不穷，嵌入式端，手机端，服务器端遍地开花。从业者们的目标只有一个，“更快更强”。

SeetaFace2包含人脸检测，关键点检测，人脸跟踪，人脸质量判断，人脸识别共5个模块。其中关键点检测相比第一代中，新增了81点landmarks，人脸质量判断，解决了因运动模糊等图像因素导致识别失败的问题。

对比SeetaFace2和SeetaFace1

![截屏2020-04-01下午1.34.25](https://i.loli.net/2020/04/01/GU8cW7TkFIrDhXZ.png)

在SeetaFace2中，人脸检测和人脸识别模型跟最新的开源的算法相比，其实并不占优势，对于项目部署而言也不太方便。因为不管是服务器端还是嵌入式端，都会有相对应的部署框架，例如，服务器端可定考虑TensorRT部署，嵌入式端会有海思的RuyiStudio转换caffe模型，安霸的有CVflow支持转caffe和TensorFlow，恩智浦有AIRunner部署TensorFlow。但是对于SeetaFace2而言，其模型是直接给出的bin文件，算法不依赖于任何框架，所以对于项目工程落地而言就跑不出太大的时间优势。但是其landmark算法效果还不错，然后人脸质量判断模块算法也值得研究，可以单独拿出来用到自己的项目中。

**SeetaFace6**

2020年3月31日，[SeetaFace6](https://github.com/seetafaceengine/SeetaFace6)发布，这次发布的v6版本正式与商用版本同步，之前中间的v4 v5等都是商业版。**这次的v6是商业版的第6版，同时也是社区版的第3版。**

这次v6版本包含了一下功能：人脸检测、人脸识别、人脸跟踪、口罩检测、年龄估计、性别估计、关键点检测、眼睛状态检测、人脸质量评估、静默活体。并且特别声明了，为了响应时事，还放出了**戴口罩人脸识别**。

![fr_mask](https://i.loli.net/2020/04/01/hcUad8mAF71Klvo.png)

静默活体检测也是目前人脸领域一大热点

![fas](https://i.loli.net/2020/04/01/QmbtSfrH16LATa5.jpg)

对比于SeetaFace2，v6版本采用了商用版最新的推理引擎TenniS，很大程度上提升了模型推理速度。

![截屏2020-04-01下午2.05.37](https://i.loli.net/2020/04/01/SNDOmE8qBx37R4A.png)

### 二、TenniS引擎

TenniS(Tenser based Edge Neural Network Inference System)是中科视拓自主研发的AI算法部署框架，提供从多个训练框架到多种硬件平台的通用部署能力。

通常我们使用深度学习框架(TensorFlow，caffe，pytorch等)来训练自己的算法模型，然后再通过一定的手段进行部署。根据部署平台的要求，封装成最终要使用的SDK。

TenniS框架部署逻辑如下

![1584581810687025948](https://i.loli.net/2020/04/01/tKCDEnYceUlF5zr.jpg)

中科视拓采用将训练模型转化为TenniS的模型，然后再根据硬件平台的不同，例如x86，ARM，CUDA等，生成适合不同平台的SDK。由于TenniS提供了很好的底层兼容性，可以直接使用c++在不同平台的部署。

![1584581843528098924](https://i.loli.net/2020/04/01/V7Q1W3gXdjf5RD8.jpg)

**三、SeetaFace6**

这次开放的版本还是使用C++作为开放接口，支持x86和ARM架构。将会支持Ubuntu、CenterOS、macOS、Android、iOS，同样地不依赖任何第三方库。

算法SDK，模型文件，已经提供下载链接

这篇先写个大概，这两天我会将代码跑起来试一波。

跑起来的效果，下一篇文章再写吧。

[SeetaFace入门教程](http://leanote.com/blog/post/5e7d6cecab64412ae60016ef)

后台回复“face”关键词，获取SDK和模型文件。

