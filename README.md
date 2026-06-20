# Real-Time-Head-and-Body-Detection-on-FPS-Gameplay-A-Comparative-Study-of-YOLOv8-and-RT-DETR
predict:https://drive.google.com/drive/folders/1Rd4cZ7YwwDJarwuCq1J9ZVxgiJ-so0jv
# Real-Time Head and Body Detection on FPS Gameplay: A Comparative Study of YOLOv8 and RT-DETR

This project focuses on real-time object detection of "Head" (Class 0) and "Body" (Class 1) from FPS gameplay screenshots. It aims to evaluate and compare the detection accuracy and inference speed between **YOLOv8** and **RT-DETR** models in high-speed, dynamic environments.

---

##  Dataset Information

This dataset is specifically annotated for FPS gameplay scenarios and consists of two classes: `head` (Class ID: 0) and `body` (Class ID: 1).

### 1. Directory Structure
Please ensure your local dataset directory structure perfectly matches the configuration in `data.yaml`. The expected structure is as follows:

```text
dataset/
├── images/
│   ├── train/  # Training images (.jpg, .png)
│   └── val/    # Validation images
└── labels/
    ├── train/  # Training labels in YOLO format (.txt)
    └── val/    # Validation labels in YOLO format (.txt)
2. Label Format
Each image corresponds to a .txt file with the exact same name. Each line in the file represents a bounding box using the following format:
<class_id> <x_center> <y_center> <width> <height>

 Installation Instructions
Please make sure Python 3.8 or a newer version is installed on your system. Follow the steps below to set up the environment:

Clone the Repository:

Bash
git clone [https://github.com/UserSylvia/Real-Time-Head-and-Body-Detection-on-FPS-Gameplay-A-Comparative-Study-of-YOLOv8-and-RT-DETR.git](https://github.com/UserSylvia/Real-Time-Head-and-Body-Detection-on-FPS-Gameplay-A-Comparative-Study-of-YOLOv8-and-RT-DETR.git)
cd Real-Time-Head-and-Body-Detection-on-FPS-Gameplay-A-Comparative-Study-of-YOLOv8-and-RT-DETR
Install Required Packages:

Bash
pip install ultralytics
 Source Code & Usage
This repository includes scripts for data preprocessing, model training, and inference for both YOLOv8 and RT-DETR.

1. Configure data.yaml
Before starting the training process, open data.yaml and update the path variable to point to your local dataset directory:

YAML
#  Please change the path below to your actual local dataset absolute path
path: YOUR_LOCAL_DATASET_PATH/dataset 

train: images/train
val: images/val

names:
  0: head
  1: body
2. Model Training (Training Source Code)
YOLOv8 Training: Execute train_yolo.txt (It is recommended to change the extension to .py before running).

RT-DETR Training: Execute train_dter.txt (It is recommended to change the extension to .py before running).

Example snippet for training:

Python
from ultralytics import YOLO

# Load pre-trained weights and start training
model = YOLO('yolov8n.pt') 
model.train(data='data.yaml', epochs=100, imgsz=640)
3. Inference & Quick Test
A sample.jpg file is provided in this repository for a quick environment and code sanity check.

Test with YOLOv8: Run video_detection_yolo.txt

Test with RT-DETR: Run video_detection_dter.txt

You can modify the source argument to sample.jpg in the script to verify if the model successfully detects objects and draws bounding boxes:
from ultralytics import YOLO

# Load pre-trained weights for a quick environment test
model = YOLO('yolov8n.pt')

# Test on the single sample image
results = model.predict(source='sample.jpg', save=True, conf=0.25)
