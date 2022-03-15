# AIoT__TensorFlowLite
Project practice and summary set for TensorFlow Lite, which is based on TensorFlow 2.x. 



# TensorFlow Lite 深度学习-开源-嵌入式

TensorFlow Lite 是 TensorFlow 针对移动和嵌入式设备的轻量级解决方案。TensorFlow Lite 的目标是移动和嵌入式设备，它赋予了这些设备在终端本地运行机器学习模型的能力，从而不再需要向云端服务器发送数据。这样一来，不但节省了网络流量、减少了时间开销，而且还充分帮助用户保护自己的隐私和敏感信息。

## TensorFlow Lite 网站

| TensorFlow lite官方 (Google)   | https://tensorflow.google.cn/lite/examples                   |
| ------------------------------ | ------------------------------------------------------------ |
| TensorFlow lite 的官方中文网页 | https://www.tensorflow.org/lite/examples  里面很多教程，可以看看。 |

## TensorFlow Lite 组件、架构

**组件包括**

- TensorFlow 模型（TensorFlow Model）：训练后的 TensorFlow 模型，保存在磁盘中。
- TensorFlow Lite 转换器（TensorFlow Lite Converter）：该程序将模型转换成 TensorFlow Lite 文件格式。
- TensorFlow Lite 模型文件（TensorFlow Lite Model File）：该格式基于 FlatBuffers，经过优化以适应最大速度和最小规模。

## TensorFlow Lite 预训练的模型

ensorFlow Lite 团队提供了一系列预训练模型（pre-trained models），用于解决各种机器学习问题。这些模型已经转换为能与 TensorFlow Lite 一起使用，且可以在您的应用程序中使用的模型。

这些预训练模型包括：

- [图像分类（Image classification）](https://tensorflow.google.cn/lite/models/image_classification/overview)
- [物体检测（Object detection）](https://tensorflow.google.cn/lite/models/object_detection/overview)
- [智能回复（Smart reply）](https://tensorflow.google.cn/lite/models/smart_reply/overview)
- [姿态估计（Pose estimation）](https://tensorflow.google.cn/lite/models/pose_estimation/overview)
- [语义分割（Segmentation）](https://tensorflow.google.cn/lite/models/segmentation/overview)
- 在[模型列表（Models）](https://tensorflow.google.cn/lite/models)中查看预训练模型的完整列表。
- 可以在许多其他地方得到预训练的 TensorFlow 模型，包括 [TensorFlow Hub](https://tensorflow.google.cn/hub)。在大多数情况下，这些模型不会以 TensorFlow Lite 格式提供，您必须在使用前[转换（convert）](https://tensorflow.google.cn/lite/guide/get_started#2_convert_the_model_format)这些模型。
- 重新训练模型（迁移学习 transfer learning）
