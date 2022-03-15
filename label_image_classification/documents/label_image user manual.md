# label_image 图像分类



## Step_01) 复制到MPU里面所需要的文件，并放到 MPU 里面。

（例如，平台为 NXP 的 i.MX8M,存于目录：/app/AIOT/label_image ）

- label_image  交叉编译生成的可执行文件
- mobilenet_quant_v1_224.tflite   要用到的TensorFlow Lite 模型，用于做图像分类（例如，输入一张 鼠标的照片，运行之后，会显示此片为鼠标的概率是最大）
- picture.bmp 要测试的图片，可以自行更换照片



## Step_02） 将要“识别的图片”，用Windows自带“Paint”工具，转成bmp格式

再将图片名称，改成“picture.bmp”

覆盖到MPU的目录下：/app/AIOT/label_image

![图片转成 bmp 格式](figures/图片转成 bmp 格式.jpg)



## Step_03）How to run the this demo:

```bash
cd /app/AIOT/label_image

./label_image -v 1 -m ./mobilenet_quant_v1_224.tflite  -i ./picture.bmp -l ./labels.txt

or

./Run.sh
```



## Step_04）查看，运行结果Log：  0.921569: 674 mouse

```
[root@test]# ll
-rwxrwxrwx    1 root     root           136 Jul 22  2020 ReadMe.txt
-rwxrwxrwx    1 root     root           136 Jul 22  2020 Run.sh
-rwxrwxrwx    1 root     root       2430054 Oct 24  2019 catBMP.bmp
-rwxrwxrwx    1 root     root        270054 Oct 24  2019 chair300.bmp
-rwxrwxrwx    1 root     root        940650 May 20 07:59 grace_hopper.bmp
-rwxrwxrwx    1 root     root       3123696 Jul 23  2020 label_image
-rwxrwxrwx    1 root     root         10484 Oct 30  2017 labels.txt
-rwxrwxrwx    1 root     root         10484 Feb 26  2019 labels_mobilenet_quant_v1_224.txt
-rwxrwxrwx    1 root     root       4276100 Nov  9  2017 mobilenet_quant_v1_224.tflite
-rwxrwxrwx    1 root     root       4276352 Aug  3  2018 mobilenet_v1_1.0_224_quant.tflite
-rwxrwxrwx    1 root     root        499554 Jul 22  2020 picture.bmp
[root@test label_image]# ./Run.sh
Loaded model ./mobilenet_quant_v1_224.tflite
resolved reporter
tensors size: 89
nodes size: 31
inputs: 1
input(0) name: Placeholder
0: MobilenetV1/Logits/AvgPool_1a/AvgPool, 1024, 3, 0.0235285, 0
1: MobilenetV1/Logits/Conv2d_1c_1x1/BiasAdd, 1001, 3, 0.165351, 74
2: MobilenetV1/Logits/Conv2d_1c_1x1/Conv2D_bias, 4004, 2, 0.000116509, 0
3: MobilenetV1/Logits/Conv2d_1c_1x1/weights_quant/FakeQuantWithMinMaxVars, 1025024, 3, 0.00495183, 67
4: MobilenetV1/MobilenetV1/Conv2d_0/Conv2D_Fold_bias, 128, 2, 0.000161006, 0
5: MobilenetV1/MobilenetV1/Conv2d_0/Relu6, 401408, 3, 0.0235285, 0
6: MobilenetV1/MobilenetV1/Conv2d_0/weights_quant/FakeQuantWithMinMaxVars, 864, 3, 0.0410565, 108
7: MobilenetV1/MobilenetV1/Conv2d_10_depthwise/Relu6, 100352, 3, 0.0235285, 0
8: MobilenetV1/MobilenetV1/Conv2d_10_depthwise/depthwise_Fold_bias, 2048, 2, 0.00039105, 0
9: MobilenetV1/MobilenetV1/Conv2d_10_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0166203, 131
10: MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000189115, 0
11: MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Relu6, 100352, 3, 0.0235285, 0
12: MobilenetV1/MobilenetV1/Conv2d_10_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.00803769, 148
13: MobilenetV1/MobilenetV1/Conv2d_11_depthwise/Relu6, 100352, 3, 0.0235285, 0
14: MobilenetV1/MobilenetV1/Conv2d_11_depthwise/depthwise_Fold_bias, 2048, 2, 0.000332007, 0
15: MobilenetV1/MobilenetV1/Conv2d_11_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0141109, 123
16: MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000261272, 0
17: MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Relu6, 100352, 3, 0.0235285, 0
18: MobilenetV1/MobilenetV1/Conv2d_11_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.0111045, 115
19: MobilenetV1/MobilenetV1/Conv2d_12_depthwise/Relu6, 25088, 3, 0.0235285, 0
20: MobilenetV1/MobilenetV1/Conv2d_12_depthwise/depthwise_Fold_bias, 2048, 2, 0.00012358, 0
21: MobilenetV1/MobilenetV1/Conv2d_12_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.00525234, 117
22: MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Conv2D_Fold_bias, 4096, 2, 0.000463319, 0
23: MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Relu6, 50176, 3, 0.0235285, 0
24: MobilenetV1/MobilenetV1/Conv2d_12_pointwise/weights_quant/FakeQuantWithMinMaxVars, 524288, 3, 0.0196918, 144
25: MobilenetV1/MobilenetV1/Conv2d_13_depthwise/Relu6, 50176, 3, 0.0235285, 0
26: MobilenetV1/MobilenetV1/Conv2d_13_depthwise/depthwise_Fold_bias, 4096, 2, 0.00128296, 0
27: MobilenetV1/MobilenetV1/Conv2d_13_depthwise/weights_quant/FakeQuantWithMinMaxVars, 9216, 3, 0.0545281, 211
28: MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Conv2D_Fold_bias, 4096, 2, 0.000587459, 0
29: MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Relu6, 50176, 3, 0.0235285, 0
30: MobilenetV1/MobilenetV1/Conv2d_13_pointwise/weights_quant/FakeQuantWithMinMaxVars, 1048576, 3, 0.024968, 140
31: MobilenetV1/MobilenetV1/Conv2d_1_depthwise/Relu6, 401408, 3, 0.0235285, 0
32: MobilenetV1/MobilenetV1/Conv2d_1_depthwise/depthwise_Fold_bias, 128, 2, 0.0135622, 0
33: MobilenetV1/MobilenetV1/Conv2d_1_depthwise/weights_quant/FakeQuantWithMinMaxVars, 288, 3, 0.576417, 53
34: MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Conv2D_Fold_bias, 256, 2, 0.000240194, 0
35: MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Relu6, 802816, 3, 0.0235285, 0
36: MobilenetV1/MobilenetV1/Conv2d_1_pointwise/weights_quant/FakeQuantWithMinMaxVars, 2048, 3, 0.0102087, 101
37: MobilenetV1/MobilenetV1/Conv2d_2_depthwise/Relu6, 200704, 3, 0.0235285, 0
38: MobilenetV1/MobilenetV1/Conv2d_2_depthwise/depthwise_Fold_bias, 256, 2, 0.00194196, 0
39: MobilenetV1/MobilenetV1/Conv2d_2_depthwise/weights_quant/FakeQuantWithMinMaxVars, 576, 3, 0.0825367, 46
40: MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Conv2D_Fold_bias, 512, 2, 0.000395467, 0
41: MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Relu6, 401408, 3, 0.0235285, 0
42: MobilenetV1/MobilenetV1/Conv2d_2_pointwise/weights_quant/FakeQuantWithMinMaxVars, 8192, 3, 0.016808, 118
43: MobilenetV1/MobilenetV1/Conv2d_3_depthwise/Relu6, 401408, 3, 0.0235285, 0
44: MobilenetV1/MobilenetV1/Conv2d_3_depthwise/depthwise_Fold_bias, 512, 2, 0.000966625, 0
45: MobilenetV1/MobilenetV1/Conv2d_3_depthwise/weights_quant/FakeQuantWithMinMaxVars, 1152, 3, 0.0410832, 109
46: MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Conv2D_Fold_bias, 512, 2, 0.000266758, 0
47: MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Relu6, 401408, 3, 0.0235285, 0
48: MobilenetV1/MobilenetV1/Conv2d_3_pointwise/weights_quant/FakeQuantWithMinMaxVars, 16384, 3, 0.0113377, 110
49: MobilenetV1/MobilenetV1/Conv2d_4_depthwise/Relu6, 100352, 3, 0.0235285, 0
50: MobilenetV1/MobilenetV1/Conv2d_4_depthwise/depthwise_Fold_bias, 512, 2, 0.000243408, 0
51: MobilenetV1/MobilenetV1/Conv2d_4_depthwise/weights_quant/FakeQuantWithMinMaxVars, 1152, 3, 0.0103453, 137
52: MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Conv2D_Fold_bias, 1024, 2, 0.000325615, 0
53: MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Relu6, 200704, 3, 0.0235285, 0
54: MobilenetV1/MobilenetV1/Conv2d_4_pointwise/weights_quant/FakeQuantWithMinMaxVars, 32768, 3, 0.0138392, 129
55: MobilenetV1/MobilenetV1/Conv2d_5_depthwise/Relu6, 200704, 3, 0.0235285, 0
56: MobilenetV1/MobilenetV1/Conv2d_5_depthwise/depthwise_Fold_bias, 1024, 2, 0.000743922, 0
57: MobilenetV1/MobilenetV1/Conv2d_5_depthwise/weights_quant/FakeQuantWithMinMaxVars, 2304, 3, 0.031618, 77
58: MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Conv2D_Fold_bias, 1024, 2, 0.000189554, 0
59: MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Relu6, 200704, 3, 0.0235285, 0
60: MobilenetV1/MobilenetV1/Conv2d_5_pointwise/weights_quant/FakeQuantWithMinMaxVars, 65536, 3, 0.00805637, 127
61: MobilenetV1/MobilenetV1/Conv2d_6_depthwise/Relu6, 50176, 3, 0.0235285, 0
62: MobilenetV1/MobilenetV1/Conv2d_6_depthwise/depthwise_Fold_bias, 1024, 2, 0.000221356, 0
63: MobilenetV1/MobilenetV1/Conv2d_6_depthwise/weights_quant/FakeQuantWithMinMaxVars, 2304, 3, 0.00940801, 123
64: MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Conv2D_Fold_bias, 2048, 2, 0.0002464, 0
65: MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Relu6, 100352, 3, 0.0235285, 0
66: MobilenetV1/MobilenetV1/Conv2d_6_pointwise/weights_quant/FakeQuantWithMinMaxVars, 131072, 3, 0.0104724, 126
67: MobilenetV1/MobilenetV1/Conv2d_7_depthwise/Relu6, 100352, 3, 0.0235285, 0
68: MobilenetV1/MobilenetV1/Conv2d_7_depthwise/depthwise_Fold_bias, 2048, 2, 0.000485006, 0
69: MobilenetV1/MobilenetV1/Conv2d_7_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0206136, 129
70: MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Conv2D_Fold_bias, 2048, 2, 0.00019147, 0
71: MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Relu6, 100352, 3, 0.0235285, 0
72: MobilenetV1/MobilenetV1/Conv2d_7_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.0081378, 115
73: MobilenetV1/MobilenetV1/Conv2d_8_depthwise/Relu6, 100352, 3, 0.0235285, 0
74: MobilenetV1/MobilenetV1/Conv2d_8_depthwise/depthwise_Fold_bias, 2048, 2, 0.000389983, 0
75: MobilenetV1/MobilenetV1/Conv2d_8_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0165749, 115
76: MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000251079, 0
77: MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Relu6, 100352, 3, 0.0235285, 0
78: MobilenetV1/MobilenetV1/Conv2d_8_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.0106713, 170
79: MobilenetV1/MobilenetV1/Conv2d_9_depthwise/Relu6, 100352, 3, 0.0235285, 0
80: MobilenetV1/MobilenetV1/Conv2d_9_depthwise/depthwise_Fold_bias, 2048, 2, 0.000351091, 0
81: MobilenetV1/MobilenetV1/Conv2d_9_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.014922, 132
82: MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000161186, 0
83: MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Relu6, 100352, 3, 0.0235285, 0
84: MobilenetV1/MobilenetV1/Conv2d_9_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.00685069, 120
85: MobilenetV1/Predictions/Reshape, 1001, 3, 0.165351, 74
86: MobilenetV1/Predictions/Reshape/shape, 8, 2, 0, 0
87: MobilenetV1/Predictions/Softmax, 1001, 3, 0.00390625, 0
88: Placeholder, 150528, 3, 0.00392157, 0
len: 499554
width, height, channels: 500, 333, 3
input: 88
number of inputs: 1
number of outputs: 1
Interpreter has 90 tensors and 31 nodes
Inputs: 88
Outputs: 87

Tensor   0 MobilenetV1/Logits/AvgPool_1a/AvgPool kTfLiteUInt8  kTfLiteArenaRw       1024 bytes ( 0.0 MB)  1 1 1 1024
Tensor   1 MobilenetV1/Logits/Conv2d_1c_1x1/BiasAdd kTfLiteUInt8  kTfLiteArenaRw       1001 bytes ( 0.0 MB)  1 1 1 1001
Tensor   2 MobilenetV1/Logits/Conv2d_1c_1x1/Conv2D_bias kTfLiteInt32   kTfLiteMmapRo       4004 bytes ( 0.0 MB)  1001
Tensor   3 MobilenetV1/Logits/Conv2d_1c_1x1/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo    1025024 bytes ( 1.0 MB)  1001 1 1 1024
Tensor   4 MobilenetV1/MobilenetV1/Conv2d_0/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        128 bytes ( 0.0 MB)  32
Tensor   5 MobilenetV1/MobilenetV1/Conv2d_0/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 112 112 32
Tensor   6 MobilenetV1/MobilenetV1/Conv2d_0/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo        864 bytes ( 0.0 MB)  32 3 3 3
Tensor   7 MobilenetV1/MobilenetV1/Conv2d_10_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor   8 MobilenetV1/MobilenetV1/Conv2d_10_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor   9 MobilenetV1/MobilenetV1/Conv2d_10_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  10 MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  11 MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  12 MobilenetV1/MobilenetV1/Conv2d_10_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  13 MobilenetV1/MobilenetV1/Conv2d_11_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  14 MobilenetV1/MobilenetV1/Conv2d_11_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  15 MobilenetV1/MobilenetV1/Conv2d_11_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  16 MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  17 MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  18 MobilenetV1/MobilenetV1/Conv2d_11_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  19 MobilenetV1/MobilenetV1/Conv2d_12_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      25088 bytes ( 0.0 MB)  1 7 7 512
Tensor  20 MobilenetV1/MobilenetV1/Conv2d_12_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  21 MobilenetV1/MobilenetV1/Conv2d_12_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  22 MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       4096 bytes ( 0.0 MB)  1024
Tensor  23 MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 7 7 1024
Tensor  24 MobilenetV1/MobilenetV1/Conv2d_12_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     524288 bytes ( 0.5 MB)  1024 1 1 512
Tensor  25 MobilenetV1/MobilenetV1/Conv2d_13_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 7 7 1024
Tensor  26 MobilenetV1/MobilenetV1/Conv2d_13_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       4096 bytes ( 0.0 MB)  1024
Tensor  27 MobilenetV1/MobilenetV1/Conv2d_13_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       9216 bytes ( 0.0 MB)  1 3 3 1024
Tensor  28 MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       4096 bytes ( 0.0 MB)  1024
Tensor  29 MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 7 7 1024
Tensor  30 MobilenetV1/MobilenetV1/Conv2d_13_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo    1048576 bytes ( 1.0 MB)  1024 1 1 1024
Tensor  31 MobilenetV1/MobilenetV1/Conv2d_1_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 112 112 32
Tensor  32 MobilenetV1/MobilenetV1/Conv2d_1_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        128 bytes ( 0.0 MB)  32
Tensor  33 MobilenetV1/MobilenetV1/Conv2d_1_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo        288 bytes ( 0.0 MB)  1 3 3 32
Tensor  34 MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        256 bytes ( 0.0 MB)  64
Tensor  35 MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     802816 bytes ( 0.8 MB)  1 112 112 64
Tensor  36 MobilenetV1/MobilenetV1/Conv2d_1_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  64 1 1 32
Tensor  37 MobilenetV1/MobilenetV1/Conv2d_2_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 56 56 64
Tensor  38 MobilenetV1/MobilenetV1/Conv2d_2_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        256 bytes ( 0.0 MB)  64
Tensor  39 MobilenetV1/MobilenetV1/Conv2d_2_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo        576 bytes ( 0.0 MB)  1 3 3 64
Tensor  40 MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  41 MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 56 56 128
Tensor  42 MobilenetV1/MobilenetV1/Conv2d_2_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       8192 bytes ( 0.0 MB)  128 1 1 64
Tensor  43 MobilenetV1/MobilenetV1/Conv2d_3_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 56 56 128
Tensor  44 MobilenetV1/MobilenetV1/Conv2d_3_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  45 MobilenetV1/MobilenetV1/Conv2d_3_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       1152 bytes ( 0.0 MB)  1 3 3 128
Tensor  46 MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  47 MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 56 56 128
Tensor  48 MobilenetV1/MobilenetV1/Conv2d_3_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo      16384 bytes ( 0.0 MB)  128 1 1 128
Tensor  49 MobilenetV1/MobilenetV1/Conv2d_4_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 28 28 128
Tensor  50 MobilenetV1/MobilenetV1/Conv2d_4_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  51 MobilenetV1/MobilenetV1/Conv2d_4_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       1152 bytes ( 0.0 MB)  1 3 3 128
Tensor  52 MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  53 MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 28 28 256
Tensor  54 MobilenetV1/MobilenetV1/Conv2d_4_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo      32768 bytes ( 0.0 MB)  256 1 1 128
Tensor  55 MobilenetV1/MobilenetV1/Conv2d_5_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 28 28 256
Tensor  56 MobilenetV1/MobilenetV1/Conv2d_5_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  57 MobilenetV1/MobilenetV1/Conv2d_5_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       2304 bytes ( 0.0 MB)  1 3 3 256
Tensor  58 MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  59 MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 28 28 256
Tensor  60 MobilenetV1/MobilenetV1/Conv2d_5_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo      65536 bytes ( 0.1 MB)  256 1 1 256
Tensor  61 MobilenetV1/MobilenetV1/Conv2d_6_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 14 14 256
Tensor  62 MobilenetV1/MobilenetV1/Conv2d_6_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  63 MobilenetV1/MobilenetV1/Conv2d_6_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       2304 bytes ( 0.0 MB)  1 3 3 256
Tensor  64 MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  65 MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  66 MobilenetV1/MobilenetV1/Conv2d_6_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     131072 bytes ( 0.1 MB)  512 1 1 256
Tensor  67 MobilenetV1/MobilenetV1/Conv2d_7_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  68 MobilenetV1/MobilenetV1/Conv2d_7_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  69 MobilenetV1/MobilenetV1/Conv2d_7_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  70 MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  71 MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  72 MobilenetV1/MobilenetV1/Conv2d_7_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  73 MobilenetV1/MobilenetV1/Conv2d_8_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  74 MobilenetV1/MobilenetV1/Conv2d_8_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  75 MobilenetV1/MobilenetV1/Conv2d_8_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  76 MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  77 MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  78 MobilenetV1/MobilenetV1/Conv2d_8_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  79 MobilenetV1/MobilenetV1/Conv2d_9_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  80 MobilenetV1/MobilenetV1/Conv2d_9_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  81 MobilenetV1/MobilenetV1/Conv2d_9_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  82 MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  83 MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  84 MobilenetV1/MobilenetV1/Conv2d_9_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  85 MobilenetV1/Predictions/Reshape kTfLiteUInt8  kTfLiteArenaRw       1001 bytes ( 0.0 MB)  1 1001
Tensor  86 MobilenetV1/Predictions/Reshape/shape kTfLiteInt32   kTfLiteMmapRo          8 bytes ( 0.0 MB)  2
Tensor  87 MobilenetV1/Predictions/Softmax kTfLiteUInt8  kTfLiteArenaRw       1001 bytes ( 0.0 MB)  1 1001
Tensor  88 Placeholder          kTfLiteUInt8  kTfLiteArenaRw     150528 bytes ( 0.1 MB)  1 224 224 3
Tensor  89 (null)               kTfLiteUInt8  kTfLiteArenaRw     338688 bytes ( 0.3 MB)  1 112 112 27

Node   0 Operator Builtin Code   3 CONV_2D
  Inputs: 88 6 4
  Outputs: 5
  Temporaries: 89
Node   1 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 5 33 32
  Outputs: 31
Node   2 Operator Builtin Code   3 CONV_2D
  Inputs: 31 36 34
  Outputs: 35
Node   3 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 35 39 38
  Outputs: 37
Node   4 Operator Builtin Code   3 CONV_2D
  Inputs: 37 42 40
  Outputs: 41
Node   5 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 41 45 44
  Outputs: 43
Node   6 Operator Builtin Code   3 CONV_2D
  Inputs: 43 48 46
  Outputs: 47
Node   7 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 47 51 50
  Outputs: 49
Node   8 Operator Builtin Code   3 CONV_2D
  Inputs: 49 54 52
  Outputs: 53
Node   9 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 53 57 56
  Outputs: 55
Node  10 Operator Builtin Code   3 CONV_2D
  Inputs: 55 60 58
  Outputs: 59
Node  11 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 59 63 62
  Outputs: 61
Node  12 Operator Builtin Code   3 CONV_2D
  Inputs: 61 66 64
  Outputs: 65
Node  13 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 65 69 68
  Outputs: 67
Node  14 Operator Builtin Code   3 CONV_2D
  Inputs: 67 72 70
  Outputs: 71
Node  15 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 71 75 74
  Outputs: 73
Node  16 Operator Builtin Code   3 CONV_2D
  Inputs: 73 78 76
  Outputs: 77
Node  17 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 77 81 80
  Outputs: 79
Node  18 Operator Builtin Code   3 CONV_2D
  Inputs: 79 84 82
  Outputs: 83
Node  19 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 83 9 8
  Outputs: 7
Node  20 Operator Builtin Code   3 CONV_2D
  Inputs: 7 12 10
  Outputs: 11
Node  21 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 11 15 14
  Outputs: 13
Node  22 Operator Builtin Code   3 CONV_2D
  Inputs: 13 18 16
  Outputs: 17
Node  23 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 17 21 20
  Outputs: 19
Node  24 Operator Builtin Code   3 CONV_2D
  Inputs: 19 24 22
  Outputs: 23
Node  25 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 23 27 26
  Outputs: 25
Node  26 Operator Builtin Code   3 CONV_2D
  Inputs: 25 30 28
  Outputs: 29
Node  27 Operator Builtin Code   1 AVERAGE_POOL_2D
  Inputs: 29
  Outputs: 0
Node  28 Operator Builtin Code   3 CONV_2D
  Inputs: 0 3 2
  Outputs: 1
Node  29 Operator Builtin Code  22 RESHAPE
  Inputs: 1 86
  Outputs: 85
Node  30 Operator Builtin Code  25 SOFTMAX
  Inputs: 85
  Outputs: 87
invoked 
average time: 496.526 ms 
0.921569: 674 mouse
0.0156863: 845 switch
0.0156863: 774 saltshaker
0.0117647: 723 ping-pong ball
0.00784314: 819 spotlight
[root@hon-grip-aio-200-02122A label_image]# 













ll      
-rwxrwxrwx    1 root     root           136 Jul 22  2020 ReadMe.txt
-rwxrwxrwx    1 root     root           136 Jul 22  2020 Run.sh
-rwxrwxrwx    1 root     root       2430054 Oct 24  2019 catBMP.bmp
-rwxrwxrwx    1 root     root        270054 Oct 24  2019 chair300.bmp
-rwxrwxrwx    1 root     root        940650 May 20 07:59 grace_hopper.bmp
-rwxrwxrwx    1 root     root       3123696 Jul 23  2020 label_image
-rwxrwxrwx    1 root     root         10484 Oct 30  2017 labels.txt
-rwxrwxrwx    1 root     root         10484 Feb 26  2019 labels_mobilenet_quant_v1_224.txt
-rwxrwxrwx    1 root     root       4276100 Nov  9  2017 mobilenet_quant_v1_224.tflite
-rwxrwxrwx    1 root     root       4276352 Aug  3  2018 mobilenet_v1_1.0_224_quant.tflite
-rwxrwxrwx    1 root     root        499554 Jul 22  2020 picture.bmp
[root@hon-grip-aio-200-02122A label_image]# ./Run.sh
Loaded model ./mobilenet_quant_v1_224.tflite
resolved reporter
tensors size: 89
nodes size: 31
inputs: 1
input(0) name: Placeholder
0: MobilenetV1/Logits/AvgPool_1a/AvgPool, 1024, 3, 0.0235285, 0
1: MobilenetV1/Logits/Conv2d_1c_1x1/BiasAdd, 1001, 3, 0.165351, 74
2: MobilenetV1/Logits/Conv2d_1c_1x1/Conv2D_bias, 4004, 2, 0.000116509, 0
3: MobilenetV1/Logits/Conv2d_1c_1x1/weights_quant/FakeQuantWithMinMaxVars, 1025024, 3, 0.00495183, 67
4: MobilenetV1/MobilenetV1/Conv2d_0/Conv2D_Fold_bias, 128, 2, 0.000161006, 0
5: MobilenetV1/MobilenetV1/Conv2d_0/Relu6, 401408, 3, 0.0235285, 0
6: MobilenetV1/MobilenetV1/Conv2d_0/weights_quant/FakeQuantWithMinMaxVars, 864, 3, 0.0410565, 108
7: MobilenetV1/MobilenetV1/Conv2d_10_depthwise/Relu6, 100352, 3, 0.0235285, 0
8: MobilenetV1/MobilenetV1/Conv2d_10_depthwise/depthwise_Fold_bias, 2048, 2, 0.00039105, 0
9: MobilenetV1/MobilenetV1/Conv2d_10_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0166203, 131
10: MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000189115, 0
11: MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Relu6, 100352, 3, 0.0235285, 0
12: MobilenetV1/MobilenetV1/Conv2d_10_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.00803769, 148
13: MobilenetV1/MobilenetV1/Conv2d_11_depthwise/Relu6, 100352, 3, 0.0235285, 0
14: MobilenetV1/MobilenetV1/Conv2d_11_depthwise/depthwise_Fold_bias, 2048, 2, 0.000332007, 0
15: MobilenetV1/MobilenetV1/Conv2d_11_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0141109, 123
16: MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000261272, 0
17: MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Relu6, 100352, 3, 0.0235285, 0
18: MobilenetV1/MobilenetV1/Conv2d_11_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.0111045, 115
19: MobilenetV1/MobilenetV1/Conv2d_12_depthwise/Relu6, 25088, 3, 0.0235285, 0
20: MobilenetV1/MobilenetV1/Conv2d_12_depthwise/depthwise_Fold_bias, 2048, 2, 0.00012358, 0
21: MobilenetV1/MobilenetV1/Conv2d_12_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.00525234, 117
22: MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Conv2D_Fold_bias, 4096, 2, 0.000463319, 0
23: MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Relu6, 50176, 3, 0.0235285, 0
24: MobilenetV1/MobilenetV1/Conv2d_12_pointwise/weights_quant/FakeQuantWithMinMaxVars, 524288, 3, 0.0196918, 144
25: MobilenetV1/MobilenetV1/Conv2d_13_depthwise/Relu6, 50176, 3, 0.0235285, 0
26: MobilenetV1/MobilenetV1/Conv2d_13_depthwise/depthwise_Fold_bias, 4096, 2, 0.00128296, 0
27: MobilenetV1/MobilenetV1/Conv2d_13_depthwise/weights_quant/FakeQuantWithMinMaxVars, 9216, 3, 0.0545281, 211
28: MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Conv2D_Fold_bias, 4096, 2, 0.000587459, 0
29: MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Relu6, 50176, 3, 0.0235285, 0
30: MobilenetV1/MobilenetV1/Conv2d_13_pointwise/weights_quant/FakeQuantWithMinMaxVars, 1048576, 3, 0.024968, 140
31: MobilenetV1/MobilenetV1/Conv2d_1_depthwise/Relu6, 401408, 3, 0.0235285, 0
32: MobilenetV1/MobilenetV1/Conv2d_1_depthwise/depthwise_Fold_bias, 128, 2, 0.0135622, 0
33: MobilenetV1/MobilenetV1/Conv2d_1_depthwise/weights_quant/FakeQuantWithMinMaxVars, 288, 3, 0.576417, 53
34: MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Conv2D_Fold_bias, 256, 2, 0.000240194, 0
35: MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Relu6, 802816, 3, 0.0235285, 0
36: MobilenetV1/MobilenetV1/Conv2d_1_pointwise/weights_quant/FakeQuantWithMinMaxVars, 2048, 3, 0.0102087, 101
37: MobilenetV1/MobilenetV1/Conv2d_2_depthwise/Relu6, 200704, 3, 0.0235285, 0
38: MobilenetV1/MobilenetV1/Conv2d_2_depthwise/depthwise_Fold_bias, 256, 2, 0.00194196, 0
39: MobilenetV1/MobilenetV1/Conv2d_2_depthwise/weights_quant/FakeQuantWithMinMaxVars, 576, 3, 0.0825367, 46
40: MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Conv2D_Fold_bias, 512, 2, 0.000395467, 0
41: MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Relu6, 401408, 3, 0.0235285, 0
42: MobilenetV1/MobilenetV1/Conv2d_2_pointwise/weights_quant/FakeQuantWithMinMaxVars, 8192, 3, 0.016808, 118
43: MobilenetV1/MobilenetV1/Conv2d_3_depthwise/Relu6, 401408, 3, 0.0235285, 0
44: MobilenetV1/MobilenetV1/Conv2d_3_depthwise/depthwise_Fold_bias, 512, 2, 0.000966625, 0
45: MobilenetV1/MobilenetV1/Conv2d_3_depthwise/weights_quant/FakeQuantWithMinMaxVars, 1152, 3, 0.0410832, 109
46: MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Conv2D_Fold_bias, 512, 2, 0.000266758, 0
47: MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Relu6, 401408, 3, 0.0235285, 0
48: MobilenetV1/MobilenetV1/Conv2d_3_pointwise/weights_quant/FakeQuantWithMinMaxVars, 16384, 3, 0.0113377, 110
49: MobilenetV1/MobilenetV1/Conv2d_4_depthwise/Relu6, 100352, 3, 0.0235285, 0
50: MobilenetV1/MobilenetV1/Conv2d_4_depthwise/depthwise_Fold_bias, 512, 2, 0.000243408, 0
51: MobilenetV1/MobilenetV1/Conv2d_4_depthwise/weights_quant/FakeQuantWithMinMaxVars, 1152, 3, 0.0103453, 137
52: MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Conv2D_Fold_bias, 1024, 2, 0.000325615, 0
53: MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Relu6, 200704, 3, 0.0235285, 0
54: MobilenetV1/MobilenetV1/Conv2d_4_pointwise/weights_quant/FakeQuantWithMinMaxVars, 32768, 3, 0.0138392, 129
55: MobilenetV1/MobilenetV1/Conv2d_5_depthwise/Relu6, 200704, 3, 0.0235285, 0
56: MobilenetV1/MobilenetV1/Conv2d_5_depthwise/depthwise_Fold_bias, 1024, 2, 0.000743922, 0
57: MobilenetV1/MobilenetV1/Conv2d_5_depthwise/weights_quant/FakeQuantWithMinMaxVars, 2304, 3, 0.031618, 77
58: MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Conv2D_Fold_bias, 1024, 2, 0.000189554, 0
59: MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Relu6, 200704, 3, 0.0235285, 0
60: MobilenetV1/MobilenetV1/Conv2d_5_pointwise/weights_quant/FakeQuantWithMinMaxVars, 65536, 3, 0.00805637, 127
61: MobilenetV1/MobilenetV1/Conv2d_6_depthwise/Relu6, 50176, 3, 0.0235285, 0
62: MobilenetV1/MobilenetV1/Conv2d_6_depthwise/depthwise_Fold_bias, 1024, 2, 0.000221356, 0
63: MobilenetV1/MobilenetV1/Conv2d_6_depthwise/weights_quant/FakeQuantWithMinMaxVars, 2304, 3, 0.00940801, 123
64: MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Conv2D_Fold_bias, 2048, 2, 0.0002464, 0
65: MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Relu6, 100352, 3, 0.0235285, 0
66: MobilenetV1/MobilenetV1/Conv2d_6_pointwise/weights_quant/FakeQuantWithMinMaxVars, 131072, 3, 0.0104724, 126
67: MobilenetV1/MobilenetV1/Conv2d_7_depthwise/Relu6, 100352, 3, 0.0235285, 0
68: MobilenetV1/MobilenetV1/Conv2d_7_depthwise/depthwise_Fold_bias, 2048, 2, 0.000485006, 0
69: MobilenetV1/MobilenetV1/Conv2d_7_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0206136, 129
70: MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Conv2D_Fold_bias, 2048, 2, 0.00019147, 0
71: MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Relu6, 100352, 3, 0.0235285, 0
72: MobilenetV1/MobilenetV1/Conv2d_7_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.0081378, 115
73: MobilenetV1/MobilenetV1/Conv2d_8_depthwise/Relu6, 100352, 3, 0.0235285, 0
74: MobilenetV1/MobilenetV1/Conv2d_8_depthwise/depthwise_Fold_bias, 2048, 2, 0.000389983, 0
75: MobilenetV1/MobilenetV1/Conv2d_8_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.0165749, 115
76: MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000251079, 0
77: MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Relu6, 100352, 3, 0.0235285, 0
78: MobilenetV1/MobilenetV1/Conv2d_8_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.0106713, 170
79: MobilenetV1/MobilenetV1/Conv2d_9_depthwise/Relu6, 100352, 3, 0.0235285, 0
80: MobilenetV1/MobilenetV1/Conv2d_9_depthwise/depthwise_Fold_bias, 2048, 2, 0.000351091, 0
81: MobilenetV1/MobilenetV1/Conv2d_9_depthwise/weights_quant/FakeQuantWithMinMaxVars, 4608, 3, 0.014922, 132
82: MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Conv2D_Fold_bias, 2048, 2, 0.000161186, 0
83: MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Relu6, 100352, 3, 0.0235285, 0
84: MobilenetV1/MobilenetV1/Conv2d_9_pointwise/weights_quant/FakeQuantWithMinMaxVars, 262144, 3, 0.00685069, 120
85: MobilenetV1/Predictions/Reshape, 1001, 3, 0.165351, 74
86: MobilenetV1/Predictions/Reshape/shape, 8, 2, 0, 0
87: MobilenetV1/Predictions/Softmax, 1001, 3, 0.00390625, 0
88: Placeholder, 150528, 3, 0.00392157, 0
len: 499554
width, height, channels: 500, 333, 3
input: 88
number of inputs: 1
number of outputs: 1
Interpreter has 90 tensors and 31 nodes
Inputs: 88
Outputs: 87

Tensor   0 MobilenetV1/Logits/AvgPool_1a/AvgPool kTfLiteUInt8  kTfLiteArenaRw       1024 bytes ( 0.0 MB)  1 1 1 1024
Tensor   1 MobilenetV1/Logits/Conv2d_1c_1x1/BiasAdd kTfLiteUInt8  kTfLiteArenaRw       1001 bytes ( 0.0 MB)  1 1 1 1001
Tensor   2 MobilenetV1/Logits/Conv2d_1c_1x1/Conv2D_bias kTfLiteInt32   kTfLiteMmapRo       4004 bytes ( 0.0 MB)  1001
Tensor   3 MobilenetV1/Logits/Conv2d_1c_1x1/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo    1025024 bytes ( 1.0 MB)  1001 1 1 1024
Tensor   4 MobilenetV1/MobilenetV1/Conv2d_0/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        128 bytes ( 0.0 MB)  32
Tensor   5 MobilenetV1/MobilenetV1/Conv2d_0/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 112 112 32
Tensor   6 MobilenetV1/MobilenetV1/Conv2d_0/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo        864 bytes ( 0.0 MB)  32 3 3 3
Tensor   7 MobilenetV1/MobilenetV1/Conv2d_10_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor   8 MobilenetV1/MobilenetV1/Conv2d_10_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor   9 MobilenetV1/MobilenetV1/Conv2d_10_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  10 MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  11 MobilenetV1/MobilenetV1/Conv2d_10_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  12 MobilenetV1/MobilenetV1/Conv2d_10_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  13 MobilenetV1/MobilenetV1/Conv2d_11_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  14 MobilenetV1/MobilenetV1/Conv2d_11_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  15 MobilenetV1/MobilenetV1/Conv2d_11_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  16 MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  17 MobilenetV1/MobilenetV1/Conv2d_11_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  18 MobilenetV1/MobilenetV1/Conv2d_11_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  19 MobilenetV1/MobilenetV1/Conv2d_12_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      25088 bytes ( 0.0 MB)  1 7 7 512
Tensor  20 MobilenetV1/MobilenetV1/Conv2d_12_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  21 MobilenetV1/MobilenetV1/Conv2d_12_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  22 MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       4096 bytes ( 0.0 MB)  1024
Tensor  23 MobilenetV1/MobilenetV1/Conv2d_12_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 7 7 1024
Tensor  24 MobilenetV1/MobilenetV1/Conv2d_12_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     524288 bytes ( 0.5 MB)  1024 1 1 512
Tensor  25 MobilenetV1/MobilenetV1/Conv2d_13_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 7 7 1024
Tensor  26 MobilenetV1/MobilenetV1/Conv2d_13_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       4096 bytes ( 0.0 MB)  1024
Tensor  27 MobilenetV1/MobilenetV1/Conv2d_13_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       9216 bytes ( 0.0 MB)  1 3 3 1024
Tensor  28 MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       4096 bytes ( 0.0 MB)  1024
Tensor  29 MobilenetV1/MobilenetV1/Conv2d_13_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 7 7 1024
Tensor  30 MobilenetV1/MobilenetV1/Conv2d_13_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo    1048576 bytes ( 1.0 MB)  1024 1 1 1024
Tensor  31 MobilenetV1/MobilenetV1/Conv2d_1_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 112 112 32
Tensor  32 MobilenetV1/MobilenetV1/Conv2d_1_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        128 bytes ( 0.0 MB)  32
Tensor  33 MobilenetV1/MobilenetV1/Conv2d_1_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo        288 bytes ( 0.0 MB)  1 3 3 32
Tensor  34 MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        256 bytes ( 0.0 MB)  64
Tensor  35 MobilenetV1/MobilenetV1/Conv2d_1_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     802816 bytes ( 0.8 MB)  1 112 112 64
Tensor  36 MobilenetV1/MobilenetV1/Conv2d_1_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  64 1 1 32
Tensor  37 MobilenetV1/MobilenetV1/Conv2d_2_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 56 56 64
Tensor  38 MobilenetV1/MobilenetV1/Conv2d_2_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        256 bytes ( 0.0 MB)  64
Tensor  39 MobilenetV1/MobilenetV1/Conv2d_2_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo        576 bytes ( 0.0 MB)  1 3 3 64
Tensor  40 MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  41 MobilenetV1/MobilenetV1/Conv2d_2_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 56 56 128
Tensor  42 MobilenetV1/MobilenetV1/Conv2d_2_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       8192 bytes ( 0.0 MB)  128 1 1 64
Tensor  43 MobilenetV1/MobilenetV1/Conv2d_3_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 56 56 128
Tensor  44 MobilenetV1/MobilenetV1/Conv2d_3_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  45 MobilenetV1/MobilenetV1/Conv2d_3_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       1152 bytes ( 0.0 MB)  1 3 3 128
Tensor  46 MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  47 MobilenetV1/MobilenetV1/Conv2d_3_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     401408 bytes ( 0.4 MB)  1 56 56 128
Tensor  48 MobilenetV1/MobilenetV1/Conv2d_3_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo      16384 bytes ( 0.0 MB)  128 1 1 128
Tensor  49 MobilenetV1/MobilenetV1/Conv2d_4_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 28 28 128
Tensor  50 MobilenetV1/MobilenetV1/Conv2d_4_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo        512 bytes ( 0.0 MB)  128
Tensor  51 MobilenetV1/MobilenetV1/Conv2d_4_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       1152 bytes ( 0.0 MB)  1 3 3 128
Tensor  52 MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  53 MobilenetV1/MobilenetV1/Conv2d_4_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 28 28 256
Tensor  54 MobilenetV1/MobilenetV1/Conv2d_4_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo      32768 bytes ( 0.0 MB)  256 1 1 128
Tensor  55 MobilenetV1/MobilenetV1/Conv2d_5_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 28 28 256
Tensor  56 MobilenetV1/MobilenetV1/Conv2d_5_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  57 MobilenetV1/MobilenetV1/Conv2d_5_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       2304 bytes ( 0.0 MB)  1 3 3 256
Tensor  58 MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  59 MobilenetV1/MobilenetV1/Conv2d_5_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     200704 bytes ( 0.2 MB)  1 28 28 256
Tensor  60 MobilenetV1/MobilenetV1/Conv2d_5_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo      65536 bytes ( 0.1 MB)  256 1 1 256
Tensor  61 MobilenetV1/MobilenetV1/Conv2d_6_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw      50176 bytes ( 0.0 MB)  1 14 14 256
Tensor  62 MobilenetV1/MobilenetV1/Conv2d_6_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       1024 bytes ( 0.0 MB)  256
Tensor  63 MobilenetV1/MobilenetV1/Conv2d_6_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       2304 bytes ( 0.0 MB)  1 3 3 256
Tensor  64 MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  65 MobilenetV1/MobilenetV1/Conv2d_6_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  66 MobilenetV1/MobilenetV1/Conv2d_6_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     131072 bytes ( 0.1 MB)  512 1 1 256
Tensor  67 MobilenetV1/MobilenetV1/Conv2d_7_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  68 MobilenetV1/MobilenetV1/Conv2d_7_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  69 MobilenetV1/MobilenetV1/Conv2d_7_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  70 MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  71 MobilenetV1/MobilenetV1/Conv2d_7_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  72 MobilenetV1/MobilenetV1/Conv2d_7_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  73 MobilenetV1/MobilenetV1/Conv2d_8_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  74 MobilenetV1/MobilenetV1/Conv2d_8_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  75 MobilenetV1/MobilenetV1/Conv2d_8_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  76 MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  77 MobilenetV1/MobilenetV1/Conv2d_8_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  78 MobilenetV1/MobilenetV1/Conv2d_8_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  79 MobilenetV1/MobilenetV1/Conv2d_9_depthwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  80 MobilenetV1/MobilenetV1/Conv2d_9_depthwise/depthwise_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  81 MobilenetV1/MobilenetV1/Conv2d_9_depthwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo       4608 bytes ( 0.0 MB)  1 3 3 512
Tensor  82 MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Conv2D_Fold_bias kTfLiteInt32   kTfLiteMmapRo       2048 bytes ( 0.0 MB)  512
Tensor  83 MobilenetV1/MobilenetV1/Conv2d_9_pointwise/Relu6 kTfLiteUInt8  kTfLiteArenaRw     100352 bytes ( 0.1 MB)  1 14 14 512
Tensor  84 MobilenetV1/MobilenetV1/Conv2d_9_pointwise/weights_quant/FakeQuantWithMinMaxVars kTfLiteUInt8   kTfLiteMmapRo     262144 bytes ( 0.2 MB)  512 1 1 512
Tensor  85 MobilenetV1/Predictions/Reshape kTfLiteUInt8  kTfLiteArenaRw       1001 bytes ( 0.0 MB)  1 1001
Tensor  86 MobilenetV1/Predictions/Reshape/shape kTfLiteInt32   kTfLiteMmapRo          8 bytes ( 0.0 MB)  2
Tensor  87 MobilenetV1/Predictions/Softmax kTfLiteUInt8  kTfLiteArenaRw       1001 bytes ( 0.0 MB)  1 1001
Tensor  88 Placeholder          kTfLiteUInt8  kTfLiteArenaRw     150528 bytes ( 0.1 MB)  1 224 224 3
Tensor  89 (null)               kTfLiteUInt8  kTfLiteArenaRw     338688 bytes ( 0.3 MB)  1 112 112 27

Node   0 Operator Builtin Code   3 CONV_2D
  Inputs: 88 6 4
  Outputs: 5
  Temporaries: 89
Node   1 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 5 33 32
  Outputs: 31
Node   2 Operator Builtin Code   3 CONV_2D
  Inputs: 31 36 34
  Outputs: 35
Node   3 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 35 39 38
  Outputs: 37
Node   4 Operator Builtin Code   3 CONV_2D
  Inputs: 37 42 40
  Outputs: 41
Node   5 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 41 45 44
  Outputs: 43
Node   6 Operator Builtin Code   3 CONV_2D
  Inputs: 43 48 46
  Outputs: 47
Node   7 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 47 51 50
  Outputs: 49
Node   8 Operator Builtin Code   3 CONV_2D
  Inputs: 49 54 52
  Outputs: 53
Node   9 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 53 57 56
  Outputs: 55
Node  10 Operator Builtin Code   3 CONV_2D
  Inputs: 55 60 58
  Outputs: 59
Node  11 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 59 63 62
  Outputs: 61
Node  12 Operator Builtin Code   3 CONV_2D
  Inputs: 61 66 64
  Outputs: 65
Node  13 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 65 69 68
  Outputs: 67
Node  14 Operator Builtin Code   3 CONV_2D
  Inputs: 67 72 70
  Outputs: 71
Node  15 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 71 75 74
  Outputs: 73
Node  16 Operator Builtin Code   3 CONV_2D
  Inputs: 73 78 76
  Outputs: 77
Node  17 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 77 81 80
  Outputs: 79
Node  18 Operator Builtin Code   3 CONV_2D
  Inputs: 79 84 82
  Outputs: 83
Node  19 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 83 9 8
  Outputs: 7
Node  20 Operator Builtin Code   3 CONV_2D
  Inputs: 7 12 10
  Outputs: 11
Node  21 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 11 15 14
  Outputs: 13
Node  22 Operator Builtin Code   3 CONV_2D
  Inputs: 13 18 16
  Outputs: 17
Node  23 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 17 21 20
  Outputs: 19
Node  24 Operator Builtin Code   3 CONV_2D
  Inputs: 19 24 22
  Outputs: 23
Node  25 Operator Builtin Code   4 DEPTHWISE_CONV_2D
  Inputs: 23 27 26
  Outputs: 25
Node  26 Operator Builtin Code   3 CONV_2D
  Inputs: 25 30 28
  Outputs: 29
Node  27 Operator Builtin Code   1 AVERAGE_POOL_2D
  Inputs: 29
  Outputs: 0
Node  28 Operator Builtin Code   3 CONV_2D
  Inputs: 0 3 2
  Outputs: 1
Node  29 Operator Builtin Code  22 RESHAPE
  Inputs: 1 86
  Outputs: 85
Node  30 Operator Builtin Code  25 SOFTMAX
  Inputs: 85
  Outputs: 87
invoked 
average time: 271.33 ms 
0.921569: 674 mouse
0.0156863: 845 switch
0.0156863: 774 saltshaker
0.0117647: 723 ping-pong ball
0.00784314: 819 spotlight
[root@test label_image]# 

```

