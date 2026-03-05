README = """
# Traffic Sign Detection using YOLOv8

This project implements an object detection system for detecting traffic signs in images and real-world driving videos using the YOLOv8 deep learning framework.

The model was trained on the German Traffic Sign Detection Benchmark (GTSDB) dataset and evaluated on validation data and real driving footage. The goal of the project is to build and evaluate a deep learning pipeline capable of detecting traffic signs under realistic driving conditions.

This project was developed as part of the Computer Vision course in the B.Sc. Applied Artificial Intelligence program at IU International University of Applied Sciences.

---

## Project Overview

The project includes the following steps:

1. Dataset exploration and preparation  
2. Conversion of annotations into YOLO format  
3. Training YOLOv8 models  
4. Evaluation using object detection metrics  
5. Applying the model to real-world driving videos  

The final model demonstrates reliable detection of traffic signs under different conditions such as varying lighting, distances and camera motion.

---

## Dataset

The project uses the German Traffic Sign Detection Benchmark (GTSDB) dataset.

Dataset source:  
https://benchmark.ini.rub.de/gtsdb_dataset.html

The dataset contains:

- traffic scene images  
- bounding box annotations  
- multiple traffic sign categories  

Before training, the dataset was converted into YOLO annotation format using normalized bounding box coordinates.

Due to size limitations the dataset is not included in this repository.

---

## Repository Structure

Projekt/

README.md  
.gitignore  

cv_traffic_signs/  
    notebooks/                 Jupyter notebooks for training and evaluation  
    data/  
        yolo/gtsdb/  
            data.yaml          Dataset configuration  

FullIJCNN2013/                 Original dataset (not included in repo)  
runs/                          Training outputs (not included)

Large files such as datasets, training outputs, videos and virtual environments are excluded via the .gitignore file.

---

## Model

The project uses YOLOv8, an object detection architecture developed by Ultralytics.

Framework repository:  
https://github.com/ultralytics/ultralytics

Different model configurations were tested:

- YOLOv8n (baseline model)  
- YOLOv8s (improved accuracy)

Training used higher input resolution, data augmentation and extended training epochs to improve performance.

---

## Training

Training was performed using the Ultralytics YOLO framework.

Example training configuration:

model.train(
    data="data.yaml",
    epochs=120,
    imgsz=960,
    batch=16,
    augment=True
)

During training the following metrics were monitored:

- Precision  
- Recall  
- Mean Average Precision (mAP)

---

## Evaluation

The trained model was evaluated on a validation dataset.

Example evaluation call:

model.val(
    data="data.yaml",
    imgsz=960,
    conf=0.25,
    iou=0.6
)

Evaluation metrics include:

- Precision  
- Recall  
- mAP50  
- mAP50-95  

---

## Video Inference

To demonstrate real-world applicability, the trained model was applied to several dashcam videos.

Example inference:

model.predict(
    source="video.mp4",
    imgsz=960,
    conf=0.25,
    save=True
)

The resulting videos show detected traffic signs with bounding boxes and predicted classes.

---

## Requirements

Main dependencies:

- Python
- PyTorch
- Ultralytics YOLO
- Jupyter Notebook

Installation example:

pip install ultralytics torch torchvision

---

## Notes

The following files are not included in the repository:

- datasets  
- trained model weights  
- training outputs (runs/)  
- videos used for inference  
- virtual environments  

This keeps the repository lightweight while still allowing the project to be reproduced using the provided notebooks and configuration files.

---

## Author

Manujel Prlic

B.Sc. Applied Artificial Intelligence  
IU International University of Applied Sciences
"""