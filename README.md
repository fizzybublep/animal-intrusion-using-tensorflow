# (1) Project Overview :

This project implements a real-time animal intrusion detection system using TensorFlow Object Detection API and a pretrained MS COCO model, integrated with an Arduino-based alarm system.
The system detects animals (specifically bears, elephants, and tigers) using a webcam feed. When an animal is detected, a signal is sent from the Python environment to an Arduino microcontroller via PySerial, triggering an alarm actuator.
This project demonstrates:
- Transfer learning using pretrained deep learning models
- End-to-end object detection pipeline
- Hardware–software integration using serial communication
- Practical application of computer vision for safety systems

# (2) Model & Learning Approach

Pretrained model used:
ssd_mobilenet_v2_fpnlite_320x320_coco17_tpu-8 (trained on MS COCO)

Why pretrained (transfer learning)?
- Requires significantly less training data
- Faster convergence
- Lower computational cost
- Better generalization

The model was fine-tuned on a custom dataset containing images of:
- Bears
- Elephants
- Tigers

# (3) Main Files :

| File / Folder                  | Description                                                     |
| ------------------------------ | --------------------------------------------------------------- |
| `training_and_detection.ipynb` | Main notebook for training, evaluation, and real-time detection |
| `image_collection.ipynb`       | Script used for collecting and organizing image data            |
| `annotations/`                 | XML annotation files (Pascal VOC format)                        |
| `label_map.pbtxt`              | Label mapping for object detection classes                      |
| `models/`                      | Model configuration files                                       |
| `checkpoints/`                 | Saved model checkpoints                                         |
| `.gitignore`                   | Excludes datasets, virtual environments, and large files        |
| `README.md`                    | Project documentation                                           |

# (4) Files Not Included (Intentionally) :

To keep the repository lightweight and reproducible, the following are not uploaded:
- Training images and test datasets
- Virtual environment (tfod/)
- Pretrained model binaries
- Large TensorFlow cache files

# (5) Dataset & Annotation :
- Training images were sourced from public online datasets
- Images were manually labeled using LabelImg
- Annotations are stored in XML format (Pascal VOC)
- Labels were converted for compatibility with TensorFlow Object Detection API

# (6) Real-Time Detection Pipeline :
Webcam captures live video feed
- TensorFlow model performs object detection per frame
- If an animal is detected:
-- Detection confidence threshold is checked
-- A serial signal is sent to Arduino using PySerial
- Arduino receives the signal and activates an alarm actuator

# (7) Hardware Integration :
## Components used:
- Arduino microcontroller
- Buzzer / alarm actuator
- USB serial connection
## Communication:
- Python ↔ Arduino via pyserial
- Arduino listens for serial commands and triggers alarm

# (8) Requirements :
## Software
- Python 3.8+
- TensorFlow
- OpenCV
- NumPy
- PySerial
- Jupyter Notebook
- TensorFlow Object Detection API
## Hardware
- Webcam
- Arduino board
- Alarm / buzzer
- USB cable
