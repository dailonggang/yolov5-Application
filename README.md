# 利用yolov5-5进行实际场景开发部署
主要检测目标：头盔、吸烟、火灾

基础环境：ubantu18.04+Anconda3

搭建环境：CUDA:11.1  CUDNN:8.0  Python:3.8  torch+torchvision:1.10.1+0.11.2

开发板：Jetson Xavier NX

场景：风电电力网络安全开发部署

说明：利用摄像头实时监测电力网络和人员行为，如有下面情况进行报警：工作人员未佩戴安全帽、吸烟和设备冒烟起火。

项目难点：摄像头取景距离远，室内视野5~10m，室外视野在5-20m，检测⽬标在视野中的占⽐较⼩；室外的背景复杂；夜间环境。

数据处理:旋转、裁剪、缩放、Mosaics和mixup等数据增强操作；



