Mask R-CNN
https://github.com/matterport/Mask_RCNN
The model generates bounding boxes and segmentation ==masks== for each instance of an object in the image. It's based on Feature Pyramid Network (FPN) and a ResNet101 backbone.

AlphaPose
https://github.com/MVIG-SJTU/AlphaPose

YOLO8 pose estimation model is not fastest since it is designed for object detection in the first place. 
  
The fastest pose estimation models are typically lightweight models that are designed for specific applications, such as mobile applications or real-time video processing. Some examples of fast pose estimation models include:


- **PoseNet**  https://github.com/tensorflow/tfjs-models uses typescript
- **Deep Pose** 
- **MoveNet** 
- **AlphaPose (Regional Multi-Person Pose Estimation)**


# 2023 overview
https://viso.ai/deep-learning/pose-estimation-ultimate-overview/

One of the most popular solutions:
- Openpose 
	- https://github.com/CMU-Perceptual-Computing-Lab/openpose 
	- most popular, uses cuda
- High-Resolution Net (HRNet)  
	- https://github.com/leoxiaobin/deep-high-resolution-net.pytorch
	- uses cuda
- Deep pose
	- couldn't find implementation
- PoseNet 
	- https://github.com/tensorflow/tfjs-models
	- uses typescript
- DensePose
	- https://github.com/facebookresearch/Densepose
	- uses python2
- Pose-tensorflow
	- https://github.com/eldar/pose-tensorflow
	- relatively old
	- have not been edited since 2019
- OpenPifPaf
	- https://github.com/openpifpaf/openpifpaf
	- uses pytorch



Most of them use 
R-CNN - **Region-based Convolutional Neural Network**.
COCO - dataset


mediapipe

