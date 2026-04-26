# DeepLab
DeepLab was the first choice, as we wanted to do a Object Segmentation Program but ran into several issues. 
We were stuck in a loop due SciPy wanting a NumPy version newer than 1.25, but TensorFlow wanting one older than 1.25.
SciPy and TensorFlow were using different NumPy syntaxes, and eventually found out after trial and error.

Troubleshooting:
  - Installing NumPy 1.26.4
  - Installing Numpy 1.24.4
  - Migrating Older Syntaxes
  - Reinstallation of Model

After Troubleshooting and attempting to properly install the model to the Jetson we decided to contiue with object segmentation,
but instead use a different model.

# VGG16
We were familiar with VGG16-UNet due to using it in a previous project, and decided to pivot into object detection instead. 
Our issue was the GitHub repository tutorial we were following required us to train VGG16 ourselves in 5 epochs that nearly took 1.5 hours each

No troubleshooting done as once we realized the time requirement to train the model we decided to change models

# YOLO11
After a suggestion from a classmate to use YOLO11 due to it being simple to setup, we decided to continue with Object Detection using YOLO11
We began following the GitHub repository steps but ran into an issue similar to what we found using DeepLab
PyTorch version was mismatched and built for CUDA 13.0, whenever we used "pip install" it would only install packages for CUDA 13.0

Troubleshooting:
  - Installing PyTorch using L4T
  - Installing Jetpack 6.1
  - Reinstallation of Model
  - Using isolated docker enviroment

Using the docker actually allowed our model to work as it was an isolated enviroment that has its own libraries
But it wasnt repeatable and only worked occasionally, after this we decieded to keep using YOLO, but an older version compatible with CUDA 12.6
