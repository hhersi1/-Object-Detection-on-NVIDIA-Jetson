# Object-Detection-on-NVIDIA-Jetson
This repository contains the workflow for the Object Detection inferencing on GPU edge device project for MENG 3540: Parallel Programming
# Pretrained Model Chosen: YOLOv4
YOLOv4 was developed by Alexey Bochkovskiy in 2020, is a real-time object detection model.
It builds upon previous YOLO versions by adding improvements such as Darknet as its backbone.

YOLOv4 is implemented using the Darknet framework, a C and CUDA-based deep learning library which is specially made for running convolutional neural networks. 

# Requirements:
  - Windows 10/11 Computer
  - NVIDIA ORIN Jetson
  - Camera or Webcam
  - Python Compiler
  - Tensorflow 1
  - OpenCV 3


# How to install and run model
1) Create and Open Directory

```
mkdir YOLOv4
cd YOLOv4
```

2) Enable Highest Performance
   - GUI
     - Power Icon in top right
     - Performance Options
   - Terminal

```
sudo nvpmodel -m 0
sudo jetson_clocks
```

3) Clone GitHub Repository
   ```
   git clone https://github.com/AlexeyAB/darknet.git
   ```
4) Download Pre-Trained weights
   ```
   wget https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v4_pre/yolov4-tiny.weights
   ```

5) Build GPU Version
```
sed -i 's/GPU=0/GPU=1/' Makefile
sed -i 's/CUDNN=0/CUDNN=1/' Makefile
sed -i 's/OPENCV=0/OPENCV=1/' Makefile
sed -i 's/LIBSO=0/LIBSO=1/' Makefile
sed -i 's/ARCH= -gencode arch=compute_30,code=sm_30/ARCH= -gencode arch=compute_87,code=sm_87/' Makefile
make -j$(nproc)
mv darknet darknet_gpu
```

   
