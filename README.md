
# Person Detection and Tracking with YOLOv8 and DeepSORT

This project implements a robust person detection and tracking system using YOLOv8 for object detection and DeepSORT for multi-object tracking. The system processes video files, detects people, and tracks their movements across frames, assigning unique IDs to each tracked individual. This project is designed to run in a Google Colab environment.

https://youtu.be/_sq6Z84Ln7Y

## Table of Contents

1. [Features](#features)
2. [Requirements](#requirements)
3. [Setup](#setup)
4. [Usage](#usage)
5. [How It Works](#how-it-works)
6. [Output](#output)
7. [Customization](#customization)

## Features

- Person detection using YOLOv8
- Multi-object tracking with DeepSORT
- Batch processing of multiple video files
- Unique ID assignment for each tracked person
- Confidence threshold filtering for detections
- Output video generation with bounding boxes and ID labels

## Requirements

- Google Colab notebook
- GPU runtime (recommended for faster processing)

## Setup

1. Open the Colab notebook containing the project code.

2. Install the required packages by running the following cells:

   ```python
   !pip install torch torchvision torchaudio
   !pip install ultralytics
   !pip install deep_sort_realtime
   !pip install opencv-python
   ```
3. Import the necessary libraries:

   ```python
   from ultralytics import YOLO
   import cv2
   from deep_sort_realtime.deepsort_tracker import 
   DeepSort
   import os
   ```




## Usage

1. Upload your input video files to the Colab environment in the `/content/input_videos` directory.
2. Run the code cells in the notebook sequentially.
3. The processed videos will be saved in the `/content/output_videos` directory.
4. You can download the output videos from the Colab file browser.


## How It Works

1. **Video Processing**: The script iterates through all `.mp4` files in the input directory.
2. **Object Detection**: YOLOv8 is used to detect people in each frame of the video.
3. **Confidence Filtering**: Detections with confidence scores below 0.5 are filtered out.
4. **Object Tracking**: DeepSORT algorithm tracks the detected people across frames.
5. **ID Assignment**: Unique IDs are assigned to each tracked person, starting from 1 and incrementing for each new person detected.
6. **Visualization**: Green bounding boxes are drawn around detected people, along with their assigned ID.
7. **Output Generation**: Processed frames are compiled into an output video file, saved with "_output" appended to the original filename.


## Output

The script generates output videos with the following features:

- Green bounding boxes around detected people
- Labels showing the tracking ID for each person
- Output videos are saved in the `/content/output_videos` directory with "_output" appended to the original filename


## Customization

You can customize various parameters in the script:

- `max_age`, `n_init`, `nms_max_overlap`, `max_iou_distance` in the DeepSort initialization
- Confidence threshold for detections (currently set to 0.5)
- Bounding box color and thickness
- Font settings for ID labels
