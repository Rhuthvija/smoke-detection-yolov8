# internship_inML
This repository contains my work during my ML internship.

📂 Folder Overview
/images/ → Contains screenshots and reference visuals.
/notebooks/ → Will include Python notebooks or scripts used during my internship.
README.md → This document explains the structure and purpose of the repository.
🧠 Project Summary
During this internship, I explored the following:

# task 1: Object Detection and Segmentation using YOLOv8

This repository contains my work for the **Machine Learning Internship** project — focusing on **object detection and segmentation** using the **YOLOv8** model from Ultralytics.

---

## 🚀 Project Overview

The goal of this project is to perform **object detection and segmentation** on real-world images using the YOLOv8 model.

### Tasks Completed:

* Installed and configured the YOLOv8 environment
* Ran object detection on sample images (`classroom.jpg`, `office.jpg`)
* Visualized bounding boxes and segmentation masks
* Compared detection vs segmentation results

---

## 🧩 Tools & Libraries

| Tool                   | Purpose                         |
| ---------------------- | ------------------------------- |
| **Python 3.x**         | Programming language            |
| **Ultralytics YOLOv8** | Object detection & segmentation |
| **OpenCV**             | Image processing                |
| **Matplotlib**         | Visualization                   |
| **NumPy**              | Array operations                |

---

## 📁 Repository Structure

```
internship_inML/
│
├── code/
│   ├── detection_classroom.py
│   ├── segmentation_office.py
│
├── images/
│   ├── classroom.jpg
│   ├── office.jpg
│   └── results/
│       ├── classroom_detected.jpg
│       ├── office_segmented.jpg
│
├── requirements.txt
└── README.md
```

---

## 📷 Sample Results

| Image                  
| ---------------------- 
| classroom_detected.jpg 
| office_segmented.jpg   
---

## 🧠 Next Steps

* Experiment with different YOLOv8 models (e.g., `yolov8m`, `yolov8l`)
* Evaluate performance using metrics like Precision, Recall, and mAP
* Try real-time detection using webcam feed

---




## task 2:  Video Detection using YOLOv8

In this section, we take a short video clip and perform object detection frame-by-frame.

### 🧩 Step 1: Extract frames from the video

We use **FFmpeg** to split a video into sequential images:

```bash
ffmpeg -i input.mp4 frames/frame_%04d.jpg
```
### 🎥 Video Detection Results
- [Input video (Google Drive link)]([https://drive.google.com/...](https://drive.google.com/file/d/1hm5oYblcNJ7Kw0asFL1eLytWiEI98Os3/view?usp=drive_link))
- [Processed output video (Google Drive link)](https://drive.google.com/file/d/1GHijquTaxzF1daGmt_42MJWdRRpEcneJ/view?usp=drive_link)

* `input.mp4` → your video file
* `frames/frame_%04d.jpg` → output folder and image pattern

### 🧠 Step 2: Run YOLOv8 object detection on all frames

```bash
yolo detect predict model=yolov8n.pt source="frames/" save=True
```

This generates processed images (with bounding boxes) inside the `runs/detect/predict/` folder.

### 🎞️ Step 3: Combine processed frames back into a video

We use FFmpeg again to stitch them together:

```bash
ffmpeg -framerate 24 -i runs/detect/predict/frame_%04d.jpg -c:v libx264 -pix_fmt yuv420p output.mp4
```

* `output.mp4` will be your final detected video
* You can play it using any media player

### 🧾 Output

* **Input video:** `input.mp4`
* **Processed video:** `output.mp4`

This demonstrates how YOLOv8 can handle not just static images, but dynamic video streams by processing frames in sequence.



## vision task: Outdoor Smoke Detection using YOLOv8

### Problem Statement
Outdoor smoke originating from factories, vehicles, and wildfires contributes significantly to air pollution and poses serious risks to human health and the environment.
The goal of this project is to design a computer vision system that can automatically detect outdoor smoke in videos, with minimal human intervention and high reliability.

###Project Objective
Detect smoke in real-world outdoor videos
Train a custom object detection model using transfer learning
Validate the model on unseen videos
Produce a single consolidated demo video as proof of performance

### Approach
1. Collected real-world outdoor smoke videos (factory emissions, vehicular smoke, wildfire smoke).
2. Extracted diverse frames from videos using FFmpeg.
3. Annotated smoke regions manually using Label Studio.
4. Created a custom YOLO-format dataset (train/validation split).
5. Performed transfer learning using a pre-trained YOLOv8 model.
6. Ran object detection on multiple unseen videos.
7. Merged all processed outputs into a single demonstration video.

### Frame Extraction
Used FFmpeg to extract frames from videos.
Special care was taken to avoid near-duplicate frames (high FPS causes overfitting).
Selected diverse frames manually to improve generalization.

### Annotation (Major Challenge)

Installed and used Label Studio for manual annotation.
Labeled smoke regions using bounding boxes.
One major challenge faced was:
Configuring Label Studio to correctly load local image paths
Avoiding over-annotation of visually similar frames
Final dataset consisted of ~90+ carefully annotated images.

### Dataset Preparation

Converted annotations into YOLO format.
Organized dataset into:
images/train, images/val
labels/train, labels/val
Created a custom data.yaml file for training.

### Repository Structure (Explanation)
├── data.yaml
├── yolov8n.pt
├── final_output_smoke_detection.mp4
├── runs/
│   └── detect/
│       └── train6/
│           └── weights/
│               ├── best.pt
│               └── last.pt
└── README.md

### File Explanations
data.yaml
Defines dataset paths, number of classes, and class names for YOLO training.
yolov8n.pt
Pre-trained YOLOv8 model used as the base for transfer learning.
runs/detect/train6/weights/best.pt
Final trained smoke detection model.
final_output_smoke_detection.mp4
Merged output video demonstrating smoke detection across multiple real-world scenarios.

⚠️ Note on Missing Files (Important)
Due to GitHub file size limitations, the following folders are not uploaded:
images/
labels/
Raw extracted frames

These folders together exceed GitHub’s size limits.
However, the complete dataset was used locally for:
Annotation
Training
Validation
and is fully reflected in the final trained model and output video.

### Tools & Technologies
- Python
- YOLOv8 (Ultralytics)
- Label Studio
- FFmpeg
- OpenCV
- GitHub

### Results
The trained model is able to detect outdoor smoke across different scenarios including industrial areas, vehicles, and wildfires.  
The final output video demonstrates consistent smoke detection across multiple real-world clips.
This project demonstrates the practical challenges of real-world computer vision beyond curated datasets.

### Key Learnings

Dataset quality is more important than dataset size.
Annotation is the most time-consuming and critical step.
Debugging dataset paths and training configurations is a core ML skill.
End-to-end pipelines are significantly harder than running pre-trained demos.

### Output
- Final merged video: `final_output_smoke_detection.mp4`

*Created and maintained by [Rhuthvija](https://github.com/Rhuthvija)* ✨


