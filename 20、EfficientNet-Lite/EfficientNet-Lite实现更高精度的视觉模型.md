### EfficientNet-Lite实现更高精度的视觉模型

[原文](https://blog.tensorflow.org/2020/03/higher-accuracy-on-vision-models-with-efficientnet-lite.html?m=1)来自TensorFlow Blog

---

2019年5月，谷歌发布了一系列名为[EfficientNet](https://ai.googleblog.com/2019/05/efficientnet-improving-accuracy-and.html)的图像分类模型，该模型以最少的计算资源消耗实现了当时最高的准确度。但是此模型设计之初并没有考虑到嵌入式设备上的部署，所以如果EfficientNet可以在边缘设备上运行，它将为计算资源受限的移动端和IoT上的新颖应用打开大门。

TensorFlow作为谷歌的亲儿子，首先实现了在[TensorFlowLite](https://www.tensorflow.org/lite)框架下EfficientNet在嵌入式设备上的部署，新的模型称之为[EfficientNet-Lite](https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet/lite)。其主要运行平台是移动端CPU、GPU和边缘设备的TPU。

EfficientNet-Lite将EfficientNet的性能带到了边缘设备，并提供五种不同的模型变体，提供了从模型大小(推理延迟)由小变大的不同模型，可供灵活选择。类似于EfficientNet0-EfficientNet6，随着精度升高，其模型大小(推理延迟)越大。

EfficientNet-Lite4，经过整型量化之后，在ImageNet top-1达到80.4%的准确率，同时其在手机Pixel 4 CPU上达到实时(30ms/image)。

与常见的的图像分类模型的类似量化版本相比下图是量化的EfficientNet-Lite模型的性能。

![image-20200318115235636](https://i.loli.net/2020/03/18/5MZ8a2OtEmhf3Ij.png)

![截屏2020-03-18下午12.02.26](https://i.loli.net/2020/03/18/rNC8JMGl4yQITtV.png)

对于边缘设备来说，在进行部署的时候仍然还有非常多的挑战

**量化**，由于许多边缘设备的浮点运算支持有限，因此在边缘设备上量化是最有价值的部署操作。但是，量化操作通常需要非常复杂的训练过程，并且要在一定程度上抑制量化操作带来的精度损失。

TensorFlow Lite提供了[量化操作流程](https://www.tensorflow.org/lite/performance/post_training_quantization)可供参考,尽可能小的降低了精度损失。

**硬件异构**，同一种模型很难在不同的硬件上不做修改地运行起来，例如有移动GPU，移动NPU，还有TPU。由于硬件异构，所以每一种硬件支持的运算加速操作都不同，在EfficientNet中，很多操作都不能被硬件支持，所以不得不在原始的EfficientNet上做出了一下修改

- 删除了不支持的squeeze和excitation操作
- 使用ReLU6替换swish，可以提高训练后量化的质量
- 降低模型计算量的时候，固定stem和模型head



**TensorFlow提供工具用来进行训练后的模型量化加速**

[TensorFlow Model Optimization Toolkit](https://www.tensorflow.org/lite/performance/model_optimization)

仅通过整数后训练即可轻松对模型进行量化，而不会损失太多准确性（参考上面链接）。成功将模型大小减少4倍，同时将推理速度提高了2倍。

![截屏2020-03-18下午12.18.06](https://i.loli.net/2020/03/18/gBIJEP1tQo7hm8N.png)

第一次进行训练后量化的时候，精度掉的厉害，在ImageNet数据集上Top1 准确率从75%掉到46%，最后发现是因为量化输出范围过宽引起的，量化本质上是对浮点值进行缩放以适合int8存储

![截屏2020-03-18下午12.21.41](https://i.loli.net/2020/03/18/GBfCNkI6gS8hzo1.png)

在实验中，输出张量范围是-168到204，如以下示例所示

![2020-02-26](https://i.loli.net/2020/03/18/ylNef32jWDdpL6J.png)

由于很难将宽范围的浮点张量存储到int8的内存中，所以很可能掉点，通过用ReLU6代替[swish](https://arxiv.org/abs/1710.05941)，将输出限制为[0,6]，实验证明可以一定程度上解决这种问题，浮点精度75.1%量化之后精度可以保持到74.4%。

**可以在自己的数据集上尝试一下**

[TensorFlow Lite Model Maker](https://github.com/tensorflow/examples/tree/master/tensorflow_examples/lite/model_maker)