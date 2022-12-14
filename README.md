# 利用yolov5-5进行实际场景开发部署
### 主要检测目标：头盔、吸烟、火灾

场景：风电电力网络安全监测

说明：利用摄像头实时监测电力网络和人员行为，如有下面情况进行报警：工作人员进入工作区域未佩戴安全帽、吸烟和设备冒烟起火。

项目难点：摄像头取景距离远，室内视野5~10m，室外视野在5-20m，检测类别多、尺度不一，在视野中目标较小；室外的背景复杂；夜间环境。

如图所示：![image](https://github.com/dailonggang/yolov5-Application/blob/main/%E9%83%A8%E7%BD%B2%E5%9B%BE%E7%89%87/3.jpg)

# yolov5算法开发

基础环境：ubantu18.04+Anconda3

搭建环境：CUDA:11.1  CUDNN:8.0  Python:3.8  torch+torchvision:1.10.1+0.11.2

数据处理：旋转、裁剪、缩放、Mosaics和mixup等数据增强操作。
![image](https://github.com/dailonggang/yolov5-Application/blob/main/%E9%83%A8%E7%BD%B2%E5%9B%BE%E7%89%87/1.jpg)

训练自定义数据集参见[知乎](https://zhuanlan.zhihu.com/p/523184652)。

# 测试效果
![image](https://github.com/dailonggang/yolov5-Application/blob/main/%E9%83%A8%E7%BD%B2%E5%9B%BE%E7%89%87/2.jpg)
视频测试效果请见：[仓库上传视频](https://github.com/dailonggang/yolov5-Application/tree/main/%E9%83%A8%E7%BD%B2%E6%B5%8B%E8%AF%95)

# 部署
为了兼顾速度以及达到客户的实际要求，选取 Jetson Xavier NX 开发板进行部署开发。

NX 环境搭建：python 3.6.9  pytorch 1.7.0  cuda 10.2  cudnn 8.0  tensorrt 7.1.3.0  torchvison 0.8.1。

# 部署流程
1.选择合适版本的tensorRTX

对照YOLOv5给出版本，[参考网址](https://github.com/wang-xinyu/tensorrtx/tree/master/yolov5)

2.修改配置文件

主要修改CLASS_NUM、INPUT_H、INPUT_W和量化类型

3.编译运行

首先利用tensorrtx下的 gen_wts.py 文件将生成的.pt权值文件转为.wts的中间格式，然后利用 .wts 中间格式转为.engine文件

4.将生成的engine文件放入c++文件中重新编译运行

# 优化
优化效果请见：[仓库上传视频](https://github.com/dailonggang/yolov5-Application/tree/main/%E9%83%A8%E7%BD%B2%E6%B5%8B%E8%AF%95)
